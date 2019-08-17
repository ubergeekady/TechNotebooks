## Hello World

```go
package main
import "fmt"
func main(){
	fmt.println("Hello World")
}
```



## Variables

```go
//Declare it now and initialize and use later
var i int
i = 42

var j int = 27

//Automatically figure out data type (only inside functions)
k := 99

fmt.Println(i)
//42

fmt.Printf("%v, %T", j,j)
//27, int
```

```go
a := 99.9
fmt.Printf("%v, %T", j,j)
//99.9, float64
```

```go
//At package level only
var(
		x string = "Aditya"
		y int = 3
)
```

Variable in the innermost scope will take precedence

```go
package main
import "fmt"
var k int = 32
func main(){
	fmt.println(k)
  //32
	var k int = 27
	fmt.println(k)
	//27
}
```

If you have a local variable which is declared and not used, it will show a compile time error.

**Naming**. Lowercase variables are scoped inside the package. Anything that consumes the package cannot and see and work with it. Block scoping also works.

Use PascalCase for exported variables and constants and camelCase for internal.

Naming convention. Use camelcase. When you use acronym, keep it uppercase. myURL. Keep more verbose variable names.

```go
//Type conversion
var k int = int(22)
```

```go
package main

import "fmt"

func main() {
	var i int = 43
	fmt.Printf("%v, %T\n", i, i)

	var j string
	j = string(i)
	fmt.Printf("%v, %T\n", j, j)
}
```

```
43, int
+, string

Program exited.
```

The above just used unicode of that integer value. 

Use strconv package to convert to string types

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var i int = 43
	fmt.Printf("%v, %T\n", i, i)

	var j string
	j = strconv.Itoa(i)
	fmt.Printf("%v, %T\n", j, j)
}
```

```
43, int
43, string

Program exited.
```

1. Boolean types
2. Numeric types
   1. Integers
   2. Floating point
   3. Complex numbers
3. Text types

```go
var n bool = true
fmt.Printf("%v, %T\n", n, n)
```

```go
package main

import (
	"fmt"
)

func main() {
	n := 1 == 1
	m := 1 == 2
	fmt.Printf("%v, %T\n", n, n)
	fmt.Printf("%v, %T\n", m, m)
}

```

```
true, bool
false, bool

Program exited.
```

In go, everytime you initialize a variable, it has a zero value (neat stuff)

```go
package main

import (
	"fmt"
)

func main() {
	var m int
	fmt.Printf("%v, %T\n", m, m)
}
//0, int
```

Zero value for boolean is false

Zero value for numeric types is zero

Zero value for strings is the empty string

Signed integers - int, int8, int16, int32, int64

Unsigned integers - uint8, uint16, uint32

Operators - + - * / %

```go
//Integer division will truncate the decimal part
package main

import (
	"fmt"
)

func main() {
	a := 10
	b := 3
	fmt.Println(a / b)
}

```

```go
//Can't divide different types
package main

import (
	"fmt"
)

func main() {
	var a int16 = 10
	var b int32 = 3
	fmt.Println(a / b)
}
//You have to do type conversions
//fmt.Println(a/int16(b))
```

```
./prog.go:10:16: invalid operation: a / b (mismatched types int16 and int32)

Go build failed.
```

```go
package main

import (
	"fmt"
)

func main() {
	a := 10 //1010
	b := 3 //0011
	fmt.Println(a & b) //0010
	fmt.Println(a | b) //1011
	fmt.Println(a ^ b) //1001
	fmt.Println(a &^ b)//0100
}
```

```
2
11
9
8

Program exited.
```

Bitshifting << and >>

Floating point - float32, float64

```go
package main

import (
	"fmt"
)

func main() {
	a := "hello world"
	fmt.Printf("%v, %T\n", a[2], a[2])
}
```

```
108, uint8

Program exited.
```

Can concatenate strings with +

```go
package main

import (
	"fmt"
)

func main() {
	b := "hello world"
	a := []byte(b)
	fmt.Printf("%v, %T\n", a, a)
}

```

```
[104 101 108 108 111 32 119 111 114 108 100], []uint8

Program exited.
```

**Aliasing a variable**

Defining an alias (an alternate name for a type) >May improve clarity 

``` go
type Celcius float64
type IDNum int
var temp Celcius
var pid IDNum
```

Initializing variables in Declarations

```go
var x int = 100
var x = 100 //(will infer the type automatically)
```

Unitialized variables has a zero value

```go
var x int // x = 0
var x string //x=""
```

Can perform declaration and intialization together with the := operators Variable is declared as type of expression on the right hand side.

```go
x := 100
```



## Data Types & Pointers

Different lengths and signs - int8, int16, int32, int64 (and uint8 etc. etc. for unsigned)

```
var x int
```

A pointer is an adress to some data in memory. & operator returns the address of a variable/function. * operator dereferences - returns the data at that address (much like C). 

```go
var x int = 1
var y int //Default initialize
var ip *int //ip is the pointer to an integer

