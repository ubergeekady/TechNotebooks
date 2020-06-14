## Variables, Types and Constants

```go
var age int // variable declaration
var age int // variable declaration
age = 29 //assignment
age = 54 //assignment

var age int = 29 // variable declaration with initial value

var age = 29 // type will be inferred

var width, height int = 100, 50 //declaring multiple variables
var width, height = 100, 50 //"int" is dropped

var width, height int
width = 100
height = 50


var (
    name   = "ady"
    age    = 29
    height int
)

count := 10
name, age := "ady", 29 //short hand declaration
```

Short hand syntax can only be used when at least one of the variables on the left side of := is newly declared.

bool
string

**Numeric Types**
int8, int16, int32, int64, int
uint8, uint16, uint32, uint64, uint
float32, float64
complex64, complex128
byte
rune

**int8:** represents 8 bit signed integers
**size:** 8 bits
**range:** -128 to 127

**int16:** represents 16 bit signed integers
**size:** 16 bits
**range:** -32768 to 32767

**int32:** represents 32 bit signed integers
**size:** 32 bits
**range:** -2147483648 to 2147483647

**int64:** represents 64 bit signed integers
**size:** 64 bits
**range:** -9223372036854775808 to 9223372036854775807

**int:** represents 32 or 64 bit integers depending on the underlying platform. You should generally be using *int* to represent integers unless there is a need to use a specific sized integer.
**size:** 32 bits in 32 bit systems and 64 bit in 64 bit systems.
**range:** -2147483648 to 2147483647 in 32 bit systems and -9223372036854775808 to 9223372036854775807 in 64 bit systems

The type of a variable can be printed using %T format specifier in Printf function. Go has a package unsafe which has a Sizeof function which returns in bytes the size of the variable passed to it. unsafe package should be used with care as the code using it might have portability issues, but for the purposes of this tutorial we can use it.

```go
package main

import (  
    "fmt"
    "unsafe"
)

func main() {  
    var a int = 89
    b := 95
    fmt.Println("value of a is", a, "and b is", b)
    fmt.Printf("type of a is %T, size of a is %d", a, unsafe.Sizeof(a)) //type and size of a
    fmt.Printf("\ntype of b is %T, size of b is %d", b, unsafe.Sizeof(b)) //type and size of b
}
```

```
value of a is 89 and b is 95  
type of a is int, size of a is 4  
type of b is int, size of b is 4 
```

**uint8:** represents 8 bit unsigned integers
**size:** 8 bits
**range:** 0 to 255

**uint16:** represents 16 bit unsigned integers
**size:** 16 bits
**range:** 0 to 65535

**uint32:** represents 32 bit unsigned integers
**size:** 32 bits
**range:** 0 to 4294967295

**uint64:** represents 64 bit unsigned integers
**size:** 64 bits
**range:** 0 to 18446744073709551615

**uint :** represents 32 or 64 bit unsigned integers depending on the underlying platform.
**size :** 32 bits in 32 bit systems and 64 bits in 64 bit systems.
**range :** 0 to 4294967295 in 32 bit systems and 0 to 18446744073709551615 in 64 bit systems

**float32:** 32 bit floating point numbers
**float64:** 64 bit floating point numbers

```go
package main

import (  
    "fmt"
)

func main() {  
    a, b := 5.67, 8.97
    fmt.Printf("type of a %T b %T\n", a, b)
    sum := a + b
    diff := a - b
    fmt.Println("sum", sum, "diff", diff)

    no1, no2 := 56, 89
    fmt.Println("sum", no1+no2, "diff", no1-no2)
}
```

**complex64:** complex numbers which have float32 real and imaginary parts
**complex128:** complex numbers with float64 real and imaginary parts

The builtin function complex is used to construct a complex number with real and imaginary parts. The complex function has the following definition

func complex(r, i FloatType) ComplexType  

It takes a real and imaginary part as a parameter and returns a complex type. Both the real and imaginary parts must be of the same type. ie either float32 or float64. If both the real and imaginary parts are float32, this function returns a complex value of type complex64. If both the real and imaginary parts are of type float64, this function returns a complex value of type complex128

```
c := 6 + 7i 
```

**byte** is an alias of uint8
**rune** is an alias of int32

**Go is very strict about explicit typing. There is no automatic type promotion or conversion.**

The value of a constant should be known at compile time.

```go
    var a = math.Sqrt(4)//allowed
    const b = math.Sqrt(4)//not allowed
```

