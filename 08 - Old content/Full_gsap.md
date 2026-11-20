## Learn gsap 
1. in this note we gonna cover the basics of `gsap` which is a well known library that helps dev to perform complex animation very esaly 
2. in the begining we gonna follow the old fashion way using html, css, and, js
3. after we gonna move to react

### Instalation 
1. after creating you main files `index.html` , `style.css` , `script.js` now it's time to import the gsap library to you project using GSAP `CDN` which is the folowing : 

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js" integrity="sha512-7eHRwcbYkK4d9g/6tD/mhkf++eoTHwpNM9woBxtPUBWm67zeAfFC+HrdoE2GanKeocly/VxeLvIqwvCdk7qScg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

2. perform simple animation 
- we need to give the element that we wanna animate a unique id 
```html 
<html> 
<body>
	<div id="box"></div>
</body>
</html>
```
- we can apply some styles 
```css
div#box {
	width: 300px;
	height: 300px;
	background-color: crimson;
}
```
- now let's move on into the script file were we can make our magic 
```javascript
gsap.to()    // initial position to final position
// or 
gsap.from()  // final position to initial position
// or
gsap.fromTo('', {from}, {to})
// both takes two args 
// first_arg : id_element that we want to animate or element name
"#main__h2" or "h2"
// second_arg : animations in key: value format
{
	x: .. , 
	y: .. ,
	...
}
-----------------------------------------------------
gsap.to('#box', {
	x: 1000, // in px
	duration: 2, // in s 
	delay: 1, // in s 
	rotate: 90, // deg
	backgroundColor: "#F323A2", 
	color: "#FFFFF", // text color
	borderRadius: "[.. px] or [.. %]", 
	scale: 1, // resise the element based on his initial form
})
```

- Cool fade in effect for text 
```javascript
gsap.from("h2", {
	y: 20, 
	opacity: 0, 
	duration: 2, 
	delay: 1, 
	stagger: 1, // this attribute will create a delay of 1s between each element
})
```

#### What is stagger ? 
1. `stagger`  is the one responsible to create a delay when it commes to animate many elements : this attribute is deffirent from delay and it accepts time in seconds to
2. if the value of the stagger was positif : `1, .5` it will start from the first element to the last, other wise if the value provided was negative `-1` in that case it will start from thet last element to the first

#### Repeat attribute ?
1. the `repeat` attributes controles the amount of repeating of our animation pay attention that always one animations is added to the number of repeate we provide : for exemple if we provide the value 1 the animation will happend _2 times_, first is when page is loaded and the second is the amount of repeat
2. if we provide a negative value : `-1`  that means ---> `infinite`  animation

```javascript
gsap.to('#box1". {
	repeat:  1,  // repeate one time after initial animation
	repeat: -1   // repeate infinitly the animation
})
```

#### Yoyo attribute ?
1. the `yoyo`  attribute creates a yoyo effect which means the element goes from the initial position to the final and the inverse in a smouth way like a yoyo
2. this attribute accepts boolean values only : `true || false`

```javascript
gsap.to('#box2', {
	yoyo: true
})
```


## Gsap timeline and how to control it ? 

1. in general all the animations in gsap hapends in a async way that's why we use the timeline to sync these animations which means one animations starts after another

```javascript
let tl = gsap.timeline()
// animation for the first element 
tl.to("#box1", {
	x: 400, 
	duration: 2,
	delay: 1
})
// animation for the second box 
tl.to("#box2", {
	x: 400, 
	duration: 2, 
	delay: 1
})
```


#### simple navbar animation
1. html code 
```html 
	<div id="nav">
        <h2>houssam</h2>
        <div id="part2">
            <h2>work</h2>
            <h2>courses</h2>
            <h2>about</h2>
            <h2>blog</h2>
        </div>
    </div>
```

2. animation code js 
```javascript
var tl = gsap.timeline()
tl.from("h2", {
    y: -30,
    opacity: 0,
    duration: .5,
    delay: .5,
})
tl.from("h4", {
    y: -30,
    opacity: 0,
    duration: 1,
    delay: .5,
    stagger: .3
})
```


# Scrolltrigger in gsap

1. first we need to add gsap `scrolltrigger` cdn to our html file :

```html 
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js" integrity="sha512-onMTRKJBKz8M1TnqqDuGBlowlH0ohFzMXYRNebz+yOcc5TQr/zAKsthzhuv0hiyUKEiQEQXEynnXCvNTOk50dg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

2. after that we need to add it to the element

```javascript
gsap.from("#page2 #box", {
	...
	scrollTrigger: "#page2 #box"
})
```

3. we can also specify special propreties to our scrollTrigger

```javascript
gsap.from("#page2 #box", {
	...
	scrollTrigger: {
		trigger: "#pag2 #box",
		scroll: "body", 
		markers: true, 
		start: "top 60%"
	}
})
```

we use `markers` to visualize the position from were the animation should start, its not an important property and it's commonly used for education purposes.

##### Scrub property

1. this prop is used in the scrollTrigger to indelicate that the animation will be done while scrolling in the page both up and down, this prop takes both `bool` and `nums [1...5]` to control the smothness

```javascript
gsap.from("#page2 #box", {
	...,
	scrollTrigger: {
		trigger: '', 
		scroller: "body", 
		start: "top 50%", 
		end: "top 40%", 
		scrub: true, 
		pin: true
	}
})
```

##### Pin property 

`
```javascript
	gsap.from('', {
		crub: true, 
		pin: true
	})
```


# Svg  Animation

1. svg or `scalable vector graphics`

```html
<body class="bg-black">

<div id="string" class="">

<svg width="1000" height="160">

<path d="M 10 100 Q 250 100 990 100" stroke="white" fill="transparent"/>

</svg>

</div>

</body>
```

```javascript
var path = 'M 10 100 Q 250 100 490 100'

// move x y curve .. center .. ..

let finalPath = 'M 10 100 Q 250 100 490 100'

  

var string = document.querySelector('#string')

string.addEventListener('mousemove', function(position){

path = `M 10 100 Q ${position.x} ${position.y} 490 100`;

console.log(path)

gsap.to("svg path", {

attr: {d : path},

duration: .2,

ease: "power3.out"

})

})

string.addEventListener('mouseleave', _ => {

gsap.to("svg path", {

attr: {

d: finalPath

},

duration: .3,

ease: "bounce"

})

})
```