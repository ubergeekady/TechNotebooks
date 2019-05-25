## #1 Intro

```python
# Programming involves listing all the things that must happen to solve a problem
# When writing a program first determine step-by-step what needs to happen
# Then convert those steps into the language being Python in this situation

# Every language has the following
# 1. The ability to accept input and store it in many ways
# 2. The ability to output information to the screen, files, etc.
# 3. The ability to conditionally do one thing or another thing
# 4. The ability to do something multiple times
# 5. The ability to make mathematical calculations
# 6. The ability to change data
# 7. (Object Oriented Programming) Model real world objects using code

# ---------- Hello World ----------

# Ask the user to input their name and assign it to the name variable
# Variable names start with a letter or _ and then can contain numbers
# Names are case sensitive so name is not the same as Name
name = input('What is your name ')

# Print out Hello followed by the name they entered
print('Hello ', name)

# You can't use the following for variable names
# and, del, from, not, while, as, elif, global,
# or, with, assert, else, if, pass, yield, break,
# except, import, print, class, exec, in, raise,
# continue, finally, is, return, def, for, lambda,
# try

# Single line comments are ignored by the interpreter
'''
So are multiline comments
'''

# ---------- MATH ON 2 VALUES ----------

# Ask the user to input 2 values and store them in variables num1 and num2
# split() splits input using whitespace
num1, num2 = input('Enter 2 numbers : ').split()

# Convert strings into regular numbers (integers)
num1 = int(num1)
num2 = int(num2)

# Add the values entered and store in sum
sum = num1 + num2

# Subtract the values and store in difference
difference = num1 - num2

# Multiply the values and store in product
product = num1 * num2

# Divide the values and store in quotient
quotient = num1 / num2

# Use modulus on the values to find the remainder
remainder = num1 % num2

# Print your results
# format() loads the variable values in order into the {} placeholders
print("{} + {} = {}".format(num1, num2, sum))
print("{} - {} = {}".format(num1, num2, difference))
print("{} * {} = {}".format(num1, num2, product))
print("{} / {} = {}".format(num1, num2, quotient))
print("{} % {} = {}".format(num1, num2, remainder))

# ---------- PROBLEM : MILES TO KILOMETERS ----------
# Sample knowing that kilometers = miles * 1.60934
# Enter Miles 5
# 5 miles equals 8.0467 kilometers

# Ask the user to input miles and assign it to the miles variable
miles = input('Enter Miles ')

# Convert from string to integer
miles = int(miles)

# Perform calculation by multiplying 1.60934 times miles
kilometers = miles * 1.60934

# Print results using format()
print("{} miles equals {} kilometers".format(miles, kilometers))

# ---------- CALCULATOR ----------
# Receive 2 numbers separated by an operator and show a result
# Sample
# Enter Calculation: 5 * 6
# 5 * 6 = 30

# Store the user input of 2 numbers and an operator
num1, operator, num2 = input('Enter Calculation: ').split()

# Convert strings into integers
num1 = int(num1)
num2 = int(num2)

# If, else if (elif) and else execute different code depending on a condition
if operator == "+":
    print("{} + {} = {}".format(num1, num2, num1+num2))

# If the 1st condition wasn't true check if this one is
elif operator == "-":
    print("{} - {} = {}".format(num1, num2, num1 - num2))
elif operator == "*":
    print("{} * {} = {}".format(num1, num2, num1 * num2))
elif operator == "/":
    print("{} / {} = {}".format(num1, num2, num1 / num2))

# If none of the above conditions were true then execute this by default
else:
    print("Use either + - * or / next time")

# Other conditional operators
# > : Greater than
# < : Less than
# >= : Greater than or equal to
# <= : Less than or equal to
# != : Not equal to

# ---------- IS BIRTHDAY IMPORTANT ----------
# We'll provide different output based on age
# 1 - 18 -> Important
# 21, 50, > 65 -> Important
# All others -> Not Important

# eval() converts a string into an integer if it meets the guidelines
age = eval(input("Enter age: "))

# Logical operators can be used to combine conditions
# and : If both are true it returns true
# or : If either are true it returns true
# not : Converts true into false and vice versa

# If age is both greater than or equal to 1 and less than or equal to 18 it is true
if (age >= 1) and (age <= 18):
    print("Important Birthday")

# If age is either 21 or 50 then it is true
elif (age == 21) or (age == 50):
    print("Important Birthday")

# We check if age is less than 65 and then convert true to false or vice versa
# This is the same as if we put age > 65
elif not(age < 65):
    print("Important Birthday")
else:
    print("Sorry Not Important")

# ---------- PROBLEM : DETERMINE GRADE ----------
# If age 5 go to kindergarten
# Ages 6 through 17 goes to grades 1 through 12
# If age is greater then 17 then say go to college
# Try to complete with 10 or less lines

# Ask for the age
age = eval(input("Enter age: "))

# Handle if age < 5
if age < 5:
    print("Too Young for School")

# Special output just for age 5
elif age == 5:
    print("Go to Kindergarten")

# Since a number is the result for ages 6 - 17 we can check them all
# with 1 condition
# Use calculation to limit the conditions checked
elif (age > 5) and (age <= 17):
    grade = age - 5
    print("Go to {} grade".format(grade))

# Handle everyone else
else:
    print("Go to College")#
```

## #2 Looping

```python
# Every program has the ability to perform actions on a list of
# values. The for loop can be used to do this.

# Each time we go through the loop variable i's value will be
# assigned the next value in our list

for i in [2,4,6,8,10]:
    print("i = ", i)

# We can also have range define our list for us. range(10) will
# create a list starting at 0 and go up to but not include
# the value passed to it.

for i in range(10):
    print("i = ", i)

# We can define the starting and ending value for range
for i in range(2, 10):
    print("i = ", i)

# You can use modulus to see if a number is odd or even
# If we divide an even by 2 there will be no remainder
# so if i % 2 == 0 we know it is true
i = 2
print((i % 2) == 0)

# ---------- PROBLEM : PRINT ODDS FROM 1 to 20 ----------
# Use a for loop, range, if and modulus to print out the odds

# Use for to loop through the list from 1 to 21

for i in range(1, 21):

# Use modulus to check that the result is NOT EQUAL to 0
# Print the odds

    if ((i % 2) != 0):
        print("i = ", i)

# ---------- WORKING WITH FLOATS ----------
# Floating point numbers are numbers with decimal values

your_float = input("Enter a float: ")

# We can convert a string into a float like this

your_float = float(your_float)

# We can define how many decimals are printed being 2
# here by putting :.2 before f
print("Rounded to 2 decimals : {:.2f}".format(your_float))

# ---------- PROBLEM : COMPOUNDING INTEREST ----------
# Have the user enter their investment amount and expected interest
# Each year their investment will increase by their investment +
# their investment * the interest rate
# Print out their earnings after a 10 year period

# Ask for money invested + the interest rate
money = input("How much to invest: ")
interest_rate = input("Interest Rate: ")

# Convert value to a float
money = float(money)

# Convert value to a float and round the percentage rate by 2 digits
interest_rate = float(interest_rate) * .01

# Cycle through 10 years using for and range from 0 to 9
for i in range(10):

    # Add the current money in the account + interest earned that year
    money = money + (money * interest_rate)

# Output the results
print("Investment after 10 years: {:.2f}".format(money))

# ---------- WORKING WITH FLOATS ----------
# When working with floats understand that they are not precise

# This should print 0 but it doesn't
i = 0.1 + 0.1 + 0.1 - 0.3
print(i)

# Floats will print nonsense beyond 16 digits of precision
i = .11111111111111111111111111111111
j = .00000000000000010000000000000001

print("Answer : {:.32}".format(i + j))

# ---------- ORDER OF OPERATIONS ----------
# When making calculations unless you use parentheses * and /
# will supersede + and -

print("3 + 4 * 5 = {}".format(3 + 4 * 5))

print("(3 + 4) * 5 = {}".format((3 + 4) * 5))

# ---------- THE WHILE LOOP ----------
# We can also continue looping as long as a condition is true
# with a while loop

# While loops are used when you don't know how many times
# you will have to loop

# We can use the random module to generate random numbers
import random

# Generate a random integer between 1 and 50
rand_num = random.randrange(1, 51)

# The value we increment in the while loop is defined before the loop
i = 1

# Define the condition that while true we will continue looping
while (i != rand_num):

    # You must increment your iterator inside the while loop
    i += 1

# Outside of the while loop when we stop adding whitespace
print("The random value is : ", rand_num)

# ---------- BREAK AND CONTINUE ----------
# Continue stops executing the code that remains in the loop and
# jumps back to the top

# Break jumps completely out of the loop

i = 1

while i <= 20:

    # If a number is even don't print it
    if (i % 2) == 0:
        i += 1
        continue

    # If i equals 15 stop looping
    if i == 15:
        break

    # Print the odds
    print("Odd : ", i)

    # Increment i
    i += 1

# ---------- PROBLEM : DRAW A PINE TREE ----------
# For this problem I want you to draw a pine tree after asking the user
# for the number of rows. Here is the sample program

'''
How tall is the tree : 5
    #
   ###
  #####
 #######
#########
    #
'''

# You should use a while loop and 3 for loops

# I know that this is the number of spaces and hashes for the tree
# 4 - 1
# 3 - 3
# 2 - 5
# 1 - 7
# 0 - 9
# Spaces before stump = Spaces before top

# So I need to
# 1. Decrement spaces by one each time through the loop
# 2. Increment the hashes by 2 each time through the loop
# 3. Save spaces to the stump by calculating tree height - 1
# 4. Decrement from tree height until it equals 0
# 5. Print spaces and then hashes for each row
# 6. Print stump spaces and then 1 hash

# Get the number of rows for the tree
tree_height = input("How tall is the tree : ")

# Convert into an integer
tree_height = int(tree_height)

# Get the starting spaces for the top of the tree
spaces = tree_height - 1

# There is one hash to start that will be incremented
hashes = 1

# Save stump spaces til later
stump_spaces = tree_height - 1

# Makes sure the right number of rows are printed
while tree_height != 0:

    # Print the spaces
    # end="" means a newline won't be added
    for i in range(spaces):
        print(' ', end="")

    # Print the hashes
    for i in range(hashes):
        print('#', end="")

    # Newline after each row is printed
    print()

    # I know from research that spaces is decremented by 1 each time
    spaces -= 1

    # I know from research that hashes is incremented by 2 each time
    hashes += 2

    # Decrement tree height each time to jump out of loop
    tree_height -= 1

# Print the spaces before the stump and then a hash
for i in range(stump_spaces):
    print(' ', end="")

print("#")
```

