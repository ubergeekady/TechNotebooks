---
typora-copy-images-to: ../../../Desktop/screen1.png
---

## **Comments**

```c
/* This is a multi-line comment
   Always comment as you write code */
 
// Single line comment
```



## Constants

You define constants with define tells the compiler to replace MYNAME with what is provided

```c
#define MYNAME "Aditya Singh"
```



## Variables

Variables are boxes in memory that save important data. A variable name must start with a letter, but then can contain numbers, letters or underscores

**Char**

A char can hold any of 256 single characters. All characters are surrounded by apostrophes ' If you save a number as a char it can't be used for calculating

```c
char firstLetter = 'D';
```

**Integer**

An int can contain any whole number positive or negative between -32,768 and 32,767

```c
int age = 38;
```

**Long Integer**

Use a long int if you need to use a number larger or smaller then is provided by an int

```c
long int superBigNum = -32767000;
```

**Float**

A float is a number with a decimal positive or negative

```c
float piValue = 3.14159265359;
```

**Double**

A double is used when you need a number bigger then float

```c
double reallyBigPi = 3.1415926535897932384626433832795028841971;
```

C99 has bool. Earlier version had only 0/1.

**Enumerated Types** : Enumeration (or enum) is a user defined data type in C. It is mainly used to assign names to integral constants, the names make a program easy to read and maintain.

```c
enum State {Working = 1, Failed = 0}; 

// The name of enumeration is "flag" and the constant
// are the values of the flag. By default, the values
// of the constants are as follows:
// constant1 = 0, constant2 = 1, constant3 = 2 and 
// so on.
enum flag{constant1, constant2, constant3, ....... };



// In both of the below cases, "day" is 
// defined as the variable of type week. 

enum week{Mon, Tue, Wed};
enum week day;

// Or

enum week{Mon, Tue, Wed}day;


-------------------
  
  // An example program to demonstrate working 
// of enum in C 
#include<stdio.h> 
  
enum week{Mon, Tue, Wed, Thur, Fri, Sat, Sun}; 
  
int main() 
{ 
    enum week day; 
    day = Wed; 
    printf("%d",day); 
    return 0; 
}

//Output - 2



-------------
  
// Another example program to demonstrate working 
// of enum in C 
#include<stdio.h> 
  
enum year{Jan, Feb, Mar, Apr, May, Jun, Jul,  
          Aug, Sep, Oct, Nov, Dec}; 
  
int main() 
{ 
   int i; 
   for (i=Jan; i<=Dec; i++)       
      printf("%d ", i); 
        
   return 0; 
}

// Output -> 0 1 2 3 4 5 6 7 8 9 10 11

-------------------


```

**Interesting facts about initialization of enum.**

**1.** Two enum names can have same value. For example, in the following C program both ‘Failed’ and ‘Freezed’ have same value 0.

```c
#include <stdio.h> 
enum State {Working = 1, Failed = 0, Freezed = 0}; 
  
int main() 
{ 
   printf("%d, %d, %d", Working, Failed, Freezed); 
   return 0; 
}

//1,0,0
```

**2.** If we do not explicitly assign values to enum names, the compiler by default assigns values starting from 0. For example, in the following C program, sunday gets value 0, monday gets 1, and so on.

```c
#include <stdio.h> 
enum day {sunday, monday, tuesday, wednesday, thursday, friday, saturday}; 
  
int main() 
{ 
    enum day d = thursday; 
    printf("The day number stored in d is %d", d); 
    return 0; 
} 

//The day number stored in d is 4
```

**3.** We can assign values to some name in any order. All unassigned names get value as value of previous name plus one.

```c
#include <stdio.h> 
enum day {sunday = 1, monday, tuesday = 5, 
          wednesday, thursday = 10, friday, saturday}; 
  
int main() 
{ 
    printf("%d %d %d %d %d %d %d", sunday, monday, tuesday, 
            wednesday, thursday, friday, saturday); 
    return 0; 
}

//1 2 5 6 10 11 12
```

