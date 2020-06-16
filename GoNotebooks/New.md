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

```go
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

break and continue just like C

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

**There is a subtlety to be considered when using fallthrough. Fallthrough will happen even when the case evaluates to false.**

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

## Arrays

An array belongs to type [n]T

```go
func main() {  
    var a [3]int //int array with length 3
    fmt.Println(a)
}
```

```
[0 0 0]
```

```go
func main() {  
    var a [3]int //int array with length 3
    a[0] = 12 // array index starts at 0
    a[1] = 78
    a[2] = 50
    fmt.Println(a)
}
```

```go
func main() {  
    a := [3]int{12, 78, 50} // short hand declaration to create array
    fmt.Println(a)
}
```

It is not necessary that all elements in an array have to be assigned a value during short hand declaration.

```go
func main() {  
    a := [3]int{12} 
    fmt.Println(a)
}
```

The program will output [12 0 0]

```go
func main() {  
    a := [...]int{12, 78, 50} // ... makes the compiler determine the length
    fmt.Println(a)
}
```

Hence `[5]int` and `[25]int` are distinct types. Because of this, arrays cannot be resized. 

##### Arrays are value types

Arrays in Go are value types and not reference types. This means that when they are assigned to a new variable, a copy of the original array is assigned to the new variable. If changes are made to the new variable, it will not be reflected in the original array.

```go
func main() {  
    a := [...]string{"USA", "China", "India", "Germany", "France"}
    b := a // a copy of a is assigned to b
    b[0] = "Singapore"
    fmt.Println("a is ", a)
    fmt.Println("b is ", b) 
}
```

Similarly when arrays are passed to functions as parameters, they are passed by value and the original array in unchanged.

```go
func main() {  
    a := [...]float64{67.7, 89.8, 21, 78}
    fmt.Println("length of a is",len(a))
}
```

The `for` loop can be used to iterate over elements of an array.

Go provides a better and concise way to iterate over an array by using the **range** form of the `for` loop.

```go
func main() {  
    a := [...]float64{67.7, 89.8, 21, 78}
    sum := float64(0)
    for i, v := range a {//range returns both the index and value
        fmt.Printf("%d the element of a is %.2f\n", i, v)
        sum += v
    }
    fmt.Println("\nsum of all elements of a",sum)
}
```

```go
for _, v := range a { //ignores index  
}
```

```go
package main


import (  
    "fmt"
)

func printarray(a [3][2]string) {  
    for _, v1 := range a {
        for _, v2 := range v1 {
            fmt.Printf("%s ", v2)
        }
        fmt.Printf("\n")
    }
}

func main() {  
    a := [3][2]string{
        {"lion", "tiger"},
        {"cat", "dog"},
        {"pigeon", "peacock"}, //this comma is necessary. The compiler will complain if you omit this comma
    }
    printarray(a)
    var b [3][2]string
    b[0][0] = "apple"
    b[0][1] = "samsung"
    b[1][0] = "microsoft"
    b[1][1] = "google"
    b[2][0] = "AT&T"
    b[2][1] = "T-Mobile"
    fmt.Printf("\n")
    printarray(b)
}
```

```
lion tiger  
cat dog  
pigeon peacock 