## #3 Math, Strings & Exception Handling

```python
# ---------- FORCE USER TO ENTER A NUMBER ----------
# By giving the while a value of True it will cycle until a break is reached
while True:

    # If we expect an error can occur surround potential error with try
    try:
        number = int(input("Please enter a number : "))
        break

    # The code in the except block provides an error message to set things right
    # We can either target a specific error like ValueError
    except ValueError:
        print("You didn't enter a number")

    # We can target all other errors with a default
    except:
        print("An unknown error occurred")

print("Thank you for entering a number")

# ---------- Problem : Implement a Do While Loop ----------
# Now I want you to implement a Do While loop in Python
# They always execute all of the code at least once and at
# the end check if a condition is true that would warrant
# running the code again. They have this format
# do {
#   ... Bunch of code ...
# } while(condition)

# I'll create a guessing game in which the user must chose
# a number between 1 and 10 of the following format
'''
Guess a number between 1 and 10 : 1
Guess a number between 1 and 10 : 3
Guess a number between 1 and 10 : 5
Guess a number between 1 and 10 : 7
You guessed it
'''

# Hint : You'll need a while and break

secret_number = 7

while True:
    guess = int(input("Guess a number between 1 and 10 : "))

    if guess == secret_number:
        print("You guessed it")
        break

# ---------- MATH MODULE ----------
# Python provides many functions with its Math module
import math

# Because you used import you access methods by referencing the module
print("ceil(4.4) = ", math.ceil(4.4))
print("floor(4.4) = ", math.floor(4.4))
print("fabs(-4.4) = ", math.fabs(-4.4))

# Factorial = 1 * 2 * 3 * 4
print("factorial(4) = ", math.factorial(4))

# Return remainder of division
print("fmod(5,4) = ", math.fmod(5,4))

# Receive a float and return an int
print("trunc(4.2) = ", math.trunc(4.2))

# Return x^y
print("pow(2,2) = ", math.pow(2,2))

# Return the square root
print("sqrt(4) = ", math.sqrt(4))

# Special values
print("math.e = ", math.e)
print("math.pi = ", math.pi)

# Return e^x
print("exp(4) = ", math.factorial(4))

# Return the natural logarithm e * e * e ~= 20 so log(20) tells
# you that e^3 ~= 20
print("log(20) = ", math.log(20))

# You can define the base and 10^3 = 1000
print("log(1000,10) = ", math.log(1000,10))

# You can also use base 10 like this
print("log10(1000) = ", math.log10(1000))

# We have the following trig functions
# sin, cos, tan, asin, acos, atan, atan2, asinh, acosh,
# atanh, sinh, cosh, tanh

# Convert radians to degrees and vice versa
print("degrees(1.5708) = ", math.degrees(1.5708))
print("radians(90) = ", math.radians(90))

# ---------- ACCURATE FLOATING POINT CALCULATIONS ----------

# The decimal module provides for more accurate floating point calculations
# With from you can reference methods without the need to reference the module
# like we had to do with math above
# We create an alias being D here to avoid conflicts with methods with
# the same name
from decimal import Decimal as D

sum = D(0)
sum += D("0.01")
sum += D("0.01")
sum += D("0.01")
sum -= D("0.03")

print("Sum = ", sum)

# ---------- STRINGS ----------
# Text is stored using the string data type
# You can use type to see the data type of a value
print(type(3))
print(type(3.14))

# Single quotes or double are both used for strings
print(type("3"))
print(type('3'))

samp_string = "This is a very important string"

# Each character is stored in a series of boxes labeled with index numbers
# You can get a character by referencing an index
print(samp_string[0])

# Get the last character
print(samp_string[-1])

# Get the last character
print(samp_string[3+5])

# Get the string length
print("Length :", len(samp_string))

# Get a slice by saying where to start and end
# The 4th index isn't returned
print(samp_string[0:4])

# Get everything starting at an index
print(samp_string[8:])

# Join or concatenate strings with +
print("Green " + "Eggs")

# Repeat strings with *
print("Hello " * 5)

# Convert an int into a string
num_string = str(4)

# Cycle through each character with for
for char in samp_string:
    print(char)

# Cycle through characters in pairs
# Subtract 1 from the length because length is 1 more then the highest index
# because strings are 0 indexed
# Use range starting at index 0 through string length and increment by
# 2 each time through
for i in range(0, len(samp_string)-1, 2):
    print(samp_string[i] + samp_string[i+1])

# Computers assign characters with a number known as a Unicode
# A-Z have the numbers 65-90 and a-z 97-122

# You can get the Unicode code with ord()
print("A =", ord("A"))

# You can convert from Unicode with chr
print("65 =", chr(65))

# ---------- PROBLEM : SECRET STRING ----------
# Receive a uppercase string and then hide its meaning by turning
# it into a string of unicodes
# Then translate it from unicode back into its original meaning

norm_string = input("Enter a string to hide in uppercase: ")

secret_string = ""

# Cycle through each character in the string
for char in norm_string:

    # Store each character code in a new string
    secret_string += str(ord(char))

print("Secret Message :", secret_string)

norm_string = ""

# Cycle through each character code 2 at a time by incrementing by
# 2 each time through since unicodes go from 65 to 90
for i in range(0, len(secret_string)-1, 2):

    # Get the 1st and 2nd for the 2 digit number
    char_code = secret_string[i] + secret_string[i+1]

    # Convert the codes into characters and add them to the new string
    norm_string += chr(int(char_code))

print("Original Message :", norm_string)

# ---------- SUPER AWESOME MIND SCRAMBLING PROBLEM ----------
# Make the above work with upper and lowercase with 1 addition and
# 1 subtraction

# Add these 2 changes

# secret_string += str(ord(char) - 23)

# norm_string += chr(int(char_code) + 23)
```

## #4 String Functions