**4.** The value assigned to enum names must be some integeral constant, i.e., the value must be in range from minimum possible integer value to maximum possible integer value.

**5.** All enum constants must be unique in their scope. For example, the following program fails in compilation.

```c
enum state  {working, failed}; 
enum result {failed, passed}; 
  
int main()  { return 0; } 
```

```
Compile Error: 'failed' has a previous declaration as 'state failed'
```



**String**

To create a String you instead create char arrays Every char array has a \0 String Terminator as the last character, so always make your char arrays at least 1 character longer then you need

```c
char myName[13] = "Aditya Singh";
//OR
char myName[] = "Aditya Singh";
```

![screen1](screen1.png)

 			 				 					

Here are some declarations for variables of these types: 

```c
short shoe_size;
int house_number;
long long star_count;
```

Some kinds of data are always positive, the number of pebbles on a beach for example. In such cases you don’t need to provide for negative values. For each type that stores signed integers, there is a corresponding type that stores unsigned integers, and the unsigned type occupies the same amount of memory as the signed type. Each unsigned type name is essentially the signed type name prefixed with the keyword unsigned.   	

![screen2](screen2.png)			 			 		

With a given number of bits, the number of different values that can be represented is fixed. A 32-bit integer variable can represent any of 4,294,967,296 different values. Thus, using an unsigned type doesn’t provide more values than the corresponding signed type, but it does allow numbers to be represented that are twice the magnitude. 

```c
unsigned int count;
unsigned long population;		
```

To declare and initialize the variable Big_Number, you could write this:

```
long Big_Number = 1287600L;
```

![screen3](screen3.png)

![screen4](screen4.png)

Of course, it may be important to be able to determine within a program exactly what the limits are on the values that can be stored by a given integer type. As I mentioned earlier, the limits.h header file defines symbols that represent values for the limits for each type.

```c
#include <stdio.h>
#include <limits.h>
#include <float.h>

int main(){
	printf("Variables of type char store values from %d to %d\n", CHAR_MIN, CHAR_MAX); 
	printf("Variables of type unsigned char store values from 0 to %u\n", UCHAR_MAX); 
	printf("Variables of type short store values from %d to %d\n", SHRT_MIN, SHRT_MAX); 
	printf("Variables of type unsigned short store values from 0 to %u\n", USHRT_MAX); 
	printf("Variables of type int store values from %d to %d\n", INT_MIN, INT_MAX); 
	printf("Variables of type unsigned int store values from 0 to %u\n", UINT_MAX); 
	printf("Variables of type long store values from %ld to %ld\n", LONG_MIN, LONG_MAX); 
	printf("Variables of type unsigned long store values from 0 to %lu\n", ULONG_MAX); 
	printf("Variables of type long long store values from %lld to %lld\n", LLONG_MIN, LLONG_MAX); 
	printf("Variables of type unsigned long long store values from 0 to %llu\n\n", ULLONG_MAX);
	printf("The size of the smallest positive non-zero value of type float is %.3e\n", FLT_MIN);
	printf("The size of the largest value of type float is %.3e\n", FLT_MAX);
	printf("The size of the smallest non-zero value of type double is %.3e\n", DBL_MIN);
	printf("The size of the largest value of type double is %.3e\n", DBL_MAX);
	printf("The size of the smallest non-zero value of type long double is %.3Le\n", LDBL_MIN);
	printf("The size of the largest value of type long double is %.3Le\n\n",  LDBL_MAX);
	printf("Variables of type float provide %u decimal digits precision. \n", FLT_DIG);
	printf("Variables of type double provide %u decimal digits precision. \n", DBL_DIG);
	printf("Variables of type long double provide %u decimal digits precision. \n", LDBL_DIG);
}
```

