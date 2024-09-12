
To download python go to this link: 
https://www.python.org/downloads
there's python 3 and python 2, python 2 is a legacy version of python 
there's some apps designed for code editing we call 'em (IDE) which stands for Integrated Development Environment.   these (IDEs) help us writing our code, pointing us in the right direction and have some really cool features 
one of the Most Popular popular (IDEs) with python is call PyCharm you can download it from this link: 
https://www.jetbrains.com/pycharm
PS: there's two versions of PyCharm (Professional and Community). 
we will download the free Community version
### variables
they are like containers that hold some data or pieces of information which make it easier to work with these data. 
check out this code: 
```plaintext
character_name = "Tom"
character_age = "50"
print("There once was a man named " + character_name + ", ")
print("he was " + character_age + " years old. ")
print("he really liked the name " + character_name + ", ")
print("but didn't like being " + character_age + ". ")
```
the variables here are ::characater_name:: and ::character_age:: so if i changed tom and 50 what is basically the data in the variables, it will change automatically in our program. 
we can also give a new variable name half way through our story like this: 
```plaintext
character_name = "Tom"
character_age = "50"
print("There once was a man named " + character_name + ", ")
print("he was " + character_age + " years old. ")
character_name = "Mike"
print("he really liked the name " + character_name + ", ")
print("but didn't like being " + character_age + ". ")
```
therefore, the last two lines will replace the ::character_name:: will be mike instead of tom. 
there's a data type for python which is called ::strings:: like ::tom:: or ::50:: which is basically a plain text. 
there's also another type which numbers, therefore the line; 
```plaintext
character_age = "50"
```
can be written like this: 
```plaintext
character_age = 50
```
without the quotation marks
we can also store what is called a boolean value which is a binary variable, having two possible values called “true” and “false.”.
### Working with Strings
to add a new line use 
```plaintext
\n
```
so in a code, it would be like this: 
```plaintext
print("The Sun \nAcademy")
```
and it would come like this: 
The Sun
Academy
if you want to print out a quotation mark use the forward slash which means  render the next symbol as it is
```plaintext
\"
```
some functions do cool stuff like this: 
```plaintext
print("Sun" .upper())
```
which output the word like this: 
SUN
you can also replace some words like this: 
```plaintext
name = "car & Cat"
print(name.replace("car", "Dog"))
```
which will output text like this: 
Dog & Cat
### Working with Numbers
when using numbers with variables and you want to add a string like this: 
```plaintext
my_num = 5
print(my_num + 'is a good number')
```
this will output an error, so to do this the right way we can use: 
```plaintext
my_num = 5
print(str(my_num) + ' is a good number')
```
which will output a text like this: 
5 is a good number
we can import more functions like this from what we call a module, for example : 
```plaintext
from math import *
```
```plaintext
from math import *
print(sqrt(36))
```
this will output the number six which is the square root for 36. 
### Getting Input from User
let's say we want to make a program that asks a user for his name and says hello. 
to do this we will use the input command 
```plaintext
input("Enter your Name: ")
```
then we will store that prompt in a variable like this; 
```plaintext
name = input("Enter your Name: ")
```
now we want to say hello so we will use the print command: 
```plaintext
print("Hello " + name + "!")
```
we should get something like this: 
Enter your Name: Ahmed
Hello Ahmed!
### Build a Basic Calculator in Python 
let's make a simple calculator like this: 
```plaintext
num_1 = input("Enter your First Number: ")
num_2 = input("Enter your Second Number ")
result = num_1 + num_2
print(result)
```
this code will output a wrong answer, let's say we put 5 for the first number and 8 for the second number; python will think of this as a string, not a number so it will give you 58 as an answer. 
in order to fix this we have two solutions: 
1. using the ::int:: function like this: 
```plaintext
num_1 = input("Enter your First Number: ")
num_2 = input("Enter your Second Number ")
result = int(num_1) + int(num_2)
print(result)

```
but the ::int:: won't work with decimal numbers so we will use the second method 
2. using the ::float:: function like this: 
```plaintext
num_1 = input("Enter your First Number: ")
num_2 = input("Enter your Second Number ")
result = float(num_1) + float(num_2)
print(result)
```




