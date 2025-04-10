# Shell Scripting

- A shell provide an environment to a user to execute commands and interact with kernel.
- Shell script consist of set of commands to perform a task.
- All the commands execute sequentially.
- Some task like file manipulation, program execution, user interaction, automation of task etc can be done.

# There are different types of shell

1. bash
2. sh
3. ksh
4. tsh
5. fish
6. zsh

# what is my shell type?

echo $0

# Details about OS

cat etc/os-release

# whoami

# check available shells

echo etc/shells

# what is shebang?

- To tell linux which shell to use, to execute this file
  #!/bin/bash

# Sending out put to terminal

echo "hey what's your name"

# how to run a script

- Make sure script has execute permission rwx
- ./file_name.sh { it'll ask for the file permission }
- bash file_name.sh { it won't ask for permission }

# How to check file permission

ls -ltr

# How to give file permission

chmod +x file_name.sh

# ctrl+c to terminate

# ctrl+z to stop

# Comments

- # single line comment
- <<comment
  this
  is
  multi
  line comment
  comment

# Variables

a=10
name="ashish kushwaha"

echo "my name is $name and $age"

variable_name = $(command_name)

# Constant variable

readonly var_name = "hi"

# Arrays

## How to define an array?

space separated values

myArray=( 1 2 Hello "Hey man" )

## How to get values from an array?

get all values
echo "${myArray[*]}"

echo "${myArray[0]}"
echo "${myArray[1]}"

## How to get length of array?

echo "${#myArray[*]}"

## how to get specific range of values

echo "${myArray[*]:1}"

## get array elements from index number 2 to +3 more elements

echo "${myArray[*]:2:3}"

# How to update an array

my_array+=( 1 2 300.00008 )

# Array key-value pair

declare -A array_name
array_name=( [name]=Paul [age]=20 )

echo "${array_name[key]}"

# String Operation

length=${#my_array}
uppercase=${my_array^^}
lowercase=${my_array,,}

replace=${var_name/old_word/new_word}

slice=${my_var:start_char_index:length}

# User Interaction

## Taking input from user

read variable_name
echo "hwo are you $variable_name"

read -p "your name" variable_name

# Arithmetic Operation

let mul=4\*5
echo "$mul"

or you can do

echo "add is $((78+98))"

# Conditional Statement

`if [[$marks -gt 70]]
then
      echo "you are passed"
else
      echo "you are failed"
fi`

`if [[$marks -ge 70]]
then
      echo "you are passed A+"
elif [[$marks -ge 50]]
then
      echo "you are passed A"
else
      echo "you are failed"
fi`

# comparison operators

-eq is used for numeric value
== is used for string

equal - -eq/==
Greater than or equal to - -ge
Less than or equal to - -le
Not Equal - -ne/!=
Greater Than - -gt
Less Than - -lt

# Case Statement

`case $marks in
        a) date;;
        b) ls;;
        \*) echo "non valid input"
esac
`

`case $marks in
        a)
                  echo "do one thing"
                  echo "do second thing"
                  echo "do third thing"
                  ;;
        b) ls;;
        \*) echo "non valid input"
esac
`

# Logical operator &&, ||, !

1. `if [[$marks -gt 70]] && [[$marks -gt 90]]
then
      echo "you are passed"
else
      echo "you are failed"
fi`

2. `[[$marks -gt 70]] && echo "you'r good || echo "you'r bad"`

# For loop

`for i in 1 2 3 4 5
do
        echo "number is $i"
done`

`for name in name1 name2 name3
do
        echo "name is $name"
done`

## using wild card

`for i in {1..10}
do
        echo "number is $i"
done`

## get values from a file

FILE=/file_path
`for name in $(cat $FILE)
do
        echo "some is $name"
done`

## get values of array

myArray=(1 2 3 "john" hi hello)
length=${#myArray[*]}

for arithmetic we need double ()
`for(( i=0; i<$length; i++))
do
      echo "values of arrays is ${myArray[$i]}"
done
`

# while loop

count=0
num=10

`while [[ $count -le $num ]]
do
      echo "value of count var is $count"
      let count++
done`

# until loop - opposite to while loop

a=10
`until [[$a -eq 1]]
do
      echo $a
      let a--
done`

# infinite loop

`while true
do
      echo "thanks"
      sleep 2s
done`

`if (( ;; ))
do
      echo "thanks"
      sleep 2s
fi`

# read file with while loop

`while read myVar
do
      echo "value from file is $myVar"
done < file_name.txt`

# To read content frm a csv file

`while IFS="," read id name age
do
      echo "id is $id"
      echo "name is $name"
      echo "age is $age"
done < file_name.csv`

# Function

function my_func {
echo "hi"
}

my_func() {
echo "hi"
}

my_func

## arguments in function

`my_func() {
  local num=$1
  local num1=$2
  echo "num is $num and num2 id $num2"
}`

my_func 33 44

# Arguments passing in shell script

`bash myscript.sh arg1 arg2`

- Hogg/ to access these argunpnts inside
  our script?

1. To get no. of arguments : $#
2. To display all arguments : $@
3. To use or display a argument: $1 $2 ..

## arguments with for loop

`for arg in $@
do
      echo "Argument is $arg"
done`

## SHIFT

when we pass multiple arguments, we can shift.

echo "user name $1"
shift
echo "description is $@"

# use full concepts

## break - to stop the loop

## continue - to stop current iteration of loop and start next iteration

## sleep command

it will wait for 2 seconds
sleep 2s

## exit - to stop script at a point

## exit status $? - give you status of previous command if that was successful, it give 0

## Connectivity check script

ping -c 1 www.google.com

## basename - strip directory info and only give filename

## dirname - strip the filename and gives directory path

## realpath - gives you full path for a file

## Check if file/dir exist -

- if [[-d folder_name]] - If folder exists
- if [[! -f folder_name]] - If folder not exists

- if [[-f file_name]] - If file exists
- if [[! -f file_name]] - If file not exists

# Bash variable

## RANDOM - A random integer between 0 and 32767 is generated

## UID - User ID of the user logged in

## Redirection in script

`> (over write)`
`>>`

## what is /dev/null

In case if you don't wanna print the output of a command on terminal or write in a file,

cd /root &> /dev/null

## Print name of the script

echo "the name of the script is : ${0}"

## Log Messages

- If you want to maintain the logging for you script, you can use logger in your script.
- you can find your logs under : /var/logs/messages
- example: # logger "Hey buddy"

inside your script file
logger "this is log file"

## Debugging

set -x
set -e : if we want to exit our script when a command fail

# Running script in background

nohup file_name.sh &

# Automate our script

## For scheduling only one time, use AT

at 12:09 PM
<your_command>
Ctrl+D

atq : to check scheduled job
atrm <id> : to remove the schedule

## using crontab

To check the existing jobs - crontab -l
To add new job - crontab -e

https://crontab.guru/

`* * * * * cd file_path && bash run_any_script.sh`

# Shortcut

## delete one line

go to start of the line press d two times

# Project 1 Monitoring Free RAM Space

free : to check memory

free -mt : to check memory is MB

free -mt | grep "Total"

free -mt | grep "Total" | awk '{print $4}'

FREE_SPACE=free -mt | grep "Total" | awk '{print $4}'
TH=500

`if [[ $FREE_SPACE -lt $TH ]]
then
      echo "warning RAM is running low"
else
      echo "RAM space is sufficient - $FREE_SPACE M"
fi`

# Project 2 Monitoring Free Disk Space and Send email

df : disk space
df -H

df -H | egrep -v "Filesystem|temps" | grep "sda2" | awk '{print $5}'

`FU=df -H | egrep -v "Filesystem|temps" | grep "sda2" | awk '{print $5}'
if [[ $FU -ge 80 ]]
then
      echo "Warning, disk space is low"
else
      echo "All good"
fi`

## send email using postfix

# Archive older files or Archive large files

## Project Requirement

In the given directory, if you find files more than a given size ex:
20MB or files older than given days ex:10 days

Compress those files and move in a 'archive' folder.

## Steps of script:

Provide the path of directory
Check if the directory is present or not
Create 'archive' folder if not already present
Find all the files with size more than 20MB
Compress each file
Move the compressed files in 'archive' folder
Make a cron job to run the script every day at given time

`#Variables
BASE=/home/paul/tutorials/find_command
DAYS=1O
DEPTH=10
RUN=0
#Check if the directory is present or not
if [ ! -d $BASE ]
then
      echo "directory does not exist: $BASE"
      exit 1
fi
#Create 'archive' folder if not present
if [ ! —d $BASE/archive ]
then
      mkdir $BASE/archive
fi
#Find the list of file larger then 20MB
for i in `find $BASE -maxdepth $DEPTH -type f -size +20M`
do
if [[$RUN -eq 0]]
then
echo "[$(date "+%Y-%m-%d %H:%M:%S")] archiving $i ==> $BASE/archive"
gzip $i || exit 1
mv $i.gz $BASE/archive || exit 1
fi
done
`

#### create cron job to run thin script

`05 01 * * * /home/paul/archive_project.sh`

- give permission to this script : chmod 777 archive_project.sh

# Creating Local Users : Project

## Requirement

- Script should be executed with root user else exit with status 1 and error message.
- Script will take 1st argument as user and rest will be treated as comment.
- Auto generate password for the user
- Upon successful execution of script, display the following
- username: <username>
- password: <auto_generated_password>
- host:

## Steps:

- Check if the script is being executed with superuser(root/sudo) privileges.

`if [[ "${UID}" -ne 0 ]]
then
      echo "Please run with sudo or root"
      exit 1
fi
`

- If the user doesn't supply at least one argument, then give them help.

`if [[ "${#}" -lt 1 ]]
then
      echo "Usage: ${0} USER_NAME [COMMENTS]..."
      echo 'create a user with name USER_NAME and comments fields of COMMENTS'
      exit 1
fi
`

- The first parameter is the user name and store it.

USER_NAME="${1}"

- The rest of the parameters are for the comments and store it.

`shift
COMMENT="{$@}"
`

- Generate a password.

PASSWORD=$(date +%s%N)

- Create the user with the password.

useradd -c "${COMMENT}" -m $USER_NAME

- Check to see if the useradd command succeeded.

`if [[ $? -ne 0 ]]
then
      echo "The account could not be created"
      exit 1
fi
`

- set the password to the user

`echo $PASSWORD | passwd -stdin $USER_NAME
`

- check password successfully set or not

`if [[ $? -ne 0]]
then
      echo 'password could not be set'
      exit 1
fi
`

- Force password change on first login.

passwd -e $USER_NAME

- Display the username, password, and the host where the user is created.

`echo
echo "Username: $USER_NAME"
echo
echo "Password: $PASSWORD"
echo
echo "Host name: $(hostname)"
`

- To test

`su - user_name
`
