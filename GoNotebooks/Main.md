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

[**TODO : Runes etc**]



## Constants

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

**[TODO : More about this]**





## Arrays & Slices

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

Slices are like Arrays but not like Arrays :-P

Slices are reference types unlike arrays.

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

