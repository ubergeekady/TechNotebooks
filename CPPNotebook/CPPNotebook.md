## Variables

```c++
int a, b = 2;
unsigned int b = 3;
short int b = 2;
unsigned short int c = 4;
long int d = 2;
unsigned long int f = 2;
long long g = 3;
unsigned long long g = 4;
float pi = 3.14
double x = 3.221
long double y = 3.141561415
char c1='a'
bool happy= true
```

Data types such as short, int, long, unsigned short, unsigned int, unsigned long, and the like have a finite capacity for containing numbers. When you exceed the limit imposed by the type chosen in an arithmetic operation, you create an overflow. Take unsigned short for an example. Data type short consumes 16 bits and can hence contain values from 0 through 65,535. When you add 1 to 65,535 in an unsigned short, the value overflows to 0. It’s like the odometer of a car that suffers a mechanical overflow when it can support only five digits and the car has done 99,999 kilometers  (or miles).

```c++
#include <iostream>
using namespace std;
int main()
{
	cout << "Computing the size of some C++ inbuilt variable types" << endl;
	cout << "Size of bool: " << sizeof(bool) << endl;
	cout << "Size of char: " << sizeof(char) << endl;
	cout << "Size of unsigned short int: " << sizeof(unsigned short) << endl;
	cout << "Size of short int: " << sizeof(short) << endl;
	cout << "Size of unsigned long int: " << sizeof(unsigned long) << endl;
	cout << "Size of long: " << sizeof(long) << endl;
	cout << "Size of int: " << sizeof(int) << endl;
	cout << "Size of unsigned long long: "<< sizeof(unsigned long long)<<endl;
	cout << "Size of long long: " << sizeof(long long) << endl;
	cout << "Size of unsigned int: " << sizeof(unsigned int) << endl;
	cout << "Size of float: " << sizeof(float) << endl;
	cout << "Size of double: " << sizeof(double) << endl;
	cout << "The output changes with compiler, hardware and OS" << endl;
	return 0;
}
```

```
Computing the size of some C++ inbuilt variable types
Size of bool: 1
Size of char: 1
Size of unsigned short int: 2
Size of short int: 2
Size of unsigned long int: 8
Size of long: 8
Size of int: 4
Size of unsigned long long: 8
Size of long long: 8
Size of unsigned int: 4
Size of float: 4
Size of double: 8
The output changes with compiler, hardware and OS
```



## Constants

The most important type of constants in C++ from a practical and programmatic point of view are declared by using keyword const before the variable type. The generic declaration looks like the following:

```
const type-name constant-name = value;
```



## Literals

Literals like 2 and 3.14 are typed as well.  Simply put, integral numbers are treated as long, int or unsigned long. Decimal numbers or numbers with exponents are treated as double. Literals of other types can be mentioned using suffix

```c
a = 2 //int
a = 2u //unsigned
a = 2l //long
a = 2ul //unsigned long
a = 2.0 //double
a = 2.0f //float
a = 2.0l //long double
```

The C++ compiler distinguishes single quotes ' ' from double "". The first one is considered char and the second one is a string.

C++14 introduces binary literals which are prefixed with 0b or 0B

```
int b1 = 0b11111010 //int b1 = 250;
```



## Arrays

```c++
int myNumbers [5] = {1,2}; //Only first two elements will be initialized.
int myNumbers [5] = {}; //All initialized to zero.
int myNumbers [] = {2016, 2052, -525}; // array of 3 elements
```

```
Bytes consumed by an array = sizeof(element-type) * Number of Elements
```

Access elements in the array using zero based index.

Two dimensional arrays.

```c++
int solarPanels [2][3];
int solarPanels [2][3] = {{0, 1, 2}, {3, 4, 5}};
```



## Operators to Increment (**++**) and Decrement (**—**)

It’s important to first understand the difference between prefix and postfix and then use the one that works for you. The result of execution of the postfix operators is that the l-value is first assigned the r-value and after that assignment the r-value is incremented (or decremented). This means that in all cases where a postfix operator has been used, the value of num2 is the old value of num1 (the value before the increment or decrement operation).Prefix operators have exactly the opposite in behavior. The r-value is first incremented and then assigned to the l-value. In these cases, num2 and num1 carry the same value. Listing 5.2 demonstrates the effect of prefix and postfix increment and decrement opera- tors on a sample integer. 



## Program Flow

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




switch (n)
{
    case 1: // code to be executed if n = 1;
        break;
    case 2: // code to be executed if n = 2;
        break;
    default: // code to be executed if n doesn't match any cases
}




if (condition) {
// condition Statement 1; Statement 2;
} else {
// condition Statement 3; Statement 4;
}



(conditional expression evaluated to bool) ? expression1 if true : expression2 if false;
```



## The Range-Based **for** Loop (C++11)

```
for (VarType varName : sequence) {
	// Use varName that contains an element from sequence
}
```

```c++
#include <iostream>
using namespace std;

int main(){
    int myNumbers [5] = {1,2,3,4,5};
    for(int i : myNumbers){
        cout << i;
    }
}
```



## Functions

Functions with the same name and return type but with different parameters or set of parameters are said to be overloaded functions.

```c++
double Area(double radius);
double Area(double radius, double height);
```

There are cases where you might need a function to work on a variable that modifies a value that is avail- able outside the function, too, say in the calling function. This is when you declare a parameter that takes an argument *by reference*.

```c++
// output parameter result by reference 
void Area(double radius, double& result) 
{
	result = Pi * radius * radius;
}
```



## Pointers

*Refer to C Notes*



## Reference

A reference is an alias for a variable. When you declare a reference, you need to initialize it to a variable. Thus, the reference variable is just a different way to access the data stored in the variable being referenced. You would declare a reference using the reference operator (&) as seen in the following statement:

```c++
VarType original = Value;
VarType& ReferenceVariable = original;
```

References enable you to work with the memory location they are initialized to. This makes references particularly useful when programming functions.