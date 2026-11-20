# Linux history

| `Year` | `Contributes`                        | `Event`                                                         |
| ------ | ------------------------------------ | --------------------------------------------------------------- |
| `1964` | - General electric - Bell labs - Mit | `Multics`                                                       |
| `1970` | - Bell Labs [AT&T]                   | `unics`   -> ( B lang )                                         |
| `1973` | - Bell Labs                          | `unix `    -> (C lang)                                          |
| `1976` | - Berkley univercity                 | `BSD` [Bercley software distribution] by some skillful students |
- After berkley univ students have made there own distro in top of unix. Bell Labs company have made some policy changes : 
		- `NDA`  : [non distribution agreement] which forces everyone who wants to use this os to not edit or make a distro out of it 

#### This is a list of companies that bought the unix os after and made there own os in top of it : 

1. `IBM`     ---> AIX
2. `HP`       ---> HPUX
3. `Apple` ---> Macos 
4. `sun`     ---> sun solaris

##### After unix has become closed 

`Richard stollman`  --> `GNU`  os called [Gnu's not unix] --> open source
with a `GPL` feature which is `general public lisence`

The architecture of gnu os
![](C:\Users\houss\Downloads\schemapng)
##### Linustrovalds 
has created the new `kernel` which called `linux` and after it was integrated in the `gnu` project to give us the [GNU - Linux]

##### Most famous Linux destro
- `93`  :  Slackware 
- `93`  :  Debian
				- Ubuntu
- `94`  :  Redhat  : 
				- fedora 
				- centos 
				- RHEl [Redhat enterprise linux]
				- rocky linux

##### Shell prompt
1. `houssam` [username]
2. `@debiansrv1` [@hostname]
3. `~`  [Current directory]
4. `$ or #`  $ regular user --- # admin user or root
this is `~` called _tilda slash_
before we had : `sh` which stands for : Borne-Shell
<font color="#75aa84">Default shell is</font> `bash` which stands for : **Borne-Again-Shell**
<font color="#75aa84">We have also</font>  `zsh` which stands for : 
#### What is TTy or Teletype terminal ?
Linux alows many `tty`  or __teletype terminal__ for each user
the gui is located by default on `tty2`
to change to other tty's rub : 
- tty3 :  `alt + ctl + f3`
- tty4 :  `alt + ctl + f4`
you have tty's from : `tty1 ... tty6`
1. to check what's your current tty you need to run the folowing command 
	```shell
	tty # gives you current tty : /dev/tty2 
```
##### why we use tty ? 
1. we use tty to be able to connect multiple users or same user in the same time for exemple when we performe an action that will block us from writing on the terminal we can use tty to switch to another evirement and do some other tasks
2. when we run tty command in the gui terminal : we get __/dev/pts/0..n__
	 `pts`  : pseudo screen

```bash
# commands of today
sleep 2  # this command will sleep the terminal for 4 ms 
reboot   # this command will reboot the machine
```

## Some basic linux commands 
1. `date`  command
```bash 
date  # returns the current date [Wed Jul  3 06:03:44 PM EDT 2024]
# the date command arguments or flags
date +%R  # get the curent time  hh-mm
date +%x  # get the current date yyyy-dd-
-------------------
cal  # returns the calender of this month 
cal 2013 # returns the full cal of the selected year
cal 1 2023 # get the cal of january first 2023
```

2. what is the user
```bash 
whoami   # returns the current user
su - user_name  # switch between users 
su  # change to root
exit or ctl + d
---------
su with -  # change user with working dir as well
su # change only the user
```

 - How to perform command chaining 
 ```bash 
 pwd ; echo "one"  # seperate by semi colone ;
 pwd && echo "one" # seperate by an An ampersand
```


3. file sys commands 
```bash 
pwd  # print working directory
```

## File system hierarchy in Linux :
1. linux follows the approach of a single enverted tree 
2. `/`  this is called root directory it's the top of our file sys hierarchy
3. in Linux `/home` called _directory_ and in windows `\Usrs` called _folder_

- default table : 
```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```

> Everything in linux is a file

| directory | description                                                                                                  |
| --------- | ------------------------------------------------------------------------------------------------------------ |
| `/home`   | this directoy contains all the users [user1, user2 ....] excluding the root --> home directory for the users |
| `/root`   | this directory contains the root of the sys -> this is the home directory for the root                       |
| `/bin`    | this directory holds the binary files and commands                                                           |
| `/boot`   | files that starts boot process                                                                               |
| `/dev`    | devices including hard discs                                                                                 |
| `/etc`    | configuration files                                                                                          |
| `/sbin`   | binary files and commands of a `super user`                                                                  |
| `/tmp`    | temporary files                                                                                              |
| `/usr`    | file shared like [themes, ....]                                                                              |
| `/var`    | files that changes frequently                                                                                |
| `/media`  | mounted devices                                                                                              |
| `/mnt`    | mount external devices                                                                                       |
| `/lib`    | libraries for 32bit devices                                                                                  |
| `/lin64`  | libraries  for 64bit devices                                                                                 |
| `/opt`    | holdes files of an applications                                                                              |
| `/srv`    | services                                                                                                     |

## Navigation absolute path and relative path :

`ls`  : list content of a directory
`cd`  : change current directory
#### Relative and absolute path 
`absolute` : `cd /home/user1/Desktop`
`relative` : `cd Desktop`  --> from where i am go to this directory
`.` : current working directory
`..` : parent working directory

<mark>_Linux is case sensitive_</mark>  

### Command options 

> `command <>[option or options] <>[argument or arguments]` 

`-L`  :  long listing 
`-a`  : all file including hidden ones
`la -a -l`  _or_ `ls -la`
`ls -R`  : list all content in current working dir with nested dirs _recursive_  we can also use `tree` but it needs to be installed first by running `sudo apt install tree`
`ls -r` : the `-r` flag or reversed is an argument that returns the listing of a dir in a desc order alphabiticly
`ls -ld`  :  the `-d` flag or _directory_ is used to display a long listing of a directory for exemple : 
```bash
ls -ld work/ # this command will not display what is inside the work dir in fact it will list the dir it self as one block 
# output : 
# drwxrw-r-- 7 houssam houssam 201 Dec 12 01:10 work/
```
`ls -lc`  : the `-c` flag will list the items asc based on the time stamps


| file type | meaning                  |
| --------- | ------------------------ |
| `d`       | directory                |
| -         | regular file             |
| `c`       | character device         |
| `b`       | block device : hard disk |
| `l`       | sumbulic link            |
permissions :
				`rwx` : user permission 
				`rwx` : group permission 
				`rwx` : others permission

#### File handling 
`touch`  : create an emplty file if not exists if exists it will change the time stamps
`cat`      : or _concatinaite_ this command is used to red content of a file 
`ctrl + o`  : write out 
`alt + .`    : use last argument
`mkdir dir_name`  : make a new directory
<mark>create nested dirs</mark> : `mkdir -p dir1/dir2`  ___  `p` : _parent_ this argument used to create nested dirs in one line and if a dir does not exists it will be created

## Copy & move file or directory 
1. <mark>FIle </mark>  ---->  `cp`  : copy   -> `cp source destination`  _you can also_ change the name of the file when copying by using this command : `cp source destination/<new_name>`
2. <mark>Directory</mark>   ---> we should add the flag `-r` to the `cp` command to copy a directory :  `cp -r work/project1 work2/project2`
3. <mark> Copy content of a directory </mark>  ---> we use `*` astrics this is the syntax : 
	`cp -r /etc/* work/project1` we add -r to make sure that the directories 
	will be included as well in the copying process
3. you can view <mark>files</mark> while copying by adding the flag : `-v`  verbous
4. `mv`  --> this command cuts a file from current location to another or can be used to edit name of a file or directory
5. `df`  show discs
6. `history`  --> show all the history of commands

### Rename & Remove a file or a directory

`mv old_name new_name`  -> the mv command is used to rename file or dir 
```bash 
mv -v file1 newFile  # the -v flag will display the output of renaming 
# output : renamed 'file1' -> 'newFile' 
```

> _Trick : _
> how to create a ceatain amount of files in one command :
> `touch file{1..29}`

#### Remouve file or dir 

`-i`  : or `_information_ `this flag can be added to the regular rm command to display a worning before deleting a file or a dir 

```bash 
rm -i file1 # remove file1 with worning before deleting 
# output rm : remove regular empty file 'file1' ? [y, n]
```

`-f`  : or `force`  this flag will remove forcely the dir and sub files 

```bash 
rm -rif dir1 # it eill remove the dir and all the sub dirc and files in the directory
```

#### Controles 
`ctrl + a`  --> takes you to the begining of the line if command is a big long 
`ctrl + e`  --> take you to the end of the line ...
`ctrl + k`  --> remove text from current position till the end
`ctrl + u`  --> remove text before current position till the begining of line


## Users & groups

`users` & `groups` are used for security purpuses 
each user has his own `UID`  -> or unique identification number 
> Type of users : 
> - super_user   :   `id = 0`
> - system_user :   `1 > id > 999`
> - regular_user :   `id = 1000`

All users configuration are located in : `/etc/passwd`
all groups configuration are located in : `/etc/group`  and each group has his own `GID` or _group id_
the file `passwd`  is like a database for all users 
when creating a new user the sys will create a primary group and assign that user to it Exemple 

```bash 
ls -l home/
# permissions -- user group size creation_date h_m  file_dir_name
# drwx-w----  23 housssam houssam 2001 Dec 12 10:20 dir1/
```

##### informations about user : 
1. we use the command `id <user_name>` to display informations of a specific user
-> regular user
```bash 
id 
# uid=1000(houssam) gid=1000(houssam) groups=1000(houssam) 4(adm)...
```

-> root user 
```bash 
id root
# uid=0(root) gid=0(root) groups=0(root)
```

![[Pasted image 20240705231227.png]]


`grep <username> location`   -> find a specific user esaly 
` | `  --> the pipe line is like a filter which filters the output of the first command passed to second one before displaying to the user

```bash 
grep houssam /etc/passwd 
# or we can also use the | pipe line syntaxe 
cat /etc/passwd | grep houssam
```

to display all groupes you should run the command : 
`getent [file = passwd or group ...] username`  --> or _<font color="#0f0">get entry</font>_ 
the diff between the `gerp` and `cat` approach and `getent` is that the first ones search for the word given in our case houssam so it could bring more than one line in the other hand the `getent` command returns the group named _houssam_ 
![[Pasted image 20240705231425.png]]

- _Recap_ : 
		- in this session we saw so far were is located users database which is `passwd` and also group database which is `group`
		- to access the users list we run the folowing commands : `grep user_name /etc/passwd` 
		- to access the group list and look up for a specific group we run the folowing command : `cat /etc/group | grep houssam`


# How to gain super user access 

`sudo` --> do this command as super user 

```bash
sudo <command>  # 
sudo -i    # switch to super user
```

the command `sudo -i` switches to the root user if you don't even though you don't know the super user password 
##### change user password 

1. the command `passwd` is used to change user password

```bash
passwd # run this command
current : ...
new : ...
```

### add user to group 

- in order to add a user to a specified group you must run the following command

```bash
gpasswd -a <username> <group_name>    # add user to a group
gpasswd -d <username> <group_name>    # remove a user from a group
```


## Create users & groups

1. create a new user

```shell
sudo useradd user_name
```

2. after creating the user we need to assign to it his own password by running the following command 

```shell 
sudo passwd user_name
```