ip = &x //ip now points to x
y = *ip //y is now 1
```

Alternate way to create a variable

new() function creates a variable and returns a pointer to the variable. Variable is initiialized to zero.

```go
ptr := new(int)
*ptr = 3
```



## Variable Scope

What is scope ? The places in code where variable can be accessed. In go scoping is done through blocks.

A sequence of declarations and statements within matching brackets {} . Including function definitions. Hierarchy of blocks. There are implicit blocks also.

Universe block - all Go source

Package block - all source in a package

File block - all source in a file. a package can have many files. a package block and many file blocks.

"if" ,"for", "switch" - all code inside the statement

Clause in "switch" or "select" - individual clauses, each get a block.

**Lexical scoping**

How variable references are resolved **(variable resolution)**. Go is lexically scoped using blocks.

b(i) >= b(j) if b(j) is defined inside b(i)

"defined inside" is transitive.

Variable is accessible from a block b(j) if - Variable is declared in block(i) , b(i) >= b(j)



## Deallocating Space & Garbage Collection

When a variable is not needed. It should be deallocated.

1. Memory space is made available.

Otherwise, we will eventually run out of memory.

Each call f() creates an integer.(if an integer is declared inside the function). Once the function call ends, you don't need that space.  You need to deallocate. If you dont do that, it is called a memory leak.

**Stack vs Heap**

```go
var x = 4 //Heap

func f(){
	fmt.Printf("%d", x)
}
func g(){
	fmt.Printf("%d", x)
}
```

```go
func f(){
  var x = 4 //Stack
  fmt.Printf("%d", x)
}
func g(){
	fmt.Printf("%d", x)
}
```

Stack is dedicated to function calls.

 	1. Local variables are stored here. Deallocated after function completes. 

Heap on the other hand is the persistent area of memory. Data on heap doesn't go away. You have to explicitly deallocate it. Manual deallocation - Data on heap must be deallocated once it is done being used. In most compiled languages (like C) it is done manually.

```c
//In C, you have to do that manually. Error prone but it is fast.
x = malloc(32);
free(x);
```

**Pointers and Deallocation**

Hard to determine when a variable is no longer in use.

Garbage collection is in interpreted language like Java or Python Interpreter. Keeps track of pointers and and when there are no longer in use. Only when all references are gone.

Easy on the programmer. It is a slow process. 

**Go is special. It is a compiled language and has garbage collection built into it.**

Implementation is fast. Compiler determines stack vs heap.

Garbage collection in the background. Very little performance hit. 

## Types

Different lengths and signs - int8, int16, int32, int64 (and uint8 etc. etc. for unsigned - bigger magnitude)

```
var x int
```

float32 - 6 digits of precision

float64 - 15 digits of precision (more preferred)

```go
var x float64 = 123.45
var y float64 = 1.2345e2
```

Complex numbers

```go
var z complex128 = complex(2,3)
```

**ASCII and Unicode**

ASCII was first one. Each character is associated with an (7) 8-bit number. A=0x41

8-bit codes are sufficient for english.

But not for say for example - chinese

Unicode is 32-bit character code.

UTF-8 is a like a subset of unicode. It is a variable length code.

8 bit UTF-8 codes are same as ASCII. 

Default in Go is UTF-8. Code points - unicode characters. **A Rune** = Code Point in Go

**Strings**

Each byte is a rune representing a UTF-8 code point.

Sequence of arbitrary bytes. 1. Read only and 2.Often meant to be printed

String literal = notated by double quotes. Each characters is a rune - a UTF-8 code point.

**Unicode package**

Runes are divided into many different categories. Provides a set of functions to test categories of runes.

```go
//All Boolean
IsDigit(r rune)
IsSpace(r rune)
IsLetter(r rune)
IsLower(r rune)
IsPunct(r rune)

//Conversions
ToUpper(r rune)
ToLower(r rune)
```

IsSpac

**Strings package**

Functions to manipulate UTF-8 encoded strings.

```go
//String Search Functions
Compare(a,b) //0 , -1, 1
Contains(s, substr)
HasPrefix(s, prefix)
Index(s, substr) //Returns the index of first occurence

//Strings are immutable, but modified strings are returned.
Replace(s, old, new, n) //First n instances to be replaced
TrimSpace(s) //Get rid of spaces
```

Strconv package

Conversions to and from string representation of basic data types

```go
atoi(s)
itoa(i)
FormatFloat //Converts float to string
ParseFloat //Converts string to float
```



## Type Conversions

Most binary operations need operands of the same type. Including assignments.

```go
var x int32 = 1
var y int64 = 2
x = y // Will fail
x = int32(y) // Will work
```

T() operation does the conversions.



## Constants

Expressions whose value is known at compile time.

```go
package main

import (
	"fmt"
)

func main() {
	const myConst int = 23
	fmt.Printf("%v, %T\n", myConst, myConst)
}

```

Replaced by compiler at compile time. Value must be calculable at compile time.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	const myConst float64 = math.Sin(1.57)
	fmt.Printf("%v, %T\n", myConst, myConst)
}

```

```
./prog.go:9:8: const initializer math.Sin(1.57) is not a constant

Go build failed.
```

```go
package main

import (
	"fmt"
)

func main() {
	const a float64 = 1.57
	const b int = 14
	const c bool = true
	fmt.Printf("%v, %T\n", a, a)
	fmt.Printf("%v, %T\n", b, b)
	fmt.Printf("%v, %T\n", c, c)
}
```

```
1.57, float64
14, int
true, bool

Program exited.
```

Collections like arrays etc. cannot be const

Immutable, but can be shadowed.

Can add constant to variables when they are of the same type. 

The first one doesn't work, but the second one works ? Why? It literally takes the constant and replaces with the value.

```go
package main

import (
	"fmt"
)

func main() {
	const a int = 42
	const b int32 = 14
	fmt.Printf("%v, %T\n", a + b, a + b)
}

```