```python
# ---------- STRING METHODS ----------

# Strings have many methods we can use beyond what I covered last time
rand_string = "   this is an important string   "

# Delete whitespace on left
rand_string = rand_string.lstrip()

# Delete whitespace on right
rand_string = rand_string.rstrip()

# Delete whitespace on right and left
rand_string = rand_string.strip()

# Capitalize the 1st letter
print(rand_string.capitalize())

# Capitalize every letter
print(rand_string.upper())

# lowercase all letters
print(rand_string.lower())

# Turn a list into a string and separate items with the defined
# separator
a_list = ["Bunch", "of", "random", "words"]
print(" ".join(a_list))

# Convert a string into a list
a_list_2 = rand_string.split()

for i in a_list_2:
    print(i)

# Count how many times a string occurs in a string
print("How many is :", rand_string.count("is"))

# Get index of matching string
print("Where is string :", rand_string.find("string"))

# Replace a substring
print(rand_string.replace("an ", "a kind of "))

# ---------- PROBLEM : ACRONYM GENERATOR ----------
# You will enter a string and then convert it to an acronym
# with uppercase letters like this
'''
Convert to Acronym : Random Access Memory
RAM
'''

# Ask for a string
orig_string = input("Convert to Acronym : ")

# Convert the string to all uppercase
orig_string = orig_string.upper()

# Convert the string into a list
list_of_words = orig_string.split()

# Cycle through the list
for word in list_of_words:

    # Get the 1st letter of the word and eliminate the newline
    print(word[0], end="")

print()

# ---------- MORE STRING METHODS ----------
# For our next problem some additional string methods are going to be
# very useful

letter_z = "z"
num_3 = "3"
a_space = " "

# Returns True if characters are letters or numbers
# Whitespace is false
print("Is z a letter or number :", letter_z.isalnum())

# Returns True if characters are letters
print("Is z a letter :", letter_z.isalpha())

# Returns True if characters are numbers (Floats are False)
print("Is 3 a number :", num_3.isdigit())

# Returns True if all are lowercase
print("Is z a lowercase :", letter_z.islower())

# Returns True if all are uppercase
print("Is z a uppercase :", letter_z.isupper())

# Returns True if all are spaces
print("Is space a space :", a_space.isspace())

# ---------- MAKE A isfloat FUNCTION ----------
# There is no way to check if a string contains a float
# so let's make one by defining our own function

# Functions allow use to avoid repeating code
# They can receive values (attributes / parameters)
# They can return values

# You define your function name and the names for the values
# it receives like this

def isfloat(str_val):
    try:

        # If the string isn't a float float() will throw a
        # ValueError
        float(str_val)

        # If there is a value you want to return use return
        return True
    except ValueError:
        return False

pi = 3.14

# We call our functions by name and pass in a value between
# the parentheses
print("Is Pi a Float :", isfloat(pi))

# ---------- PROBLEM : CAESAR'S CIPHER ----------
# Receive a message and then encrypt it by shifting the
# characters by a requested amount to the right
# A becomes D, B becomes E for example
# Also decrypt the message back again

# A-Z have the numbers 65-90 in unicode
# a-z have the numbers 97-122
# You get the unicode of a character with ord(yourLetter)
# You convert from unicode to character with chr(yourNumber)

# You should check if a character is a letter and if not
# leave it as its default

# Hints
# Use isupper() to decided which unicodes to work with
# Add the key (number of characters to shift) and if
# bigger or smaller then the unicode for A, Z, a, or z
# increase or decrease by 26

# Receive the message to encrypt and the number of characters to shift
message = input("Enter your message : ")
key = int(input("How many characters should we shift (1 - 26)"))

# Prepare your secret message
secret_message = ""

# Cycle through each character in the message
for char in message:

    # If it isn't a letter then keep it as it is in the else below
    if char.isalpha():

        # Get the character code and add the shift amount
        char_code = ord(char)
        char_code += key

        # If uppercase then compare to uppercase unicodes
        if char.isupper():

            # If bigger than Z subtract 26
            if char_code > ord('Z'):
                char_code -= 26

            # If smaller than A add 26
            elif char_code < ord('A'):
                char_code += 26

        # Do the same for lowercase characters
        else:
            if char_code > ord('z'):
                char_code -= 26
            elif char_code < ord('a'):
                char_code += 26

        # Convert from code to letter and add to message
        secret_message += chr(char_code)

    # If not a letter leave the character as is
    else:
        secret_message += char

print("Encrypted :", secret_message)

# To decrypt the only thing that changes is the sign of the key
key = -key

orig_message = ""

for char in secret_message:
    if char.isalpha():
        char_code = ord(char)
        char_code += key

        if char.isupper():
            if char_code > ord('Z'):
                char_code -= 26
            elif char_code < ord('A'):
                char_code += 26
        else:
            if char_code > ord('z'):
                char_code -= 26
            elif char_code < ord('a'):
                char_code += 26

        orig_message += chr(char_code)

    else:
        orig_message += char

print("Decrypted :", orig_message)

# ---------- EXTRA HOMEWORK ----------
# For homework put the duplicate code above in a function
```

## #5 Functions

```python
# ---------- STRING METHODS ----------

# Strings have many methods we can use beyond what I covered last time
rand_string = "   this is an important string   "

# Delete whitespace on left
rand_string = rand_string.lstrip()

# Delete whitespace on right
rand_string = rand_string.rstrip()

# Delete whitespace on right and left
rand_string = rand_string.strip()

# Capitalize the 1st letter
print(rand_string.capitalize())

# Capitalize every letter
print(rand_string.upper())

# lowercase all letters
print(rand_string.lower())

# Turn a list into a string and separate items with the defined
# separator
a_list = ["Bunch", "of", "random", "words"]
print(" ".join(a_list))

# Convert a string into a list
a_list_2 = rand_string.split()

for i in a_list_2:
    print(i)

# Count how many times a string occurs in a string
print("How many is :", rand_string.count("is"))

# Get index of matching string
print("Where is string :", rand_string.find("string"))

# Replace a substring
print(rand_string.replace("an ", "a kind of "))

# ---------- PROBLEM : ACRONYM GENERATOR ----------
# You will enter a string and then convert it to an acronym
# with uppercase letters like this
'''
Convert to Acronym : Random Access Memory
RAM
'''

# Ask for a string
orig_string = input("Convert to Acronym : ")

# Convert the string to all uppercase
orig_string = orig_string.upper()

# Convert the string into a list
list_of_words = orig_string.split()

# Cycle through the list
for word in list_of_words:

    # Get the 1st letter of the word and eliminate the newline
    print(word[0], end="")

print()

# ---------- MORE STRING METHODS ----------
# For our next problem some additional string methods are going to be
# very useful

letter_z = "z"
num_3 = "3"
a_space = " "

# Returns True if characters are letters or numbers
# Whitespace is false
print("Is z a letter or number :", letter_z.isalnum())

# Returns True if characters are letters
print("Is z a letter :", letter_z.isalpha())

# Returns True if characters are numbers (Floats are False)
print("Is 3 a number :", num_3.isdigit())

# Returns True if all are lowercase
print("Is z a lowercase :", letter_z.islower())

# Returns True if all are uppercase
print("Is z a uppercase :", letter_z.isupper())

# Returns True if all are spaces
print("Is space a space :", a_space.isspace())

# ---------- MAKE A isfloat FUNCTION ----------
# There is no way to check if a string contains a float
# so let's make one by defining our own function

# Functions allow use to avoid repeating code
# They can receive values (attributes / parameters)
# They can return values

# You define your function name and the names for the values
# it receives like this

def isfloat(str_val):
    try:

        # If the string isn't a float float() will throw a
        # ValueError
        float(str_val)

        # If there is a value you want to return use return
        return True
    except ValueError:
        return False

pi = 3.14

# We call our functions by name and pass in a value between
# the parentheses
print("Is Pi a Float :", isfloat(pi))

# ---------- PROBLEM : CAESAR'S CIPHER ----------
# Receive a message and then encrypt it by shifting the
# characters by a requested amount to the right
# A becomes D, B becomes E for example
# Also decrypt the message back again

# A-Z have the numbers 65-90 in unicode
# a-z have the numbers 97-122
# You get the unicode of a character with ord(yourLetter)
# You convert from unicode to character with chr(yourNumber)

# You should check if a character is a letter and if not
# leave it as its default

# Hints
# Use isupper() to decided which unicodes to work with
# Add the key (number of characters to shift) and if
# bigger or smaller then the unicode for A, Z, a, or z
# increase or decrease by 26

# Receive the message to encrypt and the number of characters to shift
message = input("Enter your message : ")
key = int(input("How many characters should we shift (1 - 26)"))

# Prepare your secret message
secret_message = ""

# Cycle through each character in the message
for char in message:

    # If it isn't a letter then keep it as it is in the else below
    if char.isalpha():

        # Get the character code and add the shift amount
        char_code = ord(char)
        char_code += key

        # If uppercase then compare to uppercase unicodes
        if char.isupper():

            # If bigger than Z subtract 26
            if char_code > ord('Z'):
                char_code -= 26

            # If smaller than A add 26
            elif char_code < ord('A'):
                char_code += 26

        # Do the same for lowercase characters
        else:
            if char_code > ord('z'):
                char_code -= 26
            elif char_code < ord('a'):
                char_code += 26

        # Convert from code to letter and add to message
        secret_message += chr(char_code)

    # If not a letter leave the character as is
    else:
        secret_message += char

print("Encrypted :", secret_message)

# To decrypt the only thing that changes is the sign of the key
key = -key

orig_message = ""

for char in secret_message:
    if char.isalpha():
        char_code = ord(char)
        char_code += key

        if char.isupper():
            if char_code > ord('Z'):
                char_code -= 26
            elif char_code < ord('A'):
                char_code += 26
        else:
            if char_code > ord('z'):
                char_code -= 26
            elif char_code < ord('a'):
                char_code += 26

        orig_message += chr(char_code)

    else:
        orig_message += char

print("Decrypted :", orig_message)

# ---------- EXTRA HOMEWORK ----------
# For homework put the duplicate code above in a function
```

## #6 Lists