```
Variables of type char store values from -128 to 127
Variables of type unsigned char store values from 0 to 255
Variables of type short store values from -32768 to 32767
Variables of type unsigned short store values from 0 to 65535
Variables of type int store values from -2147483648 to 2147483647
Variables of type unsigned int store values from 0 to 4294967295
Variables of type long store values from -9223372036854775808 to 9223372036854775807
Variables of type unsigned long store values from 0 to 18446744073709551615
Variables of type long long store values from -9223372036854775808 to 9223372036854775807
Variables of type unsigned long long store values from 0 to 18446744073709551615

The size of the smallest positive non-zero value of type float is 1.175e-38
The size of the largest value of type float is 3.403e+38
The size of the smallest non-zero value of type double is 2.225e-308
The size of the largest value of type double is 1.798e+308
The size of the smallest non-zero value of type long double is 3.362e-4932
The size of the largest value of type long double is 1.190e+4932

Variables of type float provide 6 decimal digits precision. 
Variables of type double provide 15 decimal digits precision. 
Variables of type long double provide 18 decimal digits precision. 
```

 			 		

## Console Input/Output

Most all C function names contain no uppercase letters. 

printf() prints to screen the string inside of quotes

```c
printf("Hello World \n");
```

\n tells the screen to skip to the next line
Escape Sequences: \t - tab, \\ - backslash, \" - Quote

%d is a conversion character that inserts an int into your output

```c
printf("I am %d years old\n\n", age);
```

%ld is a conversion character for long ints

```c
printf("Big Number %ld\n\n", superBigNum);
```

%f is a conversion character for floats and doubles. You can define the number of decimal places as well. Size goes from -3.4 * 10^38 to 3.4 * 10^38

```c
printf("Pi = %.5f\n\n", piValue);
```

%c is the conversion character for chars

```c
printf("The first letter of my name is %c\n\n", firstLetter);
```

%s is used for strings

```c
printf("My name is %s\n\n", "Aditya");
printf("My name is %s\n\n", myName);
```

You can't assign a new value to a char array you would use strcpy for that

```c
strcpy(myName, "Bob Smith");
```

scanf() is used to get input from the user. You must use the & ampersand before the variable unless you're using %s

```c
char middleInitial;
printf("What is your middle initial? ");
scanf(" %c", &middleInitial);
```

You can only except more then one value if you define exactly what you expect to get

```c
char firstName[30], lastName[30];
printf("What is your name? ");
scanf("%s %s", firstName, lastName);
printf("Your name is %s %c %s\n\n", firstName, middleInitial, lastName);
```

You can also except a / if you know the user will enter it

```c
int month, day, year;
printf("Whats your birth date? ");
scanf("%d/%d/%d", &month, &day, &year);
printf("Birth Date %d/%d/%d\n\n", month, day, year);
```



## Math & Logic Operations

+, -, *, /, and sometimes % (% only with ints)

```c
int num1 = 12, num2 = 15, numAns;
float decimal1 = 1.2, decimal2 = 1.5, decimalAns;
printf("Integer Calculation %d\n\n", num2 / num1);
printf("Float Calculation %f\n\n", decimal2 / decimal1);
printf("Modulus %d\n\n", num2 % num1);

printf("Without Parentheses %d\n\n", 3 + 6 * 10);  //63
printf("With Parentheses %d\n\n", (3 + 6) * 10);  //90
```

There are shortcut ways to perform calculations : +=, -=, *=, /=, %=, ++, --

```c
int randomNum = 1;
printf("1 += 2 : %d\n\n", randomNum, randomNum += 2);
//C will first compute the value and then put it there.
```

++ and -- work differently depending on where they are

```c
int exNum = 1;
printf("++%d : %d\n\n", exNum, ++exNum);
exNum = 1;
printf("%d++ : %d\n\n", exNum, exNum++);
```

If you ever need to cast one data type to another just put (dataType) before it to cast

```c
int numberEx = 12;
float numberEx2 = 1.234;
int numberEx3 = numberEx / numberEx2;
printf("numberEx / numberEx2 : %f\n\n", (float) numberEx3);
```

There are many ways to compare data in c  - >, <, ==, >=, <=, !=

Only compare values with the same data type. To compare 2 unlike types perform a cast. A relational operator always evaluates to 1 for true, or 0 for false.

```c
printf("\n");
int num1 = 1, num2 = 2;
printf("Is 1 > 2 : %d\n\n",num1 > num2);
```