apple samsung  
microsoft google  
AT&T T-Mobile  
```

## Slices

A slice is a convenient, flexible and powerful wrapper on top of an array. Slices do not own any data on their own. They are the just references to existing arrays.

```go
func main() {  
    a := [5]int{76, 77, 78, 79, 80}
    var b []int = a[1:4] //creates a slice from a[1] to a[3]
    fmt.Println(b)
}
```

The syntax `a[start:end]` creates a slice from array `a` starting from index `start` to index `end - 1`. So in line no. 9 of the above program `a[1:4]` creates a slice representation of the array `a` starting from indexes 1 through 3. Hence the slice `b` has values `[77 78 79]`.

```go
func main() {  
    c := []int{6, 7, 8} //creates and array and returns a slice reference
    fmt.Println(c)
}
```

```go
func main() {  
    darr := [...]int{57, 89, 90, 82, 100, 78, 67, 69, 59}
    dslice := darr[2:5]
    fmt.Println("array before",darr)
    for i := range dslice {
        dslice[i]++
    }
    fmt.Println("array after",darr) 
}
```

In line number 9 of the above program, we create dslice from indexes 2, 3, 4 of the array. The for loop increments the value in these indexes by one. When we print the array after the for loop, we can see that the changes to the slice are reflected in the array. The output of the program is

```
array before [57 89 90 82 100 78 67 69 59]  
array after [57 89 91 83 101 78 67 69 59]
```

When a number of slices share the same underlying array, the changes that each one makes will be reflected in the array.

```go
func main() {  
    numa := [3]int{78, 79 ,80}
    nums1 := numa[:] //creates a slice which contains all elements of the array
    nums2 := numa[:]
    fmt.Println("array before change 1",numa)
    nums1[0] = 100
    fmt.Println("array after modification to slice nums1", numa)
    nums2[1] = 101
    fmt.Println("array after modification to slice nums2", numa)
}
```

In line no. 9, in `numa[:]` the start and end values are missing. The default values for start and end are `0` and `len(numa)` respectively. Both slices `nums1` and `nums2` share the same array. The output of the program is

```
array before change 1 [78 79 80]  
array after modification to slice nums1 [100 79 80]  
array after modification to slice nums2 [100 101 80]
```

The length of the slice is the number of elements in the slice. **The capacity of the slice is the number of elements in the underlying array starting from the index from which the slice is created.**

func make([]T, len, cap) []T can be used to create a slice by passing the type, length and capacity. The capacity parameter is optional and defaults to the length. The make function creates an array and returns a slice reference to it.

```go
func main() {  
    i := make([]int, 5, 5)
    fmt.Println(i)
}
```

The values are zeroed by default when a slice is created using make. The above program will output `[0 0 0 0 0]`.

As we already know arrays are restricted to fixed length and their length cannot be increased. Slices are dynamic and new elements can be appended to the slice using `append` function. The definition of append function is `func append(s []T, x ...T) []T`.

**x ...T** in the function definition means that the function accepts variable number of arguments for the parameter x. These type of functions are called **variadic functions.**

One question might be bothering you though. If slices are backed by arrays and arrays themselves are of fixed length then how come a slice is of dynamic length. Well what happens under the hood is, when new elements are appended to the slice, a new array is created. The elements of the existing array are copied to this new array and a new slice reference for this new array is returned. The capacity of the new slice is now twice that of the old slice. Pretty cool right :).

The zero value of a slice type is `nil`. A `nil` slice has length and capacity 0. It is possible to append values to a `nil` slice using the append function.

```go
func main() {  
    var names []string //zero value of a slice is nil
    if names == nil {
        fmt.Println("slice is nil going to append")
        names = append(names, "John", "Sebastian", "Vinay")
        fmt.Println("names contents:",names)
    }
}
```

It is also possible to append one slice to another using the `...` operator.

```go
func main() {  
    veggies := []string{"potatoes","tomatoes","brinjal"}
    fruits := []string{"oranges","apples"}
    food := append(veggies, fruits...)
    fmt.Println("food:",food)
}
```

##### Passing a slice to a function

Slices can be thought of as being represented internally by a structure type.

```go
type slice struct {  
    Length        int
    Capacity      int
    ZerothElement *byte
}
```

A slice contains the length, capacity and a pointer to the zeroth element of the array. When a slice is passed to a function, even though it's passed by value, the pointer variable will refer to the same underlying array. Hence when a slice is passed to a function as parameter, changes made inside the function are visible outside the function too.

```go
func subtactOne(numbers []int) {  
    for i := range numbers {
        numbers[i] -= 2
    }

}
func main() {  
    nos := []int{8, 7, 6}
    fmt.Println("slice before function call", nos)
    subtactOne(nos)                               //function modifies the slice
    fmt.Println("slice after function call", nos) //modifications are visible outside
}
```

The function call in line number 17 of the above program decrements each element of the slice by 2. When the slice is printed after the function call, these changes are visible. If you can recall, this is different from an array where the changes made to an array inside a function are not visible outside the function. Output of the above program is,

```
slice before function call [8 7 6]  
slice after function call [6 5 4]  
```

**Multidimensional slices**

```go
func main() {  
     pls := [][]string {
            {"C", "C++"},
            {"JavaScript"},
            {"Go", "Rust"},
            }
    for _, v1 := range pls {
        for _, v2 := range v1 {
            fmt.Printf("%s ", v2)
        }
        fmt.Printf("\n")
    }
}
```

##### Memory Optimisation

Slices hold a reference to the underlying array. As long as the slice is in memory, the array cannot be garbage collected. This might be of concern when it comes to memory management. Lets assume that we have a very large array and we are interested in processing only a small part of it. Henceforth we create a slice from that array and start processing the slice. The important thing to be noted here is that the array will still be in memory since the slice references it.

One way to solve this problem is to use the [copy](https://golang.org/pkg/builtin/#copy) function `func copy(dst, src []T) int` to make a copy of that slice. This way we can use the new slice and the original array can be garbage collected.

```go
func countries() []string {  
    countries := []string{"USA", "Singapore", "Germany", "India", "Australia"}
    neededCountries := countries[:len(countries)-2]
    countriesCpy := make([]string, len(neededCountries))
    copy(countriesCpy, neededCountries) //copies neededCountries to countriesCpy
    return countriesCpy
}
func main() {  
    countriesNeeded := countries()
    fmt.Println(countriesNeeded)
}
```

## Variadic Functions

*A variadic function is a function that accepts a variable number of arguments. If the last parameter of a function definition is prefixed by ellipsis **...**, then the function can accept any number of arguments for that parameter.*

**Only the last parameter of a function can be variadic. We will learn why this is the case in the next section of this tutorial.**

```go
func hello(a int, b ...int) {  
}
```

```go
hello(1, 2) //passing one argument "2" to b  
hello(5, 6, 7, 8, 9) //passing arguments "6, 7, 8 and 9" to b  
```

It is also possible to pass zero arguments to a variadic function.

```lanaguage
hello(1)  
```

In the above code, we call `hello` with zero arguments for `b`. This is perfectly fine.

**The way variadic functions work is by converting the variable number of arguments to a slice of the type of the variadic parameter.**

**There is a syntactic sugar which can be used to pass a slice to a variadic function. You have to suffix the slice with ellipsis `...` If that is done, the slice is directly passed to the function without a new slice being created.**

```go
func main() {  
    nums := []int{89, 90, 95}
    find(89, nums...)
}