```python
# ---------- LEARN TO PROGRAM 6 ----------

import random
import math

# With lists we can refer to groups of data with 1 name

# Each item in the list corresponds to a number (index)
# just like how people have identification numbers.
# By default the 1st item in a list has the index 0

# [0 : "string"] [1 : 1.234] [2 : 28] [3 : "c"]

# Python lists can grow in size and can contain data
# of any type

randList = ["string", 1.234, 28]

# Create a list with range
oneToTen = list(range(10))

# An awesome thing about lists is that you can use many
# of the same functions with them that you used with strings

# Combine lists
randList = randList + oneToTen

# Get the 1st item with an index
print(randList[0])

# Get the length
print("List Length :", len(randList))

# Slice a list to get 1st 3 items
first3 = randList[0:3]

# Cycle through the list and print the index
for i in first3:
    print("{} : {}".format(first3.index(i), i))

# You can repeat a list item with *
print(first3[0] * 3)

# You can see if a list contains an item
print("string" in first3)

# You can get the index of a matching item
print("Index of string :", first3.index("string"))

# Find out how many times an item is in the list
print("How many strings :", first3.count("string"))

# You can change a list item
first3[0] = "New String"

for i in first3:
    print("{} : {}".format(first3.index(i), i))

# Append a value to the end of a list
first3.append("Another")

# ---------- PROBLEM : CREATE A RANDOM LIST ----------
# Generate a random list of 5 values between 1 and 9
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# ---------- SORT A LIST : BUBBLE SORT ----------
# The Bubble sort is a way to sort a list
# It works this way
# 1. An outer loop decreases in size each time
# 2. The goal is to have the largest number at the end of
#    the list when the outer loop completes 1 cycle
# 3. The inner loop starts comparing indexes at the beginning
#    of the loop
# 4. Check if list[Index] > list[Index + 1]
# 5. If so swap the index values
# 6. When the inner loop completes the largest number is at
#    the end of the list
# 7. Decrement the outer loop by 1

# Create the value that will decrement for the outer loop
# Its value is the last index in the list
i = len(numList) - 1

while i > 1:

    j = 0

    while j < i:

        # Tracks the comparison of index values
        print("\nIs {} > {}".format(numList[j], numList[j+1]))
        print()

        # If the value on the left is bigger switch values
        if numList[j] > numList[j+1]:

            print("Switch")

            temp = numList[j]
            numList[j] = numList[j + 1]
            numList[j + 1] = temp

        else:
            print("Don't Switch")

        j += 1

        # Track changes to the list
        for k in numList:
            print(k, end=", ")
        print()

    print("END OF ROUND")

    i -= 1

for k in numList:
    print(k, end=", ")
print()

# ---------- MORE LIST FUNCTIONS ----------
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# Sort a list
numList.sort()

# Reverse a list
numList.reverse()

for k in numList:
    print(k, end=", ")
print()

# Insert value at index insert(index, value)
numList.insert(5, 10)

# Delete first occurrence of value
numList.remove(10)

for k in numList:
    print(k, end=", ")
print()

# Remove item at index
numList.pop(2)

for k in numList:
    print(k, end=", ")
print()

# ---------- LIST COMPREHENSIONS ----------
# You can construct lists in interesting ways using
# list comprehensions

# Perform an operation on each item in the list

# Create a list of even values
evenList = [i*2 for i in range(10)]

for k in evenList:
    print(k, end=", ")
print()

# List of lists containing values to the power of
# 2, 3, 4
numList = [1,2,3,4,5]

listOfValues = [[math.pow(m, 2), math.pow(m, 3), math.pow(m, 4)]
                for m in numList]

for k in listOfValues:
    print(k)
print()

# Create a 10 x 10 list
multiDList = [[0] * 10 for i in range(10)]

# Change a value in the multidimensional list
multiDList[0][1] = 10

# Get the 2nd item in the 1st list
# It may help to think of it as the 2nd item in the 1st row
print(multiDList[0][1])

# Get the 2nd item in the 2nd list
print(multiDList[1][1])

# ---------- MULTIDIMENSIONAL LIST ----------

# Show how indexes work with a multidimensional list
listTable = [[0] * 10 for i in range(10)]

for i in range(10):

    for j in range(10):
        listTable[i][j] = "{} : {}".format(i, j)

for i in range(10):

    for j in range(10):
        print(listTable[i][j], end=" || ")
    print()

# ---------- PROBLEM : CREATE MULTIPLICATION TABLE ----------
# With 2 for loops fill the cells in a multidimensional
# list with a multiplication table using values 1 - 9
'''
1, 2, 3, 4, 5, 6, 7, 8, 9,
2, 4, 6, 8, 10, 12, 14, 16, 18,
3, 6, 9, 12, 15, 18, 21, 24, 27,
4, 8, 12, 16, 20, 24, 28, 32, 36,
5, 10, 15, 20, 25, 30, 35, 40, 45,
6, 12, 18, 24, 30, 36, 42, 48, 54,
7, 14, 21, 28, 35, 42, 49, 56, 63,
8, 16, 24, 32, 40, 48, 56, 64, 72,
9, 18, 27, 36, 45, 54, 63, 72, 81
'''

# Create the multidimensional list
multTable = [[0] * 10 for i in range(10)]

# This will increment for each row
for i in range(1, 10):

    # This will increment for each item in the row
    for j in range(1, 10):

        # Assign the value to the cell
        multTable[i][j] = i * j

# Output the data in the same way you assigned it
for i in range(1, 10):

    for j in range(1, 10):
        print(multTable[i][j], end=", ")

    print()
```

## #7 Recursive Functions & Dictionaries

```python
# ---------- LEARN TO PROGRAM 6 ----------

import random
import math

# With lists we can refer to groups of data with 1 name

# Each item in the list corresponds to a number (index)
# just like how people have identification numbers.
# By default the 1st item in a list has the index 0

# [0 : "string"] [1 : 1.234] [2 : 28] [3 : "c"]

# Python lists can grow in size and can contain data
# of any type

randList = ["string", 1.234, 28]

# Create a list with range
oneToTen = list(range(10))

# An awesome thing about lists is that you can use many
# of the same functions with them that you used with strings

# Combine lists
randList = randList + oneToTen

# Get the 1st item with an index
print(randList[0])

# Get the length
print("List Length :", len(randList))

# Slice a list to get 1st 3 items
first3 = randList[0:3]

# Cycle through the list and print the index
for i in first3:
    print("{} : {}".format(first3.index(i), i))

# You can repeat a list item with *
print(first3[0] * 3)

# You can see if a list contains an item
print("string" in first3)

# You can get the index of a matching item
print("Index of string :", first3.index("string"))

# Find out how many times an item is in the list
print("How many strings :", first3.count("string"))

# You can change a list item
first3[0] = "New String"

for i in first3:
    print("{} : {}".format(first3.index(i), i))

# Append a value to the end of a list
first3.append("Another")

# ---------- PROBLEM : CREATE A RANDOM LIST ----------
# Generate a random list of 5 values between 1 and 9
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# ---------- SORT A LIST : BUBBLE SORT ----------
# The Bubble sort is a way to sort a list
# It works this way
# 1. An outer loop decreases in size each time
# 2. The goal is to have the largest number at the end of
#    the list when the outer loop completes 1 cycle
# 3. The inner loop starts comparing indexes at the beginning
#    of the loop
# 4. Check if list[Index] > list[Index + 1]
# 5. If so swap the index values
# 6. When the inner loop completes the largest number is at
#    the end of the list
# 7. Decrement the outer loop by 1

# Create the value that will decrement for the outer loop
# Its value is the last index in the list
i = len(numList) - 1

while i > 1:

    j = 0

    while j < i:

        # Tracks the comparison of index values
        print("\nIs {} > {}".format(numList[j], numList[j+1]))
        print()

        # If the value on the left is bigger switch values
        if numList[j] > numList[j+1]:

            print("Switch")

            temp = numList[j]
            numList[j] = numList[j + 1]
            numList[j + 1] = temp

        else:
            print("Don't Switch")

        j += 1

        # Track changes to the list
        for k in numList:
            print(k, end=", ")
        print()

    print("END OF ROUND")

    i -= 1

for k in numList:
    print(k, end=", ")
print()

# ---------- MORE LIST FUNCTIONS ----------
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# Sort a list
numList.sort()

# Reverse a list
numList.reverse()

for k in numList:
    print(k, end=", ")
print()

# Insert value at index insert(index, value)
numList.insert(5, 10)

# Delete first occurrence of value
numList.remove(10)

for k in numList:
    print(k, end=", ")
print()

# Remove item at index
numList.pop(2)

for k in numList:
    print(k, end=", ")
print()

# ---------- LIST COMPREHENSIONS ----------
# You can construct lists in interesting ways using
# list comprehensions

# Perform an operation on each item in the list

# Create a list of even values
evenList = [i*2 for i in range(10)]

for k in evenList:
    print(k, end=", ")
print()

# List of lists containing values to the power of
# 2, 3, 4
numList = [1,2,3,4,5]

listOfValues = [[math.pow(m, 2), math.pow(m, 3), math.pow(m, 4)]
                for m in numList]

for k in listOfValues:
    print(k)
print()

# Create a 10 x 10 list
multiDList = [[0] * 10 for i in range(10)]

# Change a value in the multidimensional list
multiDList[0][1] = 10

# Get the 2nd item in the 1st list
# It may help to think of it as the 2nd item in the 1st row
print(multiDList[0][1])

# Get the 2nd item in the 2nd list
print(multiDList[1][1])

# ---------- MULTIDIMENSIONAL LIST ----------

# Show how indexes work with a multidimensional list
listTable = [[0] * 10 for i in range(10)]

for i in range(10):

    for j in range(10):
        listTable[i][j] = "{} : {}".format(i, j)

for i in range(10):

    for j in range(10):
        print(listTable[i][j], end=" || ")
    print()

# ---------- PROBLEM : CREATE MULTIPLICATION TABLE ----------
# With 2 for loops fill the cells in a multidimensional
# list with a multiplication table using values 1 - 9
'''
1, 2, 3, 4, 5, 6, 7, 8, 9,
2, 4, 6, 8, 10, 12, 14, 16, 18,
3, 6, 9, 12, 15, 18, 21, 24, 27,
4, 8, 12, 16, 20, 24, 28, 32, 36,
5, 10, 15, 20, 25, 30, 35, 40, 45,
6, 12, 18, 24, 30, 36, 42, 48, 54,
7, 14, 21, 28, 35, 42, 49, 56, 63,
8, 16, 24, 32, 40, 48, 56, 64, 72,
9, 18, 27, 36, 45, 54, 63, 72, 81
'''

# Create the multidimensional list
multTable = [[0] * 10 for i in range(10)]

# This will increment for each row
for i in range(1, 10):

    # This will increment for each item in the row
    for j in range(1, 10):

        # Assign the value to the cell
        multTable[i][j] = i * j

# Output the data in the same way you assigned it
for i in range(1, 10):

    for j in range(1, 10):
        print(multTable[i][j], end=", ")

    print()
```