```
./prog.go:10:27: invalid operation: a + b (mismatched types int and int32)

Go build failed.
```

```go
package main

import (
	"fmt"
)

func main() {
	const a = 42
	const b int32 = 14
	fmt.Printf("%v, %T\n", a + b, a + b)
}

```

```
56, int32

Program exited.
```

**iota**

Generate set of related but distinct constants. Often represents a property which has several distinct positive values.

iota is enumerated constant

Special symbol iota allows related constans to be created easily. Iota starts at 0 in each const block and increments by one. Watch out of constant values that match zero values for variables. 

Enumerated expressions - Operations that can be dertermined at compile time are allowed - Arithmetic, Bitwise operations, Bitshifting

```go
package main

import (
	"fmt"
)

const a = iota

func main() {
	fmt.Printf("%v, %T\n", a, a)
}

```

```go
package main

import (
	"fmt"
)

//For example Days of Week or Month
const (
	a = iota
	b = iota
	c = iota
	d = iota
)

func main() {
	fmt.Printf("%v, %T\n", a, a)
	fmt.Printf("%v, %T\n", b, b)
	fmt.Printf("%v, %T\n", c, c)
	fmt.Printf("%v, %T\n", d, d)
}

```

```
0, int
1, int
2, int
3, int

Program exited.
```

```
const (
	a = iota
	b = iota
	c = iota
	d = iota
)
```

Types constants work like immutable variables. Can interoperate only with same type. Untyped constants operate like literals.

```go
type Grades int
const (
	A Grades = iota
	B
	C
	D
	E
)
```

Each constant is assigned to a unique integer. Starts at 1 and increments.



## Arrays & Slices

Key thing about arrays - Arrays are of fixed length. You know it at compile time.

Array Literals

```go
//Array Literal
//... for size in array literal infers size from number of initializers
var x [5]int = [5]{1,2,3,4,5}
```

```go
package main

import (
	"fmt"
)

func main() {
	grades := [3]int{44,55,66}
	//grades := [...]int{44,55,66}
  //var students [3]string
	fmt.Printf("%v\n", grades)
}

```

```
[44 55 66]

Program exited.
```

Arrays are laid contiguous way in memory (like C).

```go
package main

import (
	"fmt"
)

func main() {
	var students [3]string
	fmt.Printf("%v\n", students)
	students[0] = "Aditya"
	students[1] = "Rohit"
	fmt.Printf("%v\n", students)
}
```

```
[  ]
[Aditya Rohit ]

Program exited.
```

```go
package main

import (
	"fmt"
)

func main() {
	var identityMatrix [3][3]int = [3][3]int{ [3]int{1,0,0}, [3]int{0,1,0}, [3]int{0,0,1} }
	fmt.Printf("%v\n",identityMatrix)
}

```

```go
package main

import (
	"fmt"
)

func main() {
	var identityMatrix [3][3]int
	identityMatrix[0] = [3]int{1,0,0}
	identityMatrix[1] = [3]int{0,1,0}
	identityMatrix[2] = [3]int{0,0,1}
	fmt.Printf("%v\n",identityMatrix)
}

```

Go will copy the whole array over. Pass by value

```go
package main

import (
	"fmt"
)

func main() {
	a := [...]int{1,2,3}
	b := a
  //copy by value. use pointers b := &a
	b[1] = 5
	fmt.Println(a)
	fmt.Println(b)
}
```

```
[1 2 3]
[1 5 3]

Program exited.
```

**Iterating through array**

```go
x := [3]{1,2,3}

//Range returns two values - index and element at index
for i,v in range x {
	fmt.Println("%i, %v\n",i,v)
}
```

**Slices**

You don't see slices in other languages. Most of the times slices are used instead of arrays because they are flexible. **Slice is a window into an underlying array.**

Slices are like Arrays but not like Arrays :-P . Slices are reference types unlike arrays.

Variable size, up to the whole array. Two properties of slice

1. Pointer indicates the start of the slice
2. Length is the number of elements in the slice
3. Capacity is the maximum number of elements in the slice.

```go
package main

import (
	"fmt"
)

func main() {
	a := []int{1,2,3,4,5,6,7,8,9,10}
	b := a[:]
	c := a[3:]
	d := a[:6]
	e := a[3:6]

	//All these slices are pointing to the same underlying array
	a[5] = 42

	fmt.Println(a)
	fmt.Println(b)
	fmt.Println(c)
	fmt.Println(d)
	fmt.Println(e)
}

```

```
[1 2 3 4 5 42 7 8 9 10]
[1 2 3 4 5 42 7 8 9 10]
[4 5 42 7 8 9 10]
[1 2 3 4 5 42]
[4 5 42]

Program exited.
```

```go
package main

import (
	"fmt"
)

func main() {
	a := make([]int, 3, 100)
	fmt.Println(a)
	fmt.Println(len(a))
	fmt.Println(cap(a))
}

```

```
[0 0 0]
3
100

Program exited.
```

Underlying arrays.

```go
package main
import (
	"fmt"
)

func main() {
	a := []int{1,2,3}
	fmt.Println(a)
	fmt.Println(len(a))
	fmt.Println(cap(a))
}
```

```
[1 2 3]
3
3

Program exited.
```

```go
arr := [...]string{"a","b","c","d","e","f","g"}
s1 := {1,3}
s2 := {2,5}
```

len() and cap() - length and capacity of a slice.

writing to a slice writes the underlying array. Overlapping slices can point to same elements in the underlying arrays.