func find(num int, nums ...int) {  

```

```go
package main

import (  
    "fmt"
)

func change(s ...string) {  
    s[0] = "Go"
}

func main() {  
    welcome := []string{"hello", "world"}
    change(welcome...)
    fmt.Println(welcome)
}
```

What do you think will be the output of the above program? If you think it will be `[Go world]` Congrats! you have understood variadic functions and slices. If you got it wrong, no big deal, let me explain how we get this output.

## Maps

```go
func main() {  
    employeeSalary := make(map[string]int)
    employeeSalary["steve"] = 12000
    employeeSalary["jamie"] = 15000
    employeeSalary["mike"] = 9000
    fmt.Println("employeeSalary map contents:", employeeSalary)
}
```

```
employeeSalary map contents: map[steve:12000 jamie:15000 mike:9000]  
```

```go
func main() {  
    employeeSalary := map[string]int {
        "steve": 12000,
        "jamie": 15000,
    }
    employeeSalary["mike"] = 9000
    fmt.Println("employeeSalary map contents:", employeeSalary)
}
```

It's not necessary that only [string](https://golangbot.com/strings) types should be keys. All comparable types such as boolean, integer, float, complex, string, ... can also be keys. Even user-defined types such as [structs](https://golangbot.com/structs) can be keys. If you would like to know more about comparable types, please visit http://golang.org/ref/spec#Comparison_operators

The zero value of a map is `nil`. If you try to add elements to a `nil` map, a run-time [panic](https://golangbot.com/panic-and-recover/) will occur. Hence the map has to be initialized before adding elements.

```go
func main() {  
    var employeeSalary map[string]int
    employeeSalary["steve"] = 12000
}
```

```
panic: assignment to entry in nil map
```

```go
func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
        "mike": 9000,
    }
    employee := "jamie"
    salary := employeeSalary[employee]
    fmt.Println("Salary of", employee, "is", salary)
}
```

What will happen if an element is not present? The map will return the zero value of the type of that element. In the case of `employeeSalary` map, if we try to access an element which is not present, the zero value of `int` which is `0` will be returned.

```go
func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }
    fmt.Println("Salary of joe is", employeeSalary["joe"])
}
```

```go
value, ok := map[key]  
```

The above is the syntax to find out whether a particular key is present in a map. If `ok` is true, then the key is present and its value is present in the variable `value`, else the key is absent.

```go
func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }
    newEmp := "joe"
    value, ok := employeeSalary[newEmp]
    if ok == true {
        fmt.Println("Salary of", newEmp, "is", value)
        return
    }
    fmt.Println(newEmp, "not found")

}
```

In the above program, in line no. 13, `ok` will be false since `joe` is not present. Hence the program will print,

```
joe not found  
```

```go
func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
        "mike":  9000,
    }
    fmt.Println("Contents of the map")
    for key, value := range employeeSalary {
        fmt.Printf("employeeSalary[%s] = %d\n", key, value)
    }

}
```

```
Contents of the map  
employeeSalary[mike] = 9000  
employeeSalary[steve] = 12000  
employeeSalary[jamie] = 15000 
```

```go
func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,     
        "mike": 9000,
    }
    fmt.Println("map before deletion", employeeSalary)
    delete(employeeSalary, "steve")
    fmt.Println("map after deletion", employeeSalary)

}
```

```
map before deletion map[steve:12000 jamie:15000 mike:9000]  
map after deletion map[mike:9000 jamie:15000]
```

```go
package main