If is used to compare values and perform different actions depending on those comparisons. You can check multiple conditions with else if and you can define a default with else. Once one condition is true the code in between the curly brackets that follows is executed and then no other condition that follows is checked.

```c
if (num1 > num2) {
		printf("%d is greater then %d\n\n", num1, num2);
} else if(num1 < num2) {
		printf("%d is less then %d\n\n", num1, num2);
} else {
		printf("%d is equal to %d\n\n", num1, num2);
}
```

Logical operators are used to combine the above relational operators. && - And, || - Or, ! - Not

Relational operators check how values relate

```c
int custAge = 38;
if(custAge > 21 && custAge < 35) printf("They are welcome\n\n");
else printf("They are not welcome\n\n");
```

! - Not turns a 1 to 0 and vice versa

Surround relations with parentheses when using not

This won't work !custAge > 21

```c
printf("! turns a true into false : %d\n\n", !1);
```

```c
//Bob deserves a raise if he has missed less then 10 days work and has over 30000 in sales or //has signed up 30 new customers
int bobMissedDays = 8, bobTotalSales = 24000, bobNewCust = 32;
if (bobMissedDays < 10 && bobTotalSales > 30000 || bobNewCust > 30) {
		printf("Bob gets a raise\n\n");
} else {
		printf("Bob doesn't get a raise\n\n");
}
```

The Conditional Operator is great for replacing simple if statements

(comparison) ? happensIfTrue : happensIfFalse;

```c
char* legalAge = (custAge > 21) ? "true" : "false";
printf("Is the customer of legal age? %s\n\n", legalAge);
```

You can change printf with a conditional operator directly

```c
int numOfProducts = 10;
printf("I bought %s products\n\n",(numOfProducts > 1) ? "many" : "one");
```

```c
// How much space are data types taking up?
#include <stdio.h>

int main(void){
     printf("Variables of type char occupy %u bytes\n", sizeof(char));
     printf("Variables of type short occupy %u bytes\n", sizeof(short));
     printf("Variables of type int occupy %u bytes\n", sizeof(int));
     printf("Variables of type long occupy %u bytes\n", sizeof(long));
     printf("Variables of type long long occupy %u bytes\n", sizeof(long long));
     printf("Variables of type float occupy %u bytes\n", sizeof(float));
     printf("Variables of type double occupy %u bytes\n", sizeof(double));
     printf("Variables of type long double occupy %u bytes\n", sizeof(long double));
     return 0;
}
```

```c
Variables of type char occupy 1 bytes
Variables of type short occupy 2 bytes
Variables of type int occupy 4 bytes
Variables of type long occupy 8 bytes
Variables of type long long occupy 8 bytes
Variables of type float occupy 4 bytes
Variables of type double occupy 8 bytes
Variables of type long double occupy 16 bytes
```



## Type Casting

```c
//Explicit type casting
#include <stdio.h>

int main(void){
	int a=1;
	int b=2;
	printf("%f\n",(float)a/b);
}
```





## Bit, Byte etc.

```To write more about this```

What is a byte, bit, etc ? A Bit is short for Binary Digit and can be either a 1 or 0. A Byte is generally considered to be 8 Bits

```c
int bigInt = 2147483648;
printf("I'm bigger then you may have heard %d\n\n", bigInt);
```



## Looping

```
while(condition){
  //execute
}

for ( init; condition; increment ) {
   statement(s);
}

do {
   statement(s);
} while( condition );
```



## Switch Case

```
switch (n)
{
    case 1: // code to be executed if n = 1;
        break;
    case 2: // code to be executed if n = 2;
        break;
    default: // code to be executed if n doesn't match any cases
}
```



## Arrays

We have already taken a look at arrays when we stored strings in a character array. An int array is the same type of thing, and array that stores ints. An array can only store elements of the same data type

```c
char wholeName[12] = "Derek Banas";
```

You can also define an array one element at a time. If you don’t initialize an array at all, its elements, like uninitialized ordinary variables, get garbage values, but if you partially initialize an array, the remaining elements are set to 0.  				 			 		