## #8 Reading/Writing Files

```python
# ---------- LEARN TO PROGRAM 6 ----------

import random
import math

# With lists we can refer to groups of data with 1 name

# Each item in the list corresponds to a number (index)
# just like how people have identification numbers.
# By default the 1st item in a list has the index 0

# [0 : "string"] [1 : 1.234] [2 : 28] [3 : "c"]

# Python lists can grow in size and can contain data
# of any type

randList = ["string", 1.234, 28]

# Create a list with range
oneToTen = list(range(10))

# An awesome thing about lists is that you can use many
# of the same functions with them that you used with strings

# Combine lists
randList = randList + oneToTen

# Get the 1st item with an index
print(randList[0])

# Get the length
print("List Length :", len(randList))

# Slice a list to get 1st 3 items
first3 = randList[0:3]

# Cycle through the list and print the index
for i in first3:
    print("{} : {}".format(first3.index(i), i))

# You can repeat a list item with *
print(first3[0] * 3)

# You can see if a list contains an item
print("string" in first3)

# You can get the index of a matching item
print("Index of string :", first3.index("string"))

# Find out how many times an item is in the list
print("How many strings :", first3.count("string"))

# You can change a list item
first3[0] = "New String"

for i in first3:
    print("{} : {}".format(first3.index(i), i))

# Append a value to the end of a list
first3.append("Another")

# ---------- PROBLEM : CREATE A RANDOM LIST ----------
# Generate a random list of 5 values between 1 and 9
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# ---------- SORT A LIST : BUBBLE SORT ----------
# The Bubble sort is a way to sort a list
# It works this way
# 1. An outer loop decreases in size each time
# 2. The goal is to have the largest number at the end of
#    the list when the outer loop completes 1 cycle
# 3. The inner loop starts comparing indexes at the beginning
#    of the loop
# 4. Check if list[Index] > list[Index + 1]
# 5. If so swap the index values
# 6. When the inner loop completes the largest number is at
#    the end of the list
# 7. Decrement the outer loop by 1

# Create the value that will decrement for the outer loop
# Its value is the last index in the list
i = len(numList) - 1

while i > 1:

    j = 0

    while j < i:

        # Tracks the comparison of index values
        print("\nIs {} > {}".format(numList[j], numList[j+1]))
        print()

        # If the value on the left is bigger switch values
        if numList[j] > numList[j+1]:

            print("Switch")

            temp = numList[j]
            numList[j] = numList[j + 1]
            numList[j + 1] = temp

        else:
            print("Don't Switch")

        j += 1

        # Track changes to the list
        for k in numList:
            print(k, end=", ")
        print()

    print("END OF ROUND")

    i -= 1

for k in numList:
    print(k, end=", ")
print()

# ---------- MORE LIST FUNCTIONS ----------
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# Sort a list
numList.sort()

# Reverse a list
numList.reverse()

for k in numList:
    print(k, end=", ")
print()

# Insert value at index insert(index, value)
numList.insert(5, 10)

# Delete first occurrence of value
numList.remove(10)

for k in numList:
    print(k, end=", ")
print()

# Remove item at index
numList.pop(2)

for k in numList:
    print(k, end=", ")
print()

# ---------- LIST COMPREHENSIONS ----------
# You can construct lists in interesting ways using
# list comprehensions

# Perform an operation on each item in the list

# Create a list of even values
evenList = [i*2 for i in range(10)]

for k in evenList:
    print(k, end=", ")
print()

# List of lists containing values to the power of
# 2, 3, 4
numList = [1,2,3,4,5]

listOfValues = [[math.pow(m, 2), math.pow(m, 3), math.pow(m, 4)]
                for m in numList]

for k in listOfValues:
    print(k)
print()

# Create a 10 x 10 list
multiDList = [[0] * 10 for i in range(10)]

# Change a value in the multidimensional list
multiDList[0][1] = 10

# Get the 2nd item in the 1st list
# It may help to think of it as the 2nd item in the 1st row
print(multiDList[0][1])

# Get the 2nd item in the 2nd list
print(multiDList[1][1])

# ---------- MULTIDIMENSIONAL LIST ----------

# Show how indexes work with a multidimensional list
listTable = [[0] * 10 for i in range(10)]

for i in range(10):

    for j in range(10):
        listTable[i][j] = "{} : {}".format(i, j)

for i in range(10):

    for j in range(10):
        print(listTable[i][j], end=" || ")
    print()

# ---------- PROBLEM : CREATE MULTIPLICATION TABLE ----------
# With 2 for loops fill the cells in a multidimensional
# list with a multiplication table using values 1 - 9
'''
1, 2, 3, 4, 5, 6, 7, 8, 9,
2, 4, 6, 8, 10, 12, 14, 16, 18,
3, 6, 9, 12, 15, 18, 21, 24, 27,
4, 8, 12, 16, 20, 24, 28, 32, 36,
5, 10, 15, 20, 25, 30, 35, 40, 45,
6, 12, 18, 24, 30, 36, 42, 48, 54,
7, 14, 21, 28, 35, 42, 49, 56, 63,
8, 16, 24, 32, 40, 48, 56, 64, 72,
9, 18, 27, 36, 45, 54, 63, 72, 81
'''

# Create the multidimensional list
multTable = [[0] * 10 for i in range(10)]

# This will increment for each row
for i in range(1, 10):

    # This will increment for each item in the row
    for j in range(1, 10):

        # Assign the value to the cell
        multTable[i][j] = i * j

# Output the data in the same way you assigned it
for i in range(1, 10):

    for j in range(1, 10):
        print(multTable[i][j], end=", ")

    print()
```

## #9 Object Oriented Programming

