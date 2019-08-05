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

**Runes**