```c
int primeNums[3] = {2, 3, 5,};
```

You don't need to define the size if you define the values up front

```c
int morePrimes[] = {13, 17, 19, 23};
```

If during initialization the number of initializers is less than the size of array then, all the remaining elements of array are assigned value zero.

2-D arrays can be initialized in a way similar to that of I-D arrays.

```c
int matrix[3][2] = {2,3,4,5,6,7}
//OR
int matrix[3][2] = {{2,3},{4,5},{6,7}} //Row-wise grouping

//matrix[0][0]:2 matrix[0][1]:3
//matrix[1][0]:4 matrix[1][1]:5
//matrix[2][0]:6 matrix[2][1]:7	
```

Like most other languages the first number in an array is put in the zero index

```c
printf("The first prime in the list is %d\n\n", primeNums[0]);
```

A character array can be created the same way

```c
char city[7] = {'C', 'h', 'i', 'c', 'a', 'g', 'o'};
```

If I want to print the character array as a string though I have to add \0 at the end

```c
char anotherCity[5] = {'E', 't', 'n', 'a', '\0'};
printf("A City %s\n\n", anotherCity);
```

Creating the string like before is easier. No quotes and an automatic null at the end

```c
char thirdCity[] = "Paris";
```

Once an array is defined we can change the value with strcpy() but make sure if you do that that the new array is of the same size, or less. Otherwise you will overwrite other data in memory. You have to make your arrays big enough to hold all potential input, but don't over do it, or you'll consume too much memory.

```c
char yourCity[30];
printf("What city do you live in? ");
```

scanf() is kind of limited for adding a string to an array

1. It will allow you to overwrite data past the end of the space allowed
2. It won't allow you to enter spaces unless you define exactly how they will be entered

fgets() has neither of these problems and it also adds a \0 at the end for you. The only negative is that you must provide a size limit for the data being entered

```c
fgets(yourCity, 30, stdin);
printf("Hello %s\n\n", yourCity);
```

fgets() Will read in everything up till the end of the array is reached or until a \n is entered and then it will add a \0 at the end. It leaves in the \n though which can be a bad thing.

```c
for(int i = 0; i < 30; i++){
    if(yourCity[i] == '\n'){
        yourCity[i] = '\0';
        break;
    }
}
printf("Hello %s\n\n", yourCity);
```

strcmp() takes 2 strings and returns a negative number if the first string is less then the second. It returns a positive if the opposite occurs. It returns a 0 if they are equal

```c
printf("Is your city Paris? %d\n\n", strcmp(yourCity, thirdCity));
```

strcat() adds the second string to the end of the first

```c
char yourState[] = ", Pennsylvania";
strcat(yourCity, yourState);
printf("You live in %s\n\n", yourCity);
```

strlen() returns the length of the string minus \0

```c
printf("Letters in Paris : %d\n\n", strlen(thirdCity));
```

As mentioned before strcpy() is bad for copying strings because it can overwrite memory. That is were strlcpy() comes in. It won't overwrite memory and it always adds a \0

```c
strlcpy(yourCity, "El Pueblo del la Reina de Los Angeles", sizeof(yourCity));
printf("The new name is %s\n\n", yourCity);
```



## Pointers

```c
int rand1 = 12, rand2 = 15;
printf("rand1 = %p : rand2 = %p\n\n", &rand1, &rand2);
printf("rand1 = %d : rand2 = %d\n\n", &rand1, &rand2);

//rand1 = 0x7fff5f185bdc : rand2 = 0x7fff5f185bd8
//rand1 = 1595431900 : rand2 = 1595431896
```

To assign the address to another variable proceed it with an asterisk *

```c
int * pRand1 = &rand1;
```

If we use %p we get the hexadecimal version of the address

If we use %d we get the decimal version of the address

```c
printf("Pointer %p\n\n", pRand1); 
printf("Value %d\n\n", pRand1);
```

We have to use the * to get the value stored there. This is known as dereferencing the pointer. Dereferencing means to use the pointer to access the variable

