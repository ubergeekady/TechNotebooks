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

**Constants**

<u>**Go internally treats constants as untyped**</u>

The value of a constant should be known at compile time.

```go
var a = math.Sqrt(4)//allowed
const b = math.Sqrt(4)//not allowed
```

The answer is untyped constants have a default type associated with them and they supply it if and only if a line of code demands it. In the statement var name = "Sam", name needs a type and it gets it from the default type of the string constant "Sam" which is a string.

```go
package main

func main() {  
        var defaultName = "Sam" //allowed
        type myString string
        var customName myString = "Sam" //allowed
        customName = defaultName //not allowed

}
```

## Functions

```
func functionname(parametername type) returntype {  
 //function body
}
```

If consecutive parameters are of the same type, we can avoid writing the type each time and it is enough to be written once at the end.ie price int, no int can be written as price, no int.

Multiple Return Values

```go
package main

import (
    "fmt"
)

func myFunc(x int)(int, int, int, int){
        return x*2, x*3, x*4, x*5
}

func main(){
        a,b,c,d := myFunc(2)
        fmt.Println(a,b,c,d)
}
```

It is possible to return named values from a function. If a return value is named, it can be considered as being declared as a variable in the first line of the function.

```go
func rectProps(length, width float64)(area, perimeter float64) {  
    area = length * width
    perimeter = (length + width) * 2
    return //no explicit return value
}
```

## Conditionals, Loops, Switch Case

```
if condition {  
}
```

Unlike in other languages like C, the {  } are mandatory even if there is only one statement between the { }.

```
if condition {  
} else if condition {
} else {
}
```

There can be any number of else ifs. The condition is evaluated for truth from the top to bottom. Which ever if or else if's condition evaluates to true, the corresponding block of code is executed. If none of the conditions are true then else block is executed.

```
for initialisation; condition; post {  
}
```

Break and continue just like C

```go
//Multiple variables in for statement
package main

import (  
    "fmt"
)

func main() {  
    for no, i := 10, 1; i <= 10 && no <= 19; i, no = i+1, no+1 {
        fmt.Printf("%d * %d = %d\n", no, i, no*i)
    }

}
```

```go
func main() {  
    finger := 4
    fmt.Printf("Finger %d is ", finger)
    switch finger {
    case 1:
        fmt.Println("Thumb")
    case 2:
        fmt.Println("Index")
    case 3:
        fmt.Println("Middle")
    case 4:
        fmt.Println("Ring")
    case 5:
        fmt.Println("Pinky")

    }
}
```

The cases are evaluated from top to bottom and the first case which matches the expression is executed. In this case, finger has a value of 4 and hence

Duplicate cases with the same constant value are not allowed.

The default case will be executed when none of the other cases match.

```go
func main() {  
    switch finger := 8; finger {
    case 1:
        fmt.Println("Thumb")
    case 2:
        fmt.Println("Index")
    case 3:
        fmt.Println("Middle")
    case 4:
        fmt.Println("Ring")
    case 5:
        fmt.Println("Pinky")
    default: //default case
        fmt.Println("incorrect finger number")
    }
}
```

In the above program finger is 8 and it does not match any of the cases and hence incorrect finger number in the default case is printed. It's not necessary that default should be the last case in a switch statement. It can be present anywhere in the switch.

You might also have noticed a small change in the declaration of finger. It is declared in the switch itself. A switch can include an optional statement that is executed before the expression is evaluated. In line no. 8, finger is first declared and then used in the expression. The scope of finger in this case is limited to the switch block.

It is possible to include multiple expressions in a case by separating them with comma.

```go
func main() {  
    letter := "i"
    fmt.Printf("Letter %s is a ", letter)
    switch letter {
    case "a", "e", "i", "o", "u": //multiple expressions in case
        fmt.Println("vowel")
    default:
        fmt.Println("not a vowel")
    }
}
```

The expression in a switch is optional and it can be omitted. If the expression is omitted, the switch is considered to be switch true and each of the case expression is evaluated for truth and the corresponding block of code is executed.

```go
func main() {  
    num := 75
    switch { // expression is omitted
    case num >= 0 && num <= 50:
        fmt.Printf("%d is greater than 0 and less than 50", num)
    case num >= 51 && num <= 100:
        fmt.Printf("%d is greater than 51 and less than 100", num)
    case num >= 101:
        fmt.Printf("%d is greater than 100", num)
    }

}
```

In Go, the control comes out of the switch statement immediately after a case is executed. A fallthrough statement is used to transfer control to the first statement of the case that is present immediately after the case which has been executed.

**Fallthrough happens even when the case evaluates to false**

There is a subtlety to be considered when using fallthrough. Fallthrough will happen even when the case evaluates to false.

```go
package main

import (  
    "fmt"
)

func main() {  
    switch num := 25; { 
    case num < 50:
        fmt.Printf("%d is lesser than 50\n", num)
        fallthrough
    case num > 100:
        fmt.Printf("%d is greater than 100\n", num)     
    }

}
```

In the above program, `num` is 25 which is less than 50 and hence the case in line no. 9 evaluates to true. A `fallthrough` is present in line no. 11. The next case `case num > 100:` in line no. 12 is false since num < 100. But fallthrough doesn't consider this. Fallthrough will happen even though the case evaluates to false.

The break statement can be used to terminate a switch early before it completes. Let's just modify the above example to a contrived one to understand how break works.