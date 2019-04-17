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