```c
printf("Value %d\n\n", *pRand1);
```

```c
#include <stdio.h>

int main(){
	int a = 56;
	int *p = &a;
	printf("a = %d\n", a);
	printf("&a = %d\n", &a);
	printf("&a = %p\n", &a);
	printf("p = %d\n", p);
	printf("p = %p\n", p);
	*p = 45;
	printf("a = %d\n", a);
}
```

Pointer arithmetic

All types of arithmetic operations are not possible with pointers. The only valid operations that can be performed are as follows - Addition and subtraction of an integer to a pointer and increment/decrement operation.

For example if we have an integer pointer pi which contains address 1000 then on incrementing we get 1004 instead of 1001. This' is because the size of int data type is 4.  				 			 		

```c
#include <stdio.h>

int main(){
	int a = 56;
	int *p = &a;
	//Pointer arithmetic
	printf("p is %d\n", p);
	//p+1 should be 4 bytes ahead. Since it is an integer pointer.
	printf("p+1 is %d\n", p+1);
	printf("value at p+1 is %d\n", *(p+1));  //some garbage
}
```

Pointer to pointer

```c
#include <stdio.h>

int main(){
	int a = 56;
	int* p = &a;
	int** q = &p;
}
```

Function pass by reference

```c
#include <stdio.h>

void increment(int* a){
	*a = *a+1;
}

int main(){
	int a = 56;
	increment(&a);
	printf("a = %d\n",a);
}
```

**Pointers to arrays**

Address of element at index i  : &a[i] or a+i

Value of element at index i  : a[i] or *(a+i)

```c
#include <stdio.h>

int main(){
	int a[5] = {3,4,5,6,7};
	printf("sizeof a = %ld\n", sizeof(a));  //20
	printf("a = %d\n", a);  //a is actually a pointer to the first element of the array
	printf("dereference a *a = %d\n", *a);  //3
	printf("dereference a+1 *(a+1) = %d\n", *(a+1));  //4
}
```

Arrays are always passed by reference

```c
#include <stdio.h>

void Double(int* A, int size){
	int i, sum = 0;
	for(i=0; i<size; i++){
		A[i] = A[i]*2;
	}
}

int main(){
	int a[5] = {1,2,3,4,5};
	int size= sizeof(a)/sizeof(a[0]);
	Double(a, size);
	for(int i = 0; i<size; i++){
		printf("%d\n",a[i]);
	}
}
```

How to store strings ?

Size of array >= Number of characters in the string + 1

Strings are null terminated by '\0'

```c
#include <stdio.h>
#include <string.h>

int main(){
	char c[] = "ADITYA";
	printf("size of c is %ld\n", sizeof(c)); //7
	printf("length of string c is %ld\n", strlen(c)); //6
}
```

**Dynamic memory allocation** allocates a bunch of memory and returns a pointer to the first byte of the memory. This pointer can be cast to any pointer type.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
	int* ptr= ( int*)malloc(5*sizeof(int));
	printf("%d\n", sizeof(ptr));
	ptr[0]=4;
	ptr[1]=5;
	ptr[2]=6;
	ptr[3]=7;
	ptr[4]=8;
	printf("%d\n", *(ptr+3));
}
```



## More on Arrays, Pointers and Strings

A *string literal*, also termed a *string constant*, is anything enclosed in double quotation marks. The enclosed characters, plus a terminating \0 character automatically provided by the compiler, are stored in memory as a character string.

Whenever a string constant is present in the program, it is stored as an array of characters in memory terminated by the null character. The string itself becomes a pointer to the first character of the array. 

```c
char *p = "Taj Mahal";
```

Similarly when we do this - 

```c
printf("Hello World\n");
```

It is actually the pointer to the string which is passed to the printf function.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
	char a[] = "Delhi"; //a is a constant pointer
	printf("%d \n", sizeof(a)); //6
	char *b = "Delhi"; //b is a pointer variable. So requires more space
	printf("%d \n", sizeof(b)); //8

}
```

