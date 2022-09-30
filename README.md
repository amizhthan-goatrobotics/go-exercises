# Go Exercises

:information_source: &nbsp;This repo contains questions and exercises to learn and practice Golang

:bar_chart: &nbsp;There are currently **37** exercises and questions

- [Go Exercises](#go-exercises)
  - [Exercises](#exercises)
    - [Hello World](#hello-world)
    - [Strings](#strings)
    - [Arrays](#arrays)
    - [Loops](#loops)
    - [Functions](#functions)
  - [Questions](#questions)
    - [Go 101](#go-101)
    - [Variables & Data Types](#variables--data-types)
    - [User Input](#user-input)
    - [Arrays](#arrays-1)
    - [Functions](#functions-1)
  - [Projects](#projects)

## Exercises

### Hello World

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Hello World! | [Exercise](exercises/hello_world/exercise.md) | [Solution](exercises/hello_world/main.go) | |
| Variables & Constants | [Exercise](exercises/variables/exercise.md) | [Solution](exercises/variables/main.go) | |
| Arithmetic Operators | [Exercise](exercises/arithmetic_operators/exercise.md) | [Solution](exercises/arithmetic_operators/main.go) | |
| Data Types | [Exercise](exercises/data_types/exercise.md) | [Solution](exercises/data_types/solution.md) | |
| User Input | [Exercise](exercises/user_input/exercise.md) | [Solution](exercises/user_input/main.go) | |
| Packages | [Exercise](exercises/packages/exercise.md) | [Solution](exercises/packages/main.go) | 


### Strings

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Split Strings | [Exercise](exercises/split_strings/exercise.md) | [Solution](exercises/split_strings/solution.md) | |

### Arrays

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Arrays 101 | [Exercise](exercises/arrays_101/exercise.md) | [Solution](exercises/arrays_101/solution.md) | |
| Slices 101 | [Exercise](exercises/slices_101/exercise.md) | [Solution](exercises/slices_101/solution.md) | |

### Loops

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Loops 101 | [Exercise](exercises/loops_101/exercise.md) | [Solution](exercises/loops_101/main.go) | |
| Loops 102 | [Exercise](exercises/loops_102/exercise.md) | [Solution](exercises/loops_102/main.go) | |
| Continue | [Exercise](exercises/continue/exercise.md) | [Solution](exercises/continue/main.go) | |

### Functions

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Functions 101 | [Exercise](exercises/functions_101/exercise.md) | [Solution](exercises/functions_101/solution.md) | |
| Named Return Values | [Exercise](exercises/named_return_values/exercise.md) | [Solution](exercises/named_return_values/solution.md) | |


## Questions

### Go 101

<details>
<summary>What are some characteristics of the Go programming language?</summary><br><b>

  * Strong and static typing - the type of the variables can't be changed over time and they have to be defined at compile time
  * Simplicity
  * Fast compile times
  * Built-in concurrency
  * Garbage collected
  * Platform independent
  * Compile to standalone binary - anything you need to run your app will be compiled into one binary. Very useful for version management in run-time.
  * Big community
</b></details>

<details>
<summary>True or False?

  * In Go we can redeclare variables
  * Once a variable declared, we must use it
</summary>

* False
* True
</b></details>

<details>
<summary>What libraries of Go have you used?</summary><br><b>

This should be answered based on your usage but some examples are:

  * fmt - formatted I/O
  * math - random numbers, arithmetic operations like square, etc.
  * time - for any time related operation

</b></details>

<details>
<summary>Why some functions and packages in Go begin with a Capital letter?</summary><br><b>

Any exported variable, function, ... begins with a capital letter. In fact when using a package, you can use only the things the package exports for you and others to use.
</b></details>

### Variables & Data Types

<details>
<summary>Demonstrate short and regular variable declaration</summary><br><b>

```Go
package main

import "fmt"

func main() {
  x := 2
  var y int = 2

  fmt.Printf("x: %v. y: %v", x, y)
}
```
</b></details>

<details>
<summary>What is the result of the following program?

```
package main

import "fmt"

func main() {
    var userName
    userName = "user"
    fmt.Println(userName)
}
```
</summary><br><b>

Error. The type userName is not defined. It has to be declared or the value assignment should happen at declaration.

So both `var userName = user` and `var userName string` are valid.

</b></details>

<details>
<summary>What is the result of the following program?

```Go
package main
 
import "fmt"
 
func main() {
    var x uint
    x = -3
    // comment!
    fmt.Println(x)
}
```
</summary><br><b>

Error. When `x` is declared as `uint` it means you can't put any negative values. But because we did put a negative value (`-3`) it will fail to compile it.
</b></details>

<details>
<summary>What is the problem with the following block of code? How to fix it?

```
func main() {
    var x float32 = 13.5
    var y int
    y = x
}
```
</summary><br><b>
</b></details>

<details>
<summary>What is the difference between <code>var x int = 2</code> and <code>x := 2</code>?</summary><br><b>

The result is the same, a variable with the value 2.

With <code>var x int = 2</code> we are setting the variable type to integer, while with <code>x := 2</code> we are letting Go figure out by itself the type.
</b></details>

<details>
<summary>The following block of code tries to convert the integer 101 to a string but instead we get "e". Why is that? How to fix it?

```
package main

import "fmt"

func main() {
    var x int = 101
    var y string
    y = string(x)
    fmt.Println(y)
}
```
</summary><br><b>

It looks what unicode value is set at 101 and uses it for converting the integer to a string.
If you want to get "101" you should use the package "strconv" and replace <code>y = string(x)</code> with <code>y = strconv.Itoa(x)</code>
</b></details>

<details>
<summary>What is wrong with the following code?:

```Go
package main

func main() {
    var x = 2
    var y = 3
    const someConst = x + y
}
```
</summary><br><b>
Constants in Go can only be declared using constant expressions.
But `x`, `y` and their sum is variable.
<br>
<code>const initializer x + y is not a constant</code>

</b></details>

<details>
<summary>What would be the result of executing the following code:

```Go
package main

import "fmt"

x := 2

func main() {
    x = 3
    fmt.Println(x)
}
```
</summary><br><b>

It will fail with `expected declaration, found x` as outside of a function, every statement should start with a keyword (and short variable declarations won't work).
</b></details>

<details>
<summary>Demonstrate a block of variable declarations (at least 3 variables)</summary><br><b>

```Go
package main

import "fmt"

var (
  x bool   = false
  y int    = 0
  z string = "false"
)

func main() {
  fmt.Printf("The type of x: %T. The value of x: %v\n", x, x)
  fmt.Printf("The type of y: %T. The value of y: %v\n", y, y)
  fmt.Printf("The type of z: %T. The value of z: %v\n", y, y)
}
```
</b></details>


### User Input

<details>
<summary>Fix the following program to get an input from the user regarding his name and print it

```Go
var name string

fmt.Scan(name)

fmt.Println(name)
```
</summary><br><b>

```Go
var name string

fmt.Scan(&name)

fmt.Println(name)
```

</b></details>

<details>
<summary>Why when asking for user input, we have to specify &?</summary><br><b>

Because we want to reference the memory address of the variable, this is where the user input will be stored.
</b></details>

<details>
<summary>What do we print here?

```Go
var age int = 3

fmt.Println(age)
fmt.Println(&age)
```
</summary><br><b>

The value of `age` variable and then the memory location of `age` variable

</b></details>

### Arrays

<details>
<summary>Define an array of the following colors: red, green and blue</summary><br><b>

```Go
var rgb = [3]string{"red", "green", "blue"}
```
</b></details>

<details>
<summary>You defined the following array and printed it. What was the output? <code>var numbers = [10]int{}</code></summary><br><b>

```Go
[0 0 0 0 0 0 0 0 0 0]
```
</b></details>

### Functions

<details>
<summary>Define a function that prints "Hello World"</summary><br><b>

```Go
func PrintHelloWorld() {
  fmt.Println("Hello World")
}
```
</b></details>

<details>
<summary>What the following code does?

```Go
func add(x int, y int) int {
  return x + y
}
```
</summary><br><b>

add is a function that takes two parameters (two integers) and returns their sum.
</b></details>

<details>
<summary>Which of the following functions will work just fine?

```Go
func add(x int, y int) int {
  return x + y
}

func add(x, y int) int {
  return x + y
}
```
</summary><br><b>

Both. If two or more parameters share the same type, you can specify it only once.
</b></details>

<details>
<summary>Write code that will execute the following function in a valid way

```Go
func swap(x, y string) (string, string) {
  return y, x
}
```
</summary><br><b>

```Go
x, y = swap("and roll", "rock")
fmt.Println(a, b)
```

</b></details>

<details>
<summary>What is the result of the following code?

```Go
func process(num int) (x int) {
  x = num + 10
  var z = num - x
  x = z + x
  return
}

func main() {
  fmt.Println(process(10))
}
```
</summary><br><b>

10
</b></details>


## Projects

TODO