import (  
    "fmt"
)

type employee struct {  
    salary  int
    country string
}

func main() {  
    emp1 := employee{
        salary:  12000,
        country: "USA",
    }
    emp2 := employee{
        salary:  14000,
        country: "Canada",
    }
    emp3 := employee{
        salary:  13000,
        country: "India",
    }
    employeeInfo := map[string]employee{
        "Steve": emp1,
        "Jamie": emp2,
        "Mike":  emp3,
    }

    for name, info := range employeeInfo {
        fmt.Printf("Employee: %s Salary:$%d  Country: %s\n", name, info.salary, info.country)
    }

}
```

```
Employee: Mike Salary:$13000  Country: India  
Employee: Steve Salary:$12000  Country: USA  
Employee: Jamie Salary:$14000  Country: Canada
```

```go
package main

import (  
    "fmt"
)

func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,
    }
    fmt.Println("length is", len(employeeSalary))

}
```

Similar to slices, maps are reference types. When a map is assigned to a new variable, they both point to the same internal data structure. Hence changes made in one will reflect in the other.

```go
package main

import (  
    "fmt"
)

func main() {  
    employeeSalary := map[string]int{
        "steve": 12000,
        "jamie": 15000,     
        "mike": 9000,
    }
    fmt.Println("Original employee salary", employeeSalary)
    modified := employeeSalary
    modified["mike"] = 18000
    fmt.Println("Employee salary changed", employeeSalary)

}
```

## Unicode

**[...TO BE WRITTEN...]**



## Strings

A string is a slice of bytes in Go. Strings can be created by enclosing a set of characters inside double quotes " ". Since a string is a slice of bytes, it's possible to access each byte of a string.

```go
package main

import (  
    "fmt"
)

func printBytes(s string) {  
    fmt.Printf("Bytes: ")
    for i := 0; i < len(s); i++ {
        fmt.Printf("%x ", s[i])
    }
}

func main() {  
    name := "Hello World"
    fmt.Printf("String: %s\n", name)
    printBytes(name)
}

