All the source files for go should be located in a directory named src inside the workspace. So lets create directory src inside the go directory we created above. Every go project should in turn have its own subdirectory inside src. Lets create a directory hello inside src to hold the hello world project. The directory structure should look like the one below after creating the above directories.

```
        go
          src
            hello
```

Save the following program as helloworld.go in the hello directory we just created.

```go
package main

import "fmt"

func main() {  
    fmt.Println("Hello World")
}
```

```
go run ./src/hello/helloworld.go
go build
```

READMORE: GoPath

**Variables**

```
    var age int // variable declaration
    fmt.Println("my age is", age)
    
    var age int // variable declaration
    fmt.Println("my age is ", age)
    age = 29 //assignment
    
    var age int = 29 // variable declaration with initial value
    fmt.Println("my age is", age)
    
    var width, height int = 100, 50 //declaring multiple variables
    fmt.Println("width is", width, "height is", height)
    
    var width, height = 100, 50 //"int" is dropped
    fmt.Println("width is", width, "height is", height)
    
    var (
        name   = "naveen"
        age    = 29
        height int
    )
    fmt.Println("my name is", name, ", age is", age, "and height is", height)
    
    name, age := "naveen", 29 //short hand declaration
    fmt.Println("my name is", name, "age is", age)
```

Short hand syntax can only be used when at least one of the variables in the left side of := is newly declared.

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

byte is an alias of uint8
rune is an alias of int32

Strings are a collection of bytes in golang. It's alright if this definition doesn't make any sense. For now we can assume a string to be a collection of characters.

The above code is perfectly legal in C language. But in the case of go, this wont work. i is of type int and j is of type float64. We are trying to add 2 numbers of different types which is not allowed. When you run the program, you will get main.go:10: invalid operation: i + j (mismatched types int and float64)