```python
# ---------- LEARN TO PROGRAM 6 ----------

import random
import math

# With lists we can refer to groups of data with 1 name

# Each item in the list corresponds to a number (index)
# just like how people have identification numbers.
# By default the 1st item in a list has the index 0

# [0 : "string"] [1 : 1.234] [2 : 28] [3 : "c"]

# Python lists can grow in size and can contain data
# of any type

randList = ["string", 1.234, 28]

# Create a list with range
oneToTen = list(range(10))

# An awesome thing about lists is that you can use many
# of the same functions with them that you used with strings

# Combine lists
randList = randList + oneToTen

# Get the 1st item with an index
print(randList[0])

# Get the length
print("List Length :", len(randList))

# Slice a list to get 1st 3 items
first3 = randList[0:3]

# Cycle through the list and print the index
for i in first3:
    print("{} : {}".format(first3.index(i), i))

# You can repeat a list item with *
print(first3[0] * 3)

# You can see if a list contains an item
print("string" in first3)

# You can get the index of a matching item
print("Index of string :", first3.index("string"))

# Find out how many times an item is in the list
print("How many strings :", first3.count("string"))

# You can change a list item
first3[0] = "New String"

for i in first3:
    print("{} : {}".format(first3.index(i), i))

# Append a value to the end of a list
first3.append("Another")

# ---------- PROBLEM : CREATE A RANDOM LIST ----------
# Generate a random list of 5 values between 1 and 9
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# ---------- SORT A LIST : BUBBLE SORT ----------
# The Bubble sort is a way to sort a list
# It works this way
# 1. An outer loop decreases in size each time
# 2. The goal is to have the largest number at the end of
#    the list when the outer loop completes 1 cycle
# 3. The inner loop starts comparing indexes at the beginning
#    of the loop
# 4. Check if list[Index] > list[Index + 1]
# 5. If so swap the index values
# 6. When the inner loop completes the largest number is at
#    the end of the list
# 7. Decrement the outer loop by 1

# Create the value that will decrement for the outer loop
# Its value is the last index in the list
i = len(numList) - 1

while i > 1:

    j = 0

    while j < i:

        # Tracks the comparison of index values
        print("\nIs {} > {}".format(numList[j], numList[j+1]))
        print()

        # If the value on the left is bigger switch values
        if numList[j] > numList[j+1]:

            print("Switch")

            temp = numList[j]
            numList[j] = numList[j + 1]
            numList[j + 1] = temp

        else:
            print("Don't Switch")

        j += 1

        # Track changes to the list
        for k in numList:
            print(k, end=", ")
        print()

    print("END OF ROUND")

    i -= 1

for k in numList:
    print(k, end=", ")
print()

# ---------- MORE LIST FUNCTIONS ----------
numList = []
for i in range(5):
    numList.append(random.randrange(1, 9))

# Sort a list
numList.sort()

# Reverse a list
numList.reverse()

for k in numList:
    print(k, end=", ")
print()

# Insert value at index insert(index, value)
numList.insert(5, 10)

# Delete first occurrence of value
numList.remove(10)

for k in numList:
    print(k, end=", ")
print()

# Remove item at index
numList.pop(2)

for k in numList:
    print(k, end=", ")
print()

# ---------- LIST COMPREHENSIONS ----------
# You can construct lists in interesting ways using
# list comprehensions

# Perform an operation on each item in the list

# Create a list of even values
evenList = [i*2 for i in range(10)]

for k in evenList:
    print(k, end=", ")
print()

# List of lists containing values to the power of
# 2, 3, 4
numList = [1,2,3,4,5]

listOfValues = [[math.pow(m, 2), math.pow(m, 3), math.pow(m, 4)]
                for m in numList]

for k in listOfValues:
    print(k)
print()

# Create a 10 x 10 list
multiDList = [[0] * 10 for i in range(10)]

# Change a value in the multidimensional list
multiDList[0][1] = 10

# Get the 2nd item in the 1st list
# It may help to think of it as the 2nd item in the 1st row
print(multiDList[0][1])

# Get the 2nd item in the 2nd list
print(multiDList[1][1])

# ---------- MULTIDIMENSIONAL LIST ----------

# Show how indexes work with a multidimensional list
listTable = [[0] * 10 for i in range(10)]

for i in range(10):

    for j in range(10):
        listTable[i][j] = "{} : {}".format(i, j)

for i in range(10):

    for j in range(10):
        print(listTable[i][j], end=" || ")
    print()

# ---------- PROBLEM : CREATE MULTIPLICATION TABLE ----------
# With 2 for loops fill the cells in a multidimensional
# list with a multiplication table using values 1 - 9
'''
1, 2, 3, 4, 5, 6, 7, 8, 9,
2, 4, 6, 8, 10, 12, 14, 16, 18,
3, 6, 9, 12, 15, 18, 21, 24, 27,
4, 8, 12, 16, 20, 24, 28, 32, 36,
5, 10, 15, 20, 25, 30, 35, 40, 45,
6, 12, 18, 24, 30, 36, 42, 48, 54,
7, 14, 21, 28, 35, 42, 49, 56, 63,
8, 16, 24, 32, 40, 48, 56, 64, 72,
9, 18, 27, 36, 45, 54, 63, 72, 81
'''

# Create the multidimensional list
multTable = [[0] * 10 for i in range(10)]

# This will increment for each row
for i in range(1, 10):

    # This will increment for each item in the row
    for j in range(1, 10):

        # Assign the value to the cell
        multTable[i][j] = i * j

# Output the data in the same way you assigned it
for i in range(1, 10):

    for j in range(1, 10):
        print(multTable[i][j], end=", ")

    print()
```

## #10 Inheritance Magic

```python
# When we create a class we can inherit all of the fields and methods
# from another class. This is called inheritance.

# The class that inherits is called the subclass and the class we
# inherit from is the super class

# This will be our super class
class Animal:

    def __init__(self, birthType="Unknown",
                 appearance="Unknown",
                 blooded="Unknown"):
        self.__birthType = birthType
        self.__appearance = appearance
        self.__blooded = blooded

    # The getter method
    @property
    def birthType(self):

        # When using getters and setters don't forget the __
        return self.__birthType

    @birthType.setter
    def birthType(self, birthType):
        self.__birthType = birthType

    @property
    def appearance(self):
        return self.__appearance

    @appearance.setter
    def appearance(self, appearance):
        self.__appearance = appearance

    @property
    def blooded(self):
        return self.__blooded

    @blooded.setter
    def blooded(self, blooded):
        self.__blooded = blooded

    # Can be used to cast our object as a string
    # type(self).__name__ returns the class name
    def __str__(self):
        return "A {} is {} it is {} it is " \
                "{}".format(type(self).__name__,
                                              self.birthType,
                                              self.appearance,
                                              self.blooded)

# Create a Mammal class that inherits from Animal
# You can inherit from multiple classes by separating
# the classes with a comma in the parentheses
class Mammal(Animal):
    def __init__(self, birthType="born alive",
                 appearance="hair or fur",
                 blooded="warm blooded",
                 nurseYoung=True):

        # Call for the super class to initialize fields
        Animal.__init__(self, birthType,
                        appearance,
                        blooded)

        self.__nurseYoung = nurseYoung

    # We can extend the subclasses
    @property
    def nurseYoung(self):
        return self.__nurseYoung

    @nurseYoung.setter
    def appearance(self, nurseYoung):
        self.__nurseYoung = nurseYoung

    # Overwrite __str__
    # You can use super() to refer to the superclass
    def __str__(self):
        return super().__str__() + " and it is {} they nurse " \
            "their young".format(self.nurseYoung)


class Reptile(Animal):
    def __init__(self, birthType="born in an egg or born alive",
                 appearance="dry scales",
                 blooded="cold blooded"):

        # Call for the super class to initialize fields
        Animal.__init__(self, birthType,
                    appearance,
                    blooded)

    # Operator overloading isn't necessary in Python because
    # Python allows you to enter unknown numbers of values
    # Always make sure self is the first attribute in your
    # class methods
    def sumAll(self, *args):
        sum = 0

        for i in args:

            sum += i

        return sum


def main():
    animal1 = Animal("born alive")

    print(animal1.birthType)

    # Call __str__()
    print(animal1)
    print()

    mammal1 = Mammal()

    print(mammal1)

    print(mammal1.birthType)
    print(mammal1.appearance)
    print(mammal1.blooded)
    print(mammal1.nurseYoung)
    print()

    reptile1 = Reptile()

    print(reptile1.birthType)
    print(reptile1.appearance)
    print(reptile1.blooded)
    print()

    # Operator overloading in Python
    print("Sum : {}".format(reptile1.sumAll(1,2,3,4,5)))

    # Polymorphism in Python works differently from other
    # languages in that functions accept any object
    # and expect that object to provide the needed method

    # This isn't something to dwell on. Just know that
    # if you call on a method for an object that the
    # method just needs to exist for that object to work.
    # Polymorphism is a big deal in other languages that
    # are statically typed (type is defined at declaration)
    # but because Python is dynamically typed (type defined
    # when a value is assigned) it doesn't matter as much.

    def getBirthType(theObject):
        print("The {} is {}".format(type(theObject).__name__,
                                theObject.birthType))

    getBirthType(mammal1)
    getBirthType(reptile1)



main()

# ---------- MAGIC METHODS ----------
# Magic methods are surrounded by double underscores
# We can use magic methods to define how operators
# like +, -, *, /, ==, >, <, etc. will work with our
# custom objects

# Magic methods are used for operator overloading
# in Python

# __eq__ : Equal
# __ne__ : Not Equal
# __lt__ : Less Than
# __gt__ : Greater Than
# __le__ : Less Than or Equal
# __ge__ : Greater Than or Equal
# __add__ : Addition
# __sub__ : Subtraction
# __mul__ : Multiplication
# __div__ : Division
# __mod__ : Modulus

class Time:
    def __init__(self, hour=0, minute=0, second=0):
        self.hour = hour
        self.minute = minute
        self.second = second

    # Magic method that defines the string format of the object
    def __str__(self):

        # :02d adds a leading zero to have a minimum of 2 digits
        return "{}:{:02d}:{:02d}".format(self.hour,self.minute, self.second)

    def __add__(self, other_time):

        new_time = Time()

        # ---------- PROBLEM ----------
        # How would you go about adding 2 times together?
    
        # Add the seconds and correct if sum is >= 60
        if (self.second + other_time.second) >= 60:
            self.minute += 1
            new_time.second = (self.second + other_time.second) - 60
        else:
            new_time.second = self.second + other_time.second

        # Add the minutes and correct if sum is >= 60
        if (self.minute + other_time.minute) >= 60:
            self.hour += 1
            new_time.minute = (self.minute + other_time.minute) - 60
        else:
            new_time.minute = self.minute + other_time.minute

        # Add the minutes and correct if sum is > 60

        if (self.hour + other_time.hour) > 24:
            new_time.hour = (self.hour + other_time.hour) - 24
        else:
            new_time.hour = self.hour + other_time.hour

        return new_time


def main():
    time1 = Time(1, 20, 30)

    print(time1)

    time2 = Time(24, 41, 30)

    print(time1 + time2)

    # For homework get the Time objects to work for the other
    # mathematical and comparison operators



main()
```

## #11 Static & Exception Handling