```

```
String: Hello World  
Bytes: 48 65 6c 6c 6f 20 57 6f 72 6c 64  
```

**%s is the format specifier to print a string.** In line no. 16, the input string is printed. In line no. 9 of the program above, **len(s) returns the number of bytes in the string** and we use a for loop to print those bytes in hexadecimal notation. **%x is the format specifier for hexadecimal.** **%c format specifier is used to print the characters of the string**

These are the Unicode UT8-encoded values of Hello World. A basic understanding of Unicode and UTF-8 is needed to understand strings better.

**[...TO BE WRITTEN...]**

## Pointers

```go
func main() {  
    b := 255
    var a *int = &b
    fmt.Printf("Type of a is %T\n", a)
    fmt.Println("address of b is", a)
}
```

The **&** operator is used to get the address of a variable. In line no. 9 of the above program we are assigning the address of `b` to `a` whose type is `*int`. Now a is said to point to b. When we print the value in `a`, the address of `b` will be printed. This program outputs

```
Type of a is *int  
address of b is 0x1040a124 
```

The zero value of a pointer is `nil`.

Go also provides a handy function `new` to create pointers. The `new` function takes a type as argument and returns a pointer to a newly allocated zero value of the type passed as argument.

```go
func main() {  
    size := new(int)
    fmt.Printf("Size value is %d, type is %T, address is %v\n", *size, size, size)
    *size = 85
    fmt.Println("New size value is", *size)
}
```

```
Size value is 0, type is *int, address is 0x414020  
New size value is 85 
```

Dereferencing a pointer means accessing the value of the variable which the pointer points to. `*a` is the syntax to deference a.

```go
func main() {  
    b := 255
    a := &b
    fmt.Println("address of b is", a)
    fmt.Println("value of b is", *a)
}
```

```
address of b is 0x1040a124  
value of b is 255  
```

```go
func main() {  
    b := 255
    a := &b
    fmt.Println("address of b is", a)
    fmt.Println("value of b is", *a)
    *a++
    fmt.Println("new value of b is", b)
}
```

In line no. 12 of the above program, we increment the value pointed by a by 1 which changes the value of b *since a points to b*. Hence the value of b becomes 256. The output of the program is

```
address of b is 0x1040a124  
value of b is 255  
new value of b is 256 
```

```go
func change(val *int) {  
    *val = 55
}
func main() {  
    a := 58
    fmt.Println("value of a before function call is",a)
    b := &a
    change(b)
    fmt.Println("value of a after function call is", a)
}
```

In the above program, in line no. 14 we are passing the pointer variable b which holds the address of a to the function `change`. Inside `change` function, value of a is changed using dereference in line no 8. This program outputs,

```
value of a before function call is 58  
value of a after function call is 55
```

It is perfectly legal for a function to return a pointer of a local variable. The Go compiler is intelligent enough and it will allocate this variable on the heap.

```go
func hello() *int {  
    i := 5
    return &i
}
func main() {  
    d := hello()
    fmt.Println("Value of d", *d)
}
```

In line no. 9 of the program above, we return the address of the local variable `i` from the function `hello`. **The behavior of this code is undefined in programming languages such as C and C++ as the variable `i` goes out of scope once the function `hello` returns. But in the case of Go, the compiler does a escape analysis and allocates `i` on the heap as the address escapes the local scope.** Hence this program will work and it will print,

```
Value of d 5  
```

**Do not pass a pointer to an array as a argument to a function. Use slice instead.**

```go
package main

import (  
    "fmt"
)

func modify(arr *[3]int) {  
    (*arr)[0] = 90
}

func main() {  
    a := [3]int{89, 90, 91}
    modify(&a)
    fmt.Println(a)
}
```

In line no. 13 of the above program, we are passing the address of the array `a` to the `modify` function. In line no.8 in the `modify` function we are dereferencing arr and assigning `90` to the first element of the array. This program outputs `[90 90 91]`

**a[x] is shorthand for (\*a)[x]. So (\*arr)[0] in the above program can be replaced by arr[0]**. Lets rewrite the above program using this shorthand syntax.

```go
package main

import (  
    "fmt"
)

func modify(arr *[3]int) {  
    arr[0] = 90
}

func main() {  
    a := [3]int{89, 90, 91}
    modify(&a)
    fmt.Println(a)
}
```

This program also outputs [90 90 91]

Although this way of passing a pointer to an array as a argument to a function and making modification to it works, it is not the idiomatic way of achieving this in Go. We have slices for this.

Lets rewrite the same program using slices.

```go
package main

import (  
    "fmt"
)

func modify(sls []int) {  
    sls[0] = 90
}

func main() {  
    a := [3]int{89, 90, 91}
    modify(a[:])
    fmt.Println(a)
}
```

In line no.13 of the program above, we pass a slice to the `modify` function. The first element of the slice is changed to `90` inside the `modify` function. This program also outputs `[90 90 91]`. **So forget about passing pointers to arrays around and use slices instead :)**. This code is much more clean and is idiomatic Go :).

## Structs

```go
type Employee struct {  
    firstName string
    lastName  string
    age       int
}
```

```go
type Employee struct {  
    firstName, lastName string
    age                 int
}
//Not recommended
```

```go
package main

import (  
    "fmt"
)

type Employee struct {  
    firstName string
    lastName  string
    age       int
    salary    int
}

