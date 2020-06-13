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