**Slice literals**

Can be used to initialize a slice. Creates the underlying array and creates a slice to reference it. Slice points to the start of the array. Length is the capacity. Slice will refer to the entire underlying array.

```go
sli := []int{1,2,3}
```

**Make**

Create a slice (and array) using

```go
//2 argument version - specify type and length/capacity
sli := make([]int , 10)

//3 argument version - specify length and capacity (15 is capacity)
sli := make([]int, 10, 15)
```

Size of the slice can be increased by the append function. Adds elements to the end of the slice. Inserts into underlying array. Increases the size of the array if necessary (there is a time penalty though).

```go
sli = make([]int, 0 , 3)
sli = append(sli,100)
```



## Maps

Map is golang implementation of Hash Table

```go
var idMap map[string]int
idMap = make(map[string]int)
```

Map Literal

```go
idMap := map[string]int{"aditya":123, "rohit":234}
```

Accessing

```go
fmt.Println(idMap["aditya"])
```

Adding or editing

```go
idMap["jane"] = 126
```

Delete

```go
delete(idMap,"aditya")
```

Two value assignment tests for existence of the key

```go
//id = value, p will be boolean = true if the key is in the map
id,p := idMap["joe"]
```

len() returns the number of key value pairs in the map

iterate through the map

```go
for key, val := range idMap{
	fmt.Println(key, val)
}
```



## Struct

Aggregate data type. 

```go 
type Person struct{
	name string
	addr string
	phone string
}
var p1 Person
p1.name = "Aditya"
p2 := new(Person) //All initialized to zero-values

type Point struct {x, y, z float}
```

Struct Literal

```go
p1 := Person (name: "Joe", addr: "Chhatarpur", phone: "123")
```





## Control Flow

```go
if x % 2 == 0 {
	fmt.Println("Even")
} else {
  fmt.Println("Odd")
}
```

```go
//No need to put a break like C. It will automatically break
switch x{
	case 1: 
		fmt.Println("Case1")
	case 2: 
		fmt.Println("Case2")
	default: 
		fmt.Println("Default")
}
```

```go
//Tagless switch. First case whose expression which evaluates to boolean.
switch {
	case x == 1:
		fmt.Println("Case1")
	case x == 2:
		fmt.Println("Case2")
	case default:
		fmt.Println("Default")
}
```

Break and continue are also control flow much like C.



## Scan

Scan reads user input. Takes a pointer as an argument. Typed data is written to pointer. Returns the number of scanned items.

```go
var appleNum int
fmt.Printf("Number of apples ?")
num, err := fmt.Scan(&appleNum)
fmt.Printf(appleNum)
```



## JSON

JSON Mashalling - generating JSON representation from an object.

```go
p1 := Person(name : "joe", addr : "c245", phone : "222")
barr, err := json.Marshal(p1)
```

Marshal() returns JSON representation as []byte

Unmarshalling

```go
var p2 Person
err := json.Unmarshal(barr, &p2)
```



## File

```go
//dat is a []byte filled with contents of entire file.
//Explicit open/close is not needed
//Can be an issue with large files.
dat , e := ioutil.ReadFile("test.txt")

//Write file
dat = "Hello World"
err := ioutil.WriteFile("outfile.txt", dat, 0777)
```

os package

os.open() - opens a file and returns a file descriptor

os.close() - closes the file

os.read() - reads from a file into a []byte

Fills the byte array. Control the amount you want to read.

```go
//Reads and fills barr
//Read, returns the number of bytes read
//May be less than []byte length
f, err := os.Open("data.txt")
barr :=  make([]byte, 10)
nb, err := f.Read(barr)
f.Close()
```

```go
f, err := os.Create("outfile.txt")
barr := []{1,2,3}
nb, err := f.Write(barr)
nb, err := f.WriteString("Hi")
```

WriteString() - writes a string

Write() - Writes a byte array - any unicode sequence



## Functions & Closures

Call by value mostly. Copied. Modifying parameters has no effect outside the function.

In case of arrays, copy will take lots of space and time. **(Hint : use slices instead of doing it this way)**

```go
func foo(x [3]int) int {
	return x[0]
}
func main(){
	a := [3]int{1,2,3}
	fmt.Println(foo(a))
}
```

```go
func foo(x *[3]int) int {
  (*x)[0] = (*x)[0] +1
}
func main(){
	a := [3]int{1,2,3}
  foo(&a)
  fmt.Println(a)
}
```

^^ Not a good way to do it. Use slices instead.

Slices contains pointer to the array. Passing slice copies the pointer.

```go
func foo(sli int) int {
	sli[0] = sli[0] + 1
}
func main(){
	a := []int{1,2,3}
  foo(a)
	fmt.Println(a)
}
```

**First class functions**

```go
var funcVar func(int) int
func incFn (x int) int {
	return x + 1
}
func main(){
	funcVar = incFn //No parenthesis
	fmt.Println(funcVar(1))
}
```

Function can be passed to another function as an argument

```go
func applyIt(afunct func (int) int), val int) int {
	return afunct(val)
}

func incFn(x int) int {return x + 1}
func decFn(x int) int {return x - 1}

func main(){
  fmt.Println(applyIt(incFn, 2))
  fmt.Println(applyIt(decFn, 2))
}
```

**Anonymous Function**

```go
func main(){
	v := applyIt(func (x int) int {return x + 1}, 2)
	fmt.Println(v)
}
```