func main() {

    //creating struct specifying field names
    emp1 := Employee{
        firstName: "Sam",
        age:       25,
        salary:    500,
        lastName:  "Anderson",
    }

    //creating struct without specifying field names - not recommended
    emp2 := Employee{"Thomas", "Paul", 29, 800}

    fmt.Println("Employee 1", emp1)
    fmt.Println("Employee 2", emp2)
}
```

**In line 25. of the above program, `emp2` is defined by omitting the field names. In this case, it is necessary to maintain the order of fields to be the same as specified in the struct declaration. Please refrain from using this syntax since it makes it difficult to figure out which value is for which field.**

Anon structs

```go
package main

import (  
    "fmt"
)

func main() {  
    emp3 := struct {
        firstName string
        lastName  string
        age       int
        salary    int
    }{
        firstName: "Andreah",
        lastName:  "Nikola",
        age:       31,
        salary:    5000,
    }

    fmt.Println("Employee 3", emp3)
}
```

```
Employee 3 {Andreah Nikola 31 5000}  
```

```go
package main

import (  
    "fmt"
)

type Employee struct {  
    firstName string
    lastName  string
    age       int
    salary    int
}

func main() {  
    emp6 := Employee{
        firstName: "Sam",
        lastName:  "Anderson",
        age:       55,
        salary:    6000,
    }
    fmt.Println("First Name:", emp6.firstName)
    fmt.Println("Last Name:", emp6.lastName)
    fmt.Println("Age:", emp6.age)
    fmt.Printf("Salary: $%d\n", emp6.salary)
    emp6.salary = 6500
    fmt.Printf("New Salary: $%d", emp6.salary)
}
```

```
First Name: Sam  
Last Name: Anderson  
Age: 55  
Salary: $6000  
New Salary: $6500
```

When a struct is defined and it is not explicitly initialized with any value, the fields of the struct are assigned their zero values by default.

It is also possible to specify values for some fields and ignore the rest. In this case, the ignored fields are assigned zero values.

```go
    emp5 := Employee{
        firstName: "John",
        lastName:  "Paul",
    }
```

```go
func main() {  
    emp8 := &Employee{
        firstName: "Sam",
        lastName:  "Anderson",
        age:       55,
        salary:    6000,
    }
    fmt.Println("First Name:", (*emp8).firstName)
    fmt.Println("Age:", (*emp8).age)
}
```

**The Go language gives us the option to use `emp8.firstName` instead of the explicit dereference `(*emp8).firstName` to access the `firstName` field.**

```go
package main

import (  
    "fmt"
)

type Address struct {  
    city  string
    state string
}

type Person struct {  
    name    string
    age     int
    address Address
}

func main() {  
    p := Person{
        name: "Naveen",
        age:  50,
        address: Address{
            city:  "Chicago",
            state: "Illinois",
        },
    }

    fmt.Println("Name:", p.name)
    fmt.Println("Age:", p.age)
    fmt.Println("City:", p.address.city)
    fmt.Println("State:", p.address.state)
}
```

### Promoted fields

Fields that belong to an anonymous struct field in a struct are called promoted fields since they can be accessed as if they belong to the struct which holds the anonymous struct field. I can understand that this definition is quite complex so let's dive right into some code to understand this :).

```go
type Address struct {  
    city string
    state string
}
type Person struct {  
    name string
    age  int
    Address
}
```

In the above code snippet, the `Person` struct has an anonymous field `Address` which is a struct. Now the fields of the `Address` namely `city` and `state` are called promoted fields since they can be accessed as if they are directly declared in the `Person` struct itself.

```go
package main

import (  
    "fmt"
)

type Address struct {  
    city  string
    state string
}
type Person struct {  
    name string
    age  int
    Address
}

func main() {  
    p := Person{
        name: "Naveen",
        age:  50,
        Address: Address{
            city:  "Chicago",
            state: "Illinois",
        },
    }

    fmt.Println("Name:", p.name)
    fmt.Println("Age:", p.age)
    fmt.Println("City:", p.city)   //city is promoted field
    fmt.Println("State:", p.state) //state is promoted field
}
```

**Structs are value types and are comparable if each of their fields are comparable. Two struct variables are considered equal if their corresponding fields are equal.**

**Struct variables are not comparable if they contain fields that are not comparable** 