```python
# ---------- STATIC METHODS ----------

# Static methods allow access without the need to initialize
# a class. They should be used as utility methods, or when
# a method is needed, but it doesn't make sense for the real
# world object to be able to perform a task

class Sum:

    # You use the static method decorator to define that a
    # method is static
    @staticmethod
    def getSum(*args):

        sum = 0

        for i in args:
            sum += i

        return sum

def main():

    # Call a static method by proceeding it with its class
    # name
    print("Sum :", Sum.getSum(1,2,3,4,5))


main()


# ---------- STATIC VARIABLES ----------
# Fields declared in a class, but outside of any method
# are static variables. There value is shared by every
# object of that class

class Dog:

    # This is a static variable
    num_of_dogs = 0

    def __init__(self, name="Unknown"):
        self.name = name

        # You reference the static variable by proceeding
        # it with the class name
        Dog.num_of_dogs += 1

    @staticmethod
    def getNumOfDogs():
        print("There are currently {} dogs".format(Dog.num_of_dogs))

def main():

    spot = Dog("Spot")

    doug = Dog("Doug")

    spot.getNumOfDogs()


main()

# ---------- MODULES ----------
# Your Python programs will contain a main program that
# includes your main function. Then you will create many
# modules in separate files. Modules also end with .py
# just like any other Python file

# ————— sum.py —————
def getSum(*args):
    sum = 0

    for i in args:
        sum += i

    return sum

# ————— End of sum.py —————

# You can import by listing the file name minus the py
import sum

# Get access to functions by proceeding with the file
# name and then the function you want
print("Sum :", sum.getSum(1,2,3,4,5))

# ---------- FROM ----------

# You can use from to copy specific functions from a module
# You can use from sum import * to import all functions
# You can import multiple functions by listing them after
# import separated by commas
from sum import getSum

# You don't have to reference the module name now
print("Sum :", getSum(1,2,3,4,5))


# ---------- EXCEPTION HANDLING ----------
# Exceptions are triggered either when an error occurs
# or when you want them to.

# We use exceptions are used to handle errors, execute
# specific code when code generates something out of
# the ordinary, to always execute code when something
# happens (close a file that was opened),

# When an error occurs you stop executing code and jump
# to execute other code that responds to that error

# Let's handle an IndexError exception that is
# triggered when you try to access an index in a list
# that doesn't exist

# Surround a potential exception with try
try:
    aList = [1,2,3]

    print(aList[3])

# Catch the exception with except followed by the
# exception you want to catch

# You can catch multiple exceptions by separating them
# with commas inside parentheses
# except (IndexError, NameError):
except IndexError:
    print("Sorry that index doesn't exist")

# If the exception wasn't caught above this will
# catch all others
except:
    print("An unknown error occurred")

# ---------- CUSTOM EXCEPTIONS ----------

# Lets trigger an exception if the user enters a
# name that contains a number

# Although you won't commonly create your own exceptions
# this is how you do it

# Create a class that inherits from Exception
class DogNameError(Exception):

    def __init__(self, *args, **kwargs):
        Exception.__init__(self, *args, **kwargs)

try:
    dogName = input("What is your dogs name : ")

    if any(char.isdigit() for char in dogName):

        # Raise your own exception
        # You can raise the built in exceptions as well
        raise DogNameError

except DogNameError:
    print("Your dogs name can't contain a number")

# ---------- FINALLY & ELSE ----------
# finally is used when you always want certain code to
# execute whether an exception is raised or not

num1, num2 = input("Enter to values to divide : ").split()

try:
    quotient = int(num1) / int(num2)
    print("{} / {} = {}".format(num1, num2, quotient))

except ZeroDivisionError:
    print("You can't divide by zero")

# else is only executed if no exception was raised
else:
    print("You didn't raise an exception")

finally:
    print("I execute no matter what")

# ---------- PROBLEM EXCEPTIONS & FILES ----------
# 1. Create a file named mydata2.txt and put data in it
# 2. Using what you learned in part 8 and Google to find
# out how to open a file without with try to open the
# file in a try block
# 3. Catch the FileNotFoundError exception
# 4. In else print the file contents
# 5. In finally close the file
# 6. Try to open the nonexistent file mydata3.txt and
# test to see if you caught the exception

try:
    myFile = open("mydata2.txt", encoding="utf-8")

# We can use as to access data and methods in the
# exception class
except FileNotFoundError as ex:
    print("That file was not found")

    # Print out further data on the exception
    print(ex.args)

else:
    print("File :", myFile.read())
    myFile.close()

finally:
    print("Finished Working with File")
```

## #12 Lambda, Map Filter Reduce

```python
# ---------- ADVANCED FUNCTIONS ----------

# ---------- FUNCTIONS AS OBJECTS ----------

def mult_by_2(num):
    return num * 2

# A function can be
# 1. Assigned to another name

times_two = mult_by_2

print("4 * 2 =", times_two(4))

# 2. Passed into other functions

def do_math(func, num):

    return func(num)

print("8 * 2 =", do_math(mult_by_2, 8))

# 3. Returned from a function

def get_func_mult_by_num(num):

    # Create a dynamic function that will receive a value
    # and then return that value times the value passed
    # into getFuncMultByNum()
    def mult_by(value):
        return num * value

    return mult_by

generated_func = get_func_mult_by_num(5)

print("5 * 10 =", generated_func(10))

# 4. Embedded in a data structure

listOfFuncs = [times_two, generated_func]

print("5 * 9 =", listOfFuncs[1](9))

# ---------- PROBLEM ----------
# Create a function that receives a list and a function
# The function passed will return True or False if a list
# value is odd.
# The surrounding function will return a list of odd
# numbers

def is_it_odd(num):
    if num % 2 == 0:
        return False
    else:
        return True

def change_list(list, func):

    oddList = []

    for i in list:
        if func(i):
            oddList.append(i)

    return oddList

aList = range(1, 21)

print(change_list(aList, is_it_odd))


# ---------- FUNCTION ANNOTATIONS ----------
# It is possible to define the data types of attributes
# and the returned value with annotations, but they have
# no impact on how the function operates, but instead
# are for documentation

def random_func(name: str, age: int, weight: float) -> str:
    print("Name :", name)
    print("Age :", age)
    print("Weight :", weight)

    return "{} is {} years old and weighs {}".format(name, age, weight)

print(random_func("Derek", 41, 165.5))

# You don't get an error if you pass bad data
print(random_func(89, "Derek", "Turtle"))

# You can print the annotations
print(random_func.__annotations__)

# ---------- ANONYMOUS FUNCTIONS : LAMBDA ----------
# lambda is like def, but rather then assign the function
# to a name it just returns it. Because there is no name
# that is why they are called anonymous functions. You
# can however assign a lambda function to a name.

# This is their format
# lambda arg1, arg2,... : expression using the args

# lambdas are used when you need a small function, but
# don't want to junk up your code with temporary
# function names that may cause conflicts

# Add values
sum = lambda x, y : x + y

print("Sum :", sum(4, 5))

# Use a ternary operator to see if someone can vote
can_vote = lambda age: True if age >= 18 else False

print("Can Vote :", can_vote(16))

# Create a list of functions
powerList = [lambda x: x ** 2,
             lambda x: x ** 3,
             lambda x: x ** 4]

# Run each function on a value
for func in powerList:
    print(func(4))


# You can also store lambdas in dictionaires

attack = {'quick': (lambda: print("Quick Attack")),
           'power': (lambda: print("Power Attack")),
           'miss': (lambda: print("The Attack Missed"))}

attack['quick']()

# You could get a random dictionary as well for say our
# previous warrior objects
import random

# keys() returns an iterable so we convert it into a list
# choice() picks a random value from that list
attackKey = random.choice(list(attack.keys()))

attack[attackKey]()

# ---------- PROBLEM ----------
# Create a random list filled with the characters H and T
# for heads and tails. Output the number of Hs and Ts
# Example Output
# Heads :  46
# Tails :  54

# Create the list
flipList = []

# Populate the list with 100 Hs and Ts
# Trick : random.choice() returns a random value from the list
for i in range(1, 101):
    flipList += random.choice(['H', 'T'])

# Output results
print("Heads : ", flipList.count('H'))
print("Tails : ", flipList.count('T'))


# ---------- MAP ----------
# Map allows us to execute a function on each item in a list

# Generate a list from 1 to 10
oneTo10 = range(1, 11)

# The function to pass into map
def dbl_num(num):
    return num * 2

# Pass in the function and the list to generate a new list
print(list(map(dbl_num, oneTo10)))

# You could do the same thing with a lambda
print(list(map((lambda x: x * 3), oneTo10)))

# You can perform calculations against multiple lists
aList = list(map((lambda x, y: x + y), [1, 2, 3], [1, 2, 3]))
print(aList)

# ---------- FILTER ----------
# Filter selects items from a list based on a function

# Print out the even values from a list
print(list(filter((lambda x: x % 2 == 0), range(1, 11))))

# ---------- PROBLEM ----------
# Find the multiples of 9 from a random 100 value list with
# values between 1 and 1000

# Generate a random list with randint between 1 and 1000
# Use range to generate 100 values
randList = list(random.randint(1, 1001) for i in range(100))

# Use modulus to find multiples of 9 by passing the random
# list to filter
print(list(filter((lambda x: x % 9 == 0), randList)))


# ---------- REDUCE ----------
# Reduce receives a list and returns a single result

# You must import reduce
from functools import reduce

# Add up the values in a list
print(reduce((lambda x, y: x + y), range(1, 6)))
```