**Returning Function**

```go
func MakeDistOrigin(o_x, o_y float64) func (float64, float64) float64 {
		fn := func (x, y float64) float64 {
			return math.Sqrt(math.Pow(x-o_x, 2) + math.Pow(y -o_y, 2)) 
		}
		return fn
}
func main(){
  Dist1 := MakeDistOrigin(0,0)
  Dist2 := MakeDistOrigin(2,2)
  fmt.Println(Dist1(2,2))
  fmt.Println(Dist2(2,2))
}
```

Environment of a function - set of all names that are valid inside the function. Names defined locally, in the function. Lexical scoping. 

**Closure = Function + its environment**

When functions are passed or returned, their environment comes with them.

Variable number of arguments. Use ellipsis. Treated as a slice inside function.

```go
func getMax (vals ...int) int {
	maxV := -1
	for _, v := range vals {
		if v > maxV {
			maxV = v
		}
	}
	return maxV
}

//Can pass a slice to a variadic function
func main(){
  fmt.Println(getMax(1,2,3,4))
  vslice := []int{1,3,4,5}
  fmt.Println(getMax(vslice...))
}
```

Deferred function calls - call be deferred until the surrounding function completes. Typically used for cleanup activites. 

```go
func main(){
	defer fmt.Println("Bye!")
	fmt.Println("Hello!")
}
```

Arguments of a deferred function call are evaluated immediately.



## OOP

Golang does not have classes but it enables same features. First we do brief overview of OOP

**Classes**

Collection of data fields and functions that share a well-defined responsibility

Example: **Point** class

Used in a geometry program

Data: x coordinate, y coordinate

Functions: DistToOrigin(), Quadrant()AddXOffset(), AddYOffset()SetX(), SetY()

Classes are a **template**

Contain **data fields**, not data

**Object**

Instance of a class

Contains real data

Example: Point class …. actual data

**Encapsulation**

Data can be protected from the programmer

Data can be accessed only using methods

Maybe we **don’t trust the programmer** to keep data consistent

Example: Double distance to origin

Option 1: Make method DoubleDist()

Option 2: Trust programmer to double X and Y directly



## OOP In Go

**No “Class” Keyword in Go**

Most OO languages have a class keyword

Data fields and methods are defined inside a class block.

**Associating Methods with Data**

Method has a **receiver type** that it is associated with. Use dot notation to call the method

```go
type MyInt int  //My own type. The type should be defined in the same package.

func (mi MyInt) Double () int {
	return int(mi*2)
}
func main() {
	v := MyInt(3)
	fmt.Println(v.Double())
}
```

**Implicit Method Argument**

```go
func (mi MyInt) Double () int {
	return int(mi*2)
}
func main() {
	v := MyInt(3)
	fmt.Println(v.Double())
}
```

Object v is an implicit argument to the method

Call by value

**Structs, again**

Struct types compose data fields

```go
type Point struct { 
	x float64
	y float64
} 
```

Traditional feature of classes

**Structs with Methods**

**Structs and methods** together allow arbitrary data and functions to be composed

```go
func (p Point) DistToOrig() {
   t := math.Pow(p.x, 2) + 		math.Pow(p.y, 2)
   return math.Sqrt(t)
}
func main() {
   p1 := Point(3, 4)
   fmt.Println(p1.DistToOrig())
}
```

**Encapsulation in Go**

Making data fields or methods hidden from the programmer

Might use a private keyword in another language

Example: Point struct, Scale() method

Scale() should multiply x and y coordinates by a constant

Don’t trust this to the programmer

1. Might scale one coordinate but not the other

2. Coordinates could become inconsistent

3. Need to **hide x and y coordinates**

**Hiding in a Package**

Go can only hide data/methods in a package

Variables/functions are only exported if their names start with a **capital letter**

```go
package data
var x int = 1
var Y int = 2
```

```go
package main
import “data"
func main() {
	fmt.Println(Y)
	fmt.Println(x)
}
```

**Controlling Access to** **Structs**

Hide fields of structs by starting field name with a lower-case letter

```go
package data
type Point struct { 
	x float64
	y float64
} 
func (p *Point) InitMe(xn, yn float64) {
	p.x = xn
	p.y = yn
}
```

Need InitMe() to assign hidden data fields

Define public methods which access hidden data

```go
func (p *Point) Scale(v float64) {
	p.x = p.x * v
	p.y = p.y * v
}
func (p *Point) PrintMe(){
	fmt.Println(p.x, p.y)
}
```

Access to hidden fields only through public methods

```go
package main
func main() {
	var p data.Point
	p.InitMe(3, 4)
	p.Scale(2)
	p.PrintMe()
}
```

**Limitations of Methods**

Receiver is passed implicitly as an argument to the method

Method cannot modify the data inside the receiver. It is passed by value.

Example: OffsetX() should increase x coordinate

```go
func main() {
   p1 := Point(3, 4)
   p1.OffsetX(5)
}
```

**Large Receivers**

If receiver is large, lots of copying is required

**Pointer Receivers**

Receiver can be a pointer to a type

Call by reference, pointer is passed to the method

```go
func (p *Point) OffsetX(v float64) {
	p.x = p.x + v
}
```

**No Need to Dereference**

Point is referenced as p, not *p

Dereferencing is automatic with . operator 

```go
func (p *Point) OffsetX(v int) {
	p.x = p.x + v
}
```

**No Need to Reference**

Do not need to reference when calling the method

