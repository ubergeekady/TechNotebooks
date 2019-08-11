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



## Data Types & Pointers

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