## #13 List Comprehensions & Generators

```python
# ---------- ITERABLES ----------
# An iterable is a stored sequence of values (list) or,
# as we will see when we cover generators, an
# object that produces one value at a time

# Iterables differ from iterators in that an iterable
# is an object with an __iter__ method which returns
# an iterator. An iterator is an object with a
# __next__ method which retrieves the next value from
# sequence of values

# Define a string and convert it into an iterator
sampStr = iter("Sample")

print("Char :", next(sampStr))
print("Char :", next(sampStr))

# You can add iterator behavior to your classes
class Alphabet:

    def __init__(self):
        self.letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        self.index = -1

    def __iter__(self):
        return self

    def __next__(self):
        if self.index >= len(self.letters) - 1:
            raise StopIteration
        self.index += 1
        return self.letters[self.index]

alpha = Alphabet()

for letter in alpha:
    print(letter)

# Iterate through a dictionary because it is an iterable
derek = {"fName": "Derek", "lName": "Banas"}

for key in derek:
    print(key, derek[key])

# ---------- PROBLEM ----------
# Create a class that returns values from the Fibonacci
# sequence each time next is called
# Sample Output
# Fib : 1
# Fib : 2
# Fib : 3
# Fib : 5

class FibGenerator:

    def __init__(self):
        self.first = 0
        self.second = 1

    def __iter__(self):
        return self

    def __next__(self):
        fibNum = self.first + self.second
        self.first = self.second
        self.second = fibNum
        return fibNum

fibSeq = FibGenerator()

for i in range(10):
    print("Fib :", next(fibSeq))

# ---------- LIST COMPREHENSIONS ----------
# A list comprehension executes an expression against an iterable

# Note: While they are super powerful, try not to make list
# comprehensions that are hard to figure out for others

# To multiply 2 times every value with a map we'd do
print(list(map((lambda x: x * 2), range(1, 11))))

# With a list comprehension we'd do
# Note that a list comprehension is surrounded by []
# because it returns a list
print([2 * x for x in range(1, 11)])

# To construct a list of odds using filter we'd
print(list(filter((lambda x: x % 2 != 0), range(1, 11))))

# To do the same with a list comprehension
print([x for x in range(1, 11) if x % 2 != 0])

# A list comprehension can act as map and filter
# on one line
# Generate a list of 50 values and take them to the power
# of 2 and return all that are multiples of 8

print([i ** 2 for i in range(50) if i % 8 == 0])

# You can have multiple for loops as well
# Multiply all values in one list times all values in
# another
print([x * y for x in range(1, 3) for y in range(11, 16)])

# You can put list comprehensions in list comprehensions
# Generate a list of 10 values, multiply them by 2 and
# return multiples of 8
print([x for x in [i * 2 for i in range(10)] if x % 8 == 0])

# ---------- PROBLEM ----------
# Generate a list of 50 random values between 1 and 1000
# and return those that are multiples of 9
# You'll have to use a list comprehension in a list comprehension
# This is a hard one!

import random

print([x for x in [random.randint(1, 1001) for i in range(50)] if x % 9 == 0])

# List comprehensions also make it easy to work with
# multidimensional lists

multiList = [[1, 2, 3],
             [4, 5, 6],
             [7, 8, 9]]

print([col[1] for col in multiList])

# Get the diagonal by incrementing 0, 0 -> 1, 1 -> 2, 2
print([multiList[i][i] for i in range(len(multiList))])

# ---------- GENERATOR FUNCTIONS ----------
# A generator function returns a result generator when called
# They can be suspended and resumed during execution of
# your program to create results over time rather then
# all at once

# We use generators when we want to big result set, but
# we don't want to slow down the program by creating
# it all at one time

# Create a generator that calculates primes and returns
# the next prime on command

def isprime(num):
    # This for loop cycles through primes from 2 to
    # the value to check
    for i in range(2, num):

        # If any division has no remainder we know it
        # isn't a prime number
        if (num % i) == 0:
            return False
    return True

# This is the generator
def gen_primes(max_number):

    # This for loop cycles through primes from 2 to
    # the maximum value requested
    for num1 in range(2, max_number):

        if isprime(num1):

            # yield is what makes this a generator
            # When called by next it will return the
            # next result
            yield num1

# Create a reference to the generator
prime = gen_primes(50)

# Call next for each result
print("Prime :", next(prime))
print("Prime :", next(prime))
print("Prime :", next(prime))

# ---------- GENERATOR EXPRESSIONS ----------
# Generator expressions look just like list comprehensions
# but they return results one at a time
# The are surrounded by parentheses instead of [ ]

double = (x * 2 for x in range(10))

print("Double :", next(double))
print("Double :", next(double))

# You can iterate through all results as well
for num in double:
    print(num)
```

## #14 Threads

```python
# When you use threads it is like you are running
# multiple programs at once.

# Threads actually take turns executing. While one
# executes the other sleeps until it is its turn
# to execute.

import threading
import time
import random

def executeThread(i):

    # strftime or string formatted time allows you to
    # define how the time is displayed.
    # You could include the date with
    # strftime("%Y-%m-%d %H:%M:%S", gmtime())

    # Print when the thread went to sleep
    print("Thread {} sleeps at {}".format(i,
                    time.strftime("%H:%M:%S", time.gmtime())))

    # Generate a random sleep period of between 1 and
    # 5 seconds
    randSleepTime = random.randint(1, 5)

    # Pauses execution of code in this function for
    # a few seconds
    time.sleep(randSleepTime)

    # Print out info after the sleep time
    print("Thread {} stops sleeping at {}".format(i,
                    time.strftime("%H:%M:%S", time.gmtime())))

for i in range(10):

    # Each time through the loop a Thread object is created
    # You pass it the function to execute and any
    # arguments to pass to that method
    # The arguments passed must be a sequence which
    # is why we need the comma with 1 argument
    thread = threading.Thread(target=executeThread, args=(i,))
    thread.start()

    # Display active threads
    # The extra 1 is this for loop executing in the main
    # thread
    print("Active Threads :", threading.activeCount())

    # Returns a list of all active thread objects
    print("Thread Objects :", threading.enumerate())


# ---------- SUBCLASSING THREAD ----------
# You can subclass the Thread object and then define
# what happens each time a new thread is executed
# or run

class CustThread(threading.Thread):

    def __init__(self, name):
        threading.Thread.__init__(self)

        self.name = name

    def run(self):

        getTime(self.name)

        print("Thread", self.name, "Execution Ends")

def getTime(name):
    print("Thread {} sleeps at {}".format(name,
                    time.strftime("%H:%M:%S", time.gmtime())))

    randSleepTime = random.randint(1, 5)

    time.sleep(randSleepTime)

# Create thread objects
thread1 = CustThread("1")
thread2 = CustThread("2")

# Start thread execution of run()
thread1.start()
thread2.start()

# Check if thread is alive
print("Thread 1 Alive :", thread1.is_alive())
print("Thread 2 Alive :", thread2.is_alive())

# Get thread name
# You can change it with setName()
print("Thread 1 Name :", thread1.getName())
print("Thread 2 Name :", thread2.getName())

# Wait for threads to exit
thread1.join()
thread2.join()

print("Execution Ends")


# ---------- SYNCHRONIZING THREADS ----------
# You can lock other threads from executing

# If we try to model a bank account we have to make sure
# the account is locked down during a transaction so
# that if more then 1 person tries to withdrawal money at
# once we don't give out more money then is in the account

class BankAccount (threading.Thread):

    acctBalance = 100

    def __init__(self, name, moneyRequest):
        threading.Thread.__init__(self)
        self.name = name
        self.moneyRequest = moneyRequest

    def run(self):
        # Get lock to keep other threads from accessing the account
        threadLock.acquire()

        # Call the static method
        BankAccount.getMoney(self)

        # Release lock so other thread can access the account
        threadLock.release()

    @staticmethod
    def getMoney(customer):
        print("{} tries to withdrawal ${} at {}".format(customer.name,
                customer.moneyRequest,
                time.strftime("%H:%M:%S", time.gmtime())))

        if BankAccount.acctBalance - customer.moneyRequest > 0:
            BankAccount.acctBalance -= customer.moneyRequest
            print("New account balance is : ${}".format(BankAccount.acctBalance))
        else:
            print("Not enough money in the account")
            print("Current balance : ${}".format(BankAccount.acctBalance))

        time.sleep(3)

# Create a lock to be used by threads
threadLock = threading.Lock()

# Create new threads
doug = BankAccount("Doug", 1)
paul = BankAccount("Paul", 100)
sally = BankAccount("Sally", 50)

# Start new Threads
doug.start()
paul.start()
sally.start()

# Have threads wait for previous threads to terminate
doug.join()
paul.join()
sally.join()

print("Execution Ends")
```