```go
func main() {
	p := Point{3, 4}
	p.OffsetX(5)
	fmt.Println(p.x)
}
```

**Using Pointer Receivers**

Good programming practice:

1. All methods for a type have **pointer receivers**, or

2. All methods for a type have **non-pointer receivers**

Mixing pointer/non-pointer receivers for a type will get confusing

Pointer receiver allows modification

## Polymorphism, Inheritance & Overriding

Ability for an object to have different “forms” depending on the context

Example: Area() function

1. Rectangle, **area = base \* height**

2. Triangle, **area = 0.5 \* base \* height**

**Identical** at a high level of abstraction

**Different** at a low level of abstraction

**Inheritance** 

Golang does not have inheritance.

Subclass inherits the methods/data of the superclass

Example: **Speaker** superclass

Speak() method, prints “<noise>”

Subclasses **Cat** and **Dog**

Also have the Speak() method

Cat and Dog are different forms of Speaker

**Overriding**

Subclass **redefines a method** inherited from the superclass

Example: Speaker, Cat, Dog

Speaker Speak() prints “<noise>”

Cat Speak() prints “meow”

Dog Speak() prints “woof”

Speak() is polymorphic

Different implementations for each class

Same **signature** (name, params, return)



## Interfaces in Go

Set of **method signatures**

Name, parameters, return values

Implementation is NOT defined

Used to express conceptual similarity between types

Example: **Shape2D interface**

All 2D shapes must have Area() and Perimeter()

**Satisfying an Interface**

Type **satisfies an interface** if type defines all methods specified in the interface

Same method signatures

**Rectangle** and **Triangle** types satisfy the **Shape2D** interface

Must have Area() and Perimeter() methods

Additional methods are OK

*Similar to inheritance with overriding*

**Defining an Interface Type**

```go
type Shape2D interface {
   Area() float64
   Perimeter() float64
}
type Triangle {…}
func (t Triangle) Area() float64 {…}
func (t Triangle) Perimeter() float64 {…} 
```

Triangle type satisfies the Shape2D interface

No need to state it explicitly

## **Concrete vs Interface Types**

**Concrete Types**

Specify the exact representation of the data and methods

Complete method implementation is included

**Interface Types**

Specifies some method signatures

Implementations are abstracted

**Interface Values**

Can be treated like other values

Assigned to variables

Passed, returned

Interface values have two components

1.**Dynamic Type**: Concrete type which it is assigned to

2.**Dynamic Value**: Value of the dynamic type

Interface value is actually a pair 

**(dynamic type, dynamic value)** 

**Defining an Interface Type**

```go
type Speaker interface {Speak ()}

type Dog struct {name string}
func (d Dog) Speak() {
	fmt.Println(d.name)
}
func main() {
	var s1 Speaker
	var d1 Dog{“Brian”}
	s1 = d1
	s1.Speak()
}
```

Dynamic type is Dog, Dynamic value is d1

**Interface with Nil Dynamic Value**

An interface can have a nil dynamic value

```go
var s1 Speaker
var d1 *Dog
s1 = d1
```

d1 has no concrete value yet

s1 has a dynamic type but no dynamic value

**Nil Dynamic Value**

Can still call the Speak() method of s1

Doesn’t need a dynamic value to call

Need to check inside the method

```go
func (d *Dog) Speak() {
	if d == nil {
		fmt.Println(“<noise>”)
	} else {
		fmt.Println(d.name)
	}
}
var s1 Speaker
var d1 *Dog
s1 = d1
s1.Speak()
```

**Nil Interface Value**

Interface with **nil dynamic type**

Very different from an interface with a **nil dynamic value**

**Nil dynamic value** and **valid dynamic type**

Can call a method since type is known

```go
var s1 Speaker
var d1 *Dog
s1 = d1
```

**Nil dynamic type**

Cannot call a method, runtime error

```go
var s1 Speaker
```

## **Ways to Use an Interface**

Need a function which takes multiple types as a parameter

Function foo() parameter

1. Type X or type Y

Define interface Z

foo() parameter is interface Z

Types X and Y satisfy Z

Interface methods must be those needed by foo()

**Pool in a yard**

I need to put a pool in my yard

Pool needs to fit in my yard

1. Total area must be limited

Pool needs to be fenced

1. Total perimeters must be limited

Need to determine if a pool shape satisfies criteria

**FitInYard****()**

1. Takes a shape as a argument

2. Returns true if the shape satisfies criteria

Many possible shape types

1. Rectangle, triangle, circle, etc.

FitInYard() should take many shape types

Valid shape types must have:

1. Area()
2. Perimeter()

Any shape with these methods is OK

**Interface for Shapes**

```go
type Shape2D interface {
   Area() float64
   Perimeter() float64
}
type Triangle {…}
func (t Triangle) Area() float64 {…}
func (t Triangle) Perimeter() float64 {…}
type Rectangle {…}
func (t Rectangle) Area() float64 {…}
func (t Rectangle) Perimeter() float64 {…}  
```

Rectangle and Triangle satisfy Shape2D interface

**FitInYard****() Implementation**

```go
func FitInYard(s Shape2D) bool {
	if (s.Area() < 100 && 
	    s.Perimeter() < 100) {
		return true
	}
	return false
}
```

Parameter is any type that satisfies the interface

Empty interface specifies no methods

All types satisfy the empty interface

Use it to have a function accept any type as a parameter

```go
func PrintMe(val interface{}) {
	fmt.Println(val)
}
```

