- by default we use `commonjs` format in javascript to use the `module` syntax you only need to add this line to your package.json file `type: "module"`

1. How to install a dev dependency in your project ? 

```shell 
meth 1 --> npm i --save-dev package
meth 2 --> npm i -D package
```

2. in this project the main packages that we gonna need are 
	1. express
	2. mongoose
	3. bcryptjs
	4. dotenv
	5. cookie-parser
	6. cors
	7. mailtrap
	8. crypto
	9. validator --> to be able to validate certain fields like : email ...

### Specify the status of project 

- in your env file add `NODE_ENV` status `developement | production`

```env
NODE_ENV="developement"
```


3. another way to connect to the database 

```javascript
const mongoose = require("mongoose");

const connectdb = async (URI) => {
    try {
        const conn = await mongoose.connect(URI);
        console.log(`-> Connected to db ${conn.connection.host}`.cyan);
    } catch (err) {
        console.log("Error : ", err.message);
    }
};

module.exports = connectdb;
```

4. Email validation in our user model schema we use `validator` package

```javascript 
const validator = require("validator");

// model schema 
const schema = new mongoose.Schema({
	...
	email: {
		type: String, 
		required: true, 
		unique: true, 
		validate: [validator.isEmail, "Unvalid email"]
	}
}, {timestamps: true})
```

in our exemple 

```javascript 
const mongoose = require("mongoose");
const validator = require("validator");

const userSchema = new mongoose.Schema(
    {
        fullname: {
            type: String,
            required: true,
        },
        email: {
            type: String,
            required: true,
            unique: true,
            validate: [validator.isEmail, "Unvalid email format"],
        },
        password: {
            type: String,
            required: true,
        },
        lastLogin: {
            type: Date,
            default: Date.now,
        },
        isVerified: {
            type: Boolean,
            default: false,
        },
        resetPasswordToken: String,
        resetPasswordExpiresAt: Date,
        verificationToken: String,
        verificationTokenExpiresAt: Date,
    },
    { timestamps: true }
);

module.exports = mongoose.model("User", userSchema);

```

###### How to generate a jwt_secret_key using `crypto` module

```javascript
const crypto = require("crypto")

const key = crypto.randomBytes(32).toString('hex')
```

##### create a token and set it as a cookie 

```javascript 
const jwt = require("jsonwebtoken");

const generateTokenAndSetCookie = (payload) => {
    const token = jwt.sign(payload, process.env.JWT_SECRET_KEY, {
        expiresIn: "7d",
    });
    // set the token as a cookie
    res.cookie("token", token, {
        httpOnly: true, // prevent any xss attacks
        secure: process.env.NODE_ENV === "production",
        sameSite: "strict", // prevent csrf attack
        maxAge: 7 * 60 * 60 * 1000
    });
};

module.exports = generateTokenAndSetCookie;

```


###### Signup controller best practice 

```javascript
const signup = async (req, res) => {
    try {
        const { fullname, email, password } = req.body;
        if (!fullname || !email || !password) {
            throw new Error("All fields are required");
        }
        // check if user exists before or not
        const userAlreadyExists = await User.find(email);
        if (userAlreadyExists) {
            return res.status(404).json({
                status: httpStatus.FAIL,
                success: false,
                message: "User already exists",
                data: {
                    token: null,
                },
            });
        }
        // password hashing
        const hashedPass = await bcrypt.hash(password, 8);
        // generate a verification code
        const verificationToken = generateVerificationToken();
        // instansiate a new user
        const user = new User({
            fullname,
            email,
            password: hashedPass,
            verificationToken,
            verificationTokenExpiresAt: Date.now() + 24 * 60 * 60 * 1000,
        });
        // save the user
        await user.save();
        // generate a token
        const token = generateToken(res, user._id);
        // return a response 
        res.status(201).json({
            success: true, 
            message: "user created successfuly",
            data: {
                user: {
                    ...user._doc, 
                    password: undefined
                }
            }
        })
    } catch (err) {
        res.status(400).json({
            status: httpStatus.ERROR,
            success: false,
            message: err.message,
            data: {
                token: null,
            },
        });
    }
};
```

#### configure our mailtrap file so that we can send verif mails 

1. first we need to create a new file with the name `mailtrap.config.js` inside of it we paste this code which can be found in the official docs of mailtrap 

```javascript 
const { MailtrapClient } = require("mailtrap");

const TOKEN = process.env.TOKEN;
const ENDPOINT = process.env.ENDPOINT;

const client = new MailtrapClient({ endpoint: ENDPOINT, token: TOKEN });

const sender = {
    email: "mailtrap@demomailtrap.com",
    name: "Mailtrap Test",
};
const recipients = [
    {
        email: "gymhoussam2018@gmail.com",
    },
];

client
    .send({
        from: sender,
        to: recipients,
        subject: "You are awesome!",
        text: "Congrats for sending test email with Mailtrap!",
        category: "Integration Test",
    })
    .then(console.log, console.error);

```

##### Generate a verificationToken code

```javascript 
const verficationToken = () => {
	return Math.floor(100_000 + Math.random() * 900_000).toString()
}
module.exports = verificationToken;
```

##### create email function

```javascript 
const { client, sender } = require('../path')
const { VERIFICATION_EMAIL_TEMP } = require('../path')

const sendVerificationEmail = (email, verificationToken) => {
    const recipient = [{ email }];
		
    try {
		const response = await client.send({
			
		})
		console.log("Success : Email was send successfuly")
    } catch (err) {
        
    }
};

```


#### create function to send welcome email 

- this function should be created in the same `email.js` file which contains the the send verification-Token function that we defined before

```javascript 
const sendWelcomeEmail = async (email, name) => {
    const recipient = [{ email }];

    try {
        const response = await client.send({
            from: sender,
            to: recipient,
            template_uuid: "7cb02431-a8de-4309-85df-4891e0294252",
            template_variables: {
                company_info_name: "AUTH SAM",
                name: name,
            },
        });
        console.log("Error : Welcome email was sent successfuyly", response);
    } catch (err) {
        console.log("Error : error sending email", err.message);
        throw new Error("Error : While sending welcome email", err.message);
    }
};
```