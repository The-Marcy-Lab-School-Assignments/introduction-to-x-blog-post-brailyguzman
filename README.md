# Go for JavaScripters: Why You Should Learn Golang

**By**: **Braily Guzman**

!["Gopher"](./gopher.png)

## Why Learn Go

If you're a JavaScript developer looking to level up with a fast, modern language built for performance and scalability, it's time to meet Go.

**Go (or Golang)** is a middle-level programming language created at Google in 2007 by engineers who were tired of waiting around for their code to compile and dealing with overly complex systems. The result? A language that combines the performance of C (low-level) with the simplicity and readability of Python (high-level).

### What Makes Go Different?

- **Statically Typed**: You must declare variable types explicitly or let Go infer them, but once declared, the type can’t change.
- **Strongly Typed**: You can’t mix incompatible types. For example, Go won’t let you add an integer and a string together, something JavaScript would happily (and sometimes confusingly) do.
- **Compiled**: Go code is compiled into standalone binaries. That means you don’t need a runtime (like Node.js or Python) to run your app, just the binary file.

## What is Go Good At?

Go shines when it comes to building fast, scalable backend systems. It’s a top choice for writing APIs, web servers, CLI tools, and infrastructure-level software. Tools like **Docker**, **Kubernetes**, and **Terraform** are all written in Go, which says a lot about its speed and reliability.

One of Go’s biggest superpowers is **concurrency**, the ability to run multiple tasks at the same time. In JavaScript, we use `async/await` and the event loop to handle asynchronous operations. In Go, we use goroutines, lightweight threads that are easy to spawn and manage.

Go also makes deployment a breeze. While Node.js apps often require npm install, package.json, and a dozen dependencies, Go compiles everything into a single binary file you can just drop on a server and run.

## Core Syntax Overview

### Variables

**JavaScript**:

```js
const name = 'Braily';
let age = 18;
let city = 'New York';
```

**Go**:

```go
var name string = "Braily"

// Type inference with `var`
var age = 18

// Shorthand declaration
city := "New York"
```

Go is statically typed, so once a variable has a type, it can't be reassigned to something else, no switching `age` from a number to a string like in JS.

### Data Types

#### Integers

| **Type** | **Size**                                     | **Range (approximate)**         |
| -------- | -------------------------------------------- | ------------------------------- |
| int8     | 8-bit                                        | -128 to 127                     |
| uint8    | 8-bit                                        | 0 to 255                        |
| int16    | 16-bit                                       | -32,768 to 32,767               |
| uint16   | 16-bit                                       | 0 to 65,535                     |
| int32    | 32-bit                                       | -2.1 billion to 2.1 billion     |
| uint32   | 32-bit                                       | 0 to 4.2 billion                |
| int64    | 64-bit                                       | -9 quintillion to 9 quintillion |
| uint64   | 64-bit                                       | 0 to 18 quintillion             |
| int      | platform dependent (usually 32 or 64 bits)   |                                 |
| uint     | platform dependent (unsigned version of int) |                                 |

##### Key Notes

- `int` will default to 32 or 64 bits depending on your system.
- `uint` types don't allow negative numbers but igve you more room for positive values.
- Go will catch integer overflows at compile time, not at runtime.

```go
var intNum int16 = 32767 + 1 // Compile-time overflow error
```

This compiles but causes weird behavior:

```go
var intNum int16 = 32767
intNum += 1
fmt.Println(intNum) // Output: -32768 (wraps around!)
```

#### Floating Point

| **Type** | **Size** | **Precision**                          |
| -------- | -------- | -------------------------------------- |
| float32  | 32-bit   | 7 digits (single precision)            |
| float64  | 64-bit   | 15 digits (double precision — default) |

```go
var price float32 = 19.99
var total float64 = 12345678.900000

fmt.Println(price)
fmt.Println(total)
```

Warning: Precision loss can happen with `float32` when dealing with very large or very small decimal values.

### Functions and Control Flow

#### Functions

**JavaScript**:

```js
function greet(name) {
  return 'Hello ' + name;
}
```

**Go**:

```go
func greet(name string) string {
	return "Hello " + name
}
```

In go, you must declare the type of each parameter and the return value. The function block is enclosed by `{}` just like JS.

#### Conditionals

Go uses familiar `if/else` logic but requires the conditions to evaluate to a **bool**, no more truthy/falsy magic like in JS.

```go
if age >= 18 {
	fmt.Println("You're an adult!)
} else {
	fmt.Println("You're still a minor!")
}
```

## Loops

Go has only one loop keyword: `for`.

```go
for i := 0; i < 5; i++ {
	fmt.Println(i)
}
```

You can also use it like a `while` loop:

```go
x := 0

for x < 3 {
	fmt.Println(x)
	x++
}
```