**Concealing Type Differences**

Interfaces hide the differences between types

```go
func FitInYard(s Shape2D) bool {
	if (s.Area() < 100 && 
	    s.Perimeter() < 100) {
		return true
	}
	return false
}
```

Sometimes you need to treat different types in different ways

**Exposing Type Differences**

Example: Graphics program

**DrawShape****()** will draw any shape

1. func DrawShape(s Shape2D) { …

Underlying API has different drawing functions for each shape

1. func DrawRect(r Rectangle) { …
2. func DrawTriangle(t Triangle) { …

Concrete type of shape s must be determined

**Type Assertions**

Type assertions can be used to determine and extract the underlying concrete type

```go
func DrawShape(s Shape2D) bool {
	rect, ok := s.(Rectangle)
```

Type assertion extracts Rectangle from Shape2D

1. Concrete type in parentheses

If interface contains concrete type

1. rect == concrete type, ok == true

If interface does not contain concrete type

1. rect == zero, ok == false

**Type Assertions for Disambiguation**

```go
func DrawShape(s Shape2D) bool {
	rect, ok := s.(Rectangle)
	if ok {
		DrawRect(rect)
	}
	tri, ok := s.(Triangle)
	if ok {
		DrawTriangle(tri)
	}
}
```

**Type Switch**

Switch statement used with a type assertion

```go
func DrawShape(s Shape2D) bool {
	switch sh := s.(type) {
	case Rectangle:
		DrawRect(sh)
	case Triangle:
		DrawTriangle(sh)
	}
}
```

**Error Interface**

Many Go programs return error interface objects to indicate errors

```go
type error interface { 
	Error() string 
} 
```

Correct operation: error == nil

Incorrect operation: Error() prints error message

**Handling Errors**

Check whether the error is nil

If it is not nil, handle it

```go
f, err := os.Open(“/harris/test.txt”)
if err != nil {
	fmt.Println(err)
	return
}
```

fmt package calls the Error() method to generate string to print

## One More Interface Example

```go
// _Interfaces_ are named collections of method
// signatures.

package main

import "fmt"
import "math"

// Here's a basic interface for geometric shapes.
type geometry interface {
    area() float64
    perim() float64
}

// For our example we'll implement this interface on
// `rect` and `circle` types.
type rect struct {
    width, height float64
}
type circle struct {
    radius float64
}

// To implement an interface in Go, we just need to
// implement all the methods in the interface. Here we
// implement `geometry` on `rect`s.
func (r rect) area() float64 {
    return r.width * r.height
}
func (r rect) perim() float64 {
    return 2*r.width + 2*r.height
}

// The implementation for `circle`s.
func (c circle) area() float64 {
    return math.Pi * c.radius * c.radius
}
func (c circle) perim() float64 {
    return 2 * math.Pi * c.radius
}

// If a variable has an interface type, then we can call
// methods that are in the named interface. Here's a
// generic `measure` function taking advantage of this
// to work on any `geometry`.
func measure(g geometry) {
    fmt.Println(g)
    fmt.Println(g.area())
    fmt.Println(g.perim())
}

func main() {
    r := rect{width: 3, height: 4}
    c := circle{radius: 5}

    // The `circle` and `rect` struct types both
    // implement the `geometry` interface so we can use
    // instances of
    // these structs as arguments to `measure`.
    measure(r)
    measure(c)
}
```



## GoRoutines

One goroutine is created automatically to execute the main(). Other goroutines are created using the **go** keyword. 

```go
a = 1
go foo()
a = 2
```

New goroutine created for foo(). Main goroutine does not block. 

A goroutine exits **when its code is complete**

When the main goroutine is complete, all other goroutines exit

A goroutine may not complete its execution because main completes early

```go
func main() {
	go fmt.Printf("New routine")
	fmt.Printf("Main routine")
}
```

Only “**Main routine**” is printed

Main finished before the new goroutine started

```go
func main() {
   go fmt.Printf("New routine")
   time.Sleep(100 * time.Millisecond)
   fmt.Printf("Main routine")
}
```

Add a delay in the main routine to give the new routine a chance to complete

“**New** **RoutineMain** **Routine**” is now printed

Timing with goroutines

Adding a delay to wait for a goroutine is **bad**!

Timing assumptions may be wrong

1. Assumption: delay of 100 ms will ensure that goroutine has time to execute

2. Maybe the OS schedules another thread

3. Maybe the Go Runtime schedules another goroutine

Timing is nondeterministic

Need formal **synchronization** constructs

## Synchronization

Using **global events** whose execution is viewed by all threads, simultaneously

Sync Waitgroup

Sync package contains functions to synchronize between goroutines

**sync.WaitGroup** forces a goroutine to wait for other goroutines

Contains an internal counter

1. Increment counter for each goroutine to wait for

2. Decrement counter when each goroutine completes

3. Waiting goroutine cannot continue until counter is 0

```go
func foo(wg *sync.WaitGroup) {
   fmt.Printf("New routine")
   wg.Done()
}
func main() {
   var wg sync.WaitGroup
   wg.Add(1)
   go foo(&wg)
   wg.Wait()
   fmt.Printf("Main routine")
}
```

Goroutines usually work together to perform a bigger task

Often need to send data to collaborate

Example: Find the product of 4 integers

Make 2 goroutines, each multiplies a pair

Main goroutine multiplies the 2 results

Need to send ints from main routine to the two sub-routines

Need to send results from sub-routines back to main routine

## Channels

Transfer data between goroutines

Channels are typed

Use make() to create a channel

**c := make(**chan **int**)

Send and receive data using the **<-** operator

Send data on a channel

**c** **<-** **3**

Receive data from a channel

**x :=** **<-** **c**

```go
func prod(v1 int, v2 int, c chan int) {
	c <- v1 * v2}
func main() {
	c := make(chan int)
	go prod(1, 2, c)
	go prod(3, 4, c)
	a := <- c
	b := <- c
	fmt.Println(a*b)
}
```

Unbuffered channels cannot hold data in transit

Default is unbuffered

Sending blocks until data is received

Receiving blocks until data is sent

Channel communication is synchronous

Blocking is the same as waiting for communication

Receiving and ignoring the result is same as a Wait()

**Channel Capacity**

Channels can contain a limited number of objects

Default size 0 (unbuffered)

**Capacity** is the number of objects it can hold in transit

Optional argument to  make()defines channel capacity

**c := make(****chan** **int****,** **3****)**

Sending only blocks if **buffer is full**

Receiving only blocks if **buffer is empty**

Sender and receiver do not need to operate at exactly the same speed

Speed mismatch is acceptable

Average speeds must still match

**Iterating Through a Channel**

Common to iteratively read from a channel

```go
for i := range c {
   fmt.Println(i)
}
```

Continues to read from channel c

One iteration each time a new value is received

i is assigned to the read value

Iterates when sender calls **close(c)**

Multiple channels may be used to receive from multiple sources

Data from both sources may be needed

Read sequentially

```go
	a := <- c1
	b := <- c2
	fmt.Println(a*b)
```

May have a choice of which data to use

i.e. First-come first-served

Use the **select** statement to wait on the first data from a set of channels

```go
select {
   case a = <- c1:
      fmt.Println(a)
   case b = <- c2:
      fnt.Println(b)	
}
```

May select either send or receive operations

```go
select {
   case a = <- inchan:
      fmt.Println(“Received a”)
   case outchan <- b:
      fnt.Println(“sent b”)	
}
```

May want to receive data until an **abort signal** is received

Use select with a **separate abort channel**

```go
for {
   select {
      case a <- c:
         fmt.Println(a)
      case <-abort:
         return
   }
}
```

May want a default operation to avoid blocking

```go
select {
   case a = <- c1:
      fmt.Println(a)
   case b = <- c2:
      fmt.Println(b)
   default:
      fmt.Println(“nop”)	
}
```

## Mutexs

Sharing variables concurrently can cause problems

Two goroutines writing to a shared variable can interfere with each other

**Concurrency-Safe**

Function can be invoked concurrently without interfering with other goroutines

```go
// Two goroutine write to i. i should equal 2
var i int = 0
var wg sync.WaitGroup
func inc() {
   i = i + 1
   wg.Done()}
func main() {
wg.Add(2)
   go inc()
   go inc()
   wg.Wait()
   fmt.Println(i)
}
```

Don’t let 2 goroutines write to a shared variable at the same time!

Need to restrict possible interleavings

Access to shared variables cannot be interleaved

**Mutual Exclusion**

Code segments in different goroutines which cannot execute concurrently

Writing to shared variables should be mutually exclusive

A Mutex ensures mutual exclusion

Uses a **binary semaphore**

Flag up – shared variable is in use

Flag down – shared variable is available

**Lock()** method puts the flag up

Shared variable in use

If lock is already taken by a goroutine, Lock() blocks until the flag is put down

**Unlock()** method puts the flag down

Done using shared variable

When Unlock() is called, a blocked Lock() can proceed

Increment operation is now mutually exclusive

```go
var i int = 0
var mut sync.Mutex
func inc() {
   mut.Lock()
   i = i + 1
   mut.Unlock()
}
```

## Once Syncronization

**Initialization** 

must happen once

must happen before everything else

How do you perform initialization with multiple goroutines?

Could perform initialization before starting the goroutines

Has one method, once.Do(f)

Function f is executed only one time

Even if it is called in multiple goroutines

All calls to once.Do() block until the first returns

Ensures that initialization is executes first

```go
var wg sync.WaitGroup

func main() {
   wg.Add(2)
   go dostuff()
   go dostuff()
   wg.Wait()
}
```

Make two goroutines, initialization only once

Each goroutine executes dostuff()

**setup()** should execute only once

“hello” should not print until **setup()** returns

```go
var on sync.Once
func setup() {
	fmt.Println("Init")
}
func dostuff() {
	on.Do(setup)
	fmt.Println("hello")
	wg.Done()
}
```

**Init** appears only once

**Init** appears before **hello** is printed

## Deadlocks

**Circular dependencies** cause all involved goroutines to block

G1 waits for G2

G2 waits for G1

Can be caused by waiting on channels

```go
func dostuff(c1 chan int, c2 chan int) {
   <- c1
   c2 <- 1
   wg.Done()
}
```

Read from first channel

Wait for write onto first channel

Write to second channel

Wait for read from second channel

```go
func main() {
   ch1 := make(chan int)
   ch2 := make(chan int)
   wg.Add(2)
   go dostuff(ch1, ch2)
   go dostuff(ch2, ch1)
   wg.Wait()
}
```

dostuff() argument order is swapped

Each goroutine blocked on channel read

Golang runtime automatically detects when all goroutines are deadlocked 

Cannot detect when a subset of goroutines are deadlocked