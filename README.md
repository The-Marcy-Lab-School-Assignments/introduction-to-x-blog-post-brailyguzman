# Go for JavaScripters: Why You Should Learn Golang

**By**: **Braily Guzman**

!['Gopher'](./gopher.png)

---

## Table of Contents

- [Go for JavaScripters: Why You Should Learn Golang](#go-for-javascripters-why-you-should-learn-golang)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
    - [What You'll Learn](#what-youll-learn)
  - [Why Learn Go](#why-learn-go)
  - [Go vs JavaScript: Quick Comparison](#go-vs-javascript-quick-comparison)
  - [What is Go Good At?](#what-is-go-good-at)
  - [When NOT to Use Go](#when-not-to-use-go)
  - [Core Syntax Overview](#core-syntax-overview)
    - [Hello, World!](#hello-world)
    - [Variables](#variables)
    - [Data Types](#data-types)
      - [Integers](#integers)
        - [Key Notes](#key-notes)
      - [Floating Point](#floating-point)
      - [Arrays and Slices](#arrays-and-slices)
        - [Arrays](#arrays)
        - [Slices](#slices)
    - [Structs, Types, Methods, and Interfaces](#structs-types-methods-and-interfaces)
    - [Strings, Bytes, and Runes](#strings-bytes-and-runes)
      - [Strings (Immutable UTF-8)](#strings-immutable-utf-8)
      - [\[\]byte (Raw Bytes)](#byte-raw-bytes)
      - [Runes (Unicode Code Points)](#runes-unicode-code-points)
      - [Type Conversions](#type-conversions)
      - [Quick Comparison: JavaScript vs Go](#quick-comparison-javascript-vs-go)
    - [Functions and Control Flow](#functions-and-control-flow)
      - [Functions](#functions)
      - [Returning Multiple Values](#returning-multiple-values)
      - [Conditionals](#conditionals)
  - [Pointers](#pointers)
  - [Loops](#loops)
    - [Using range](#using-range)
  - [Working with the strings Package](#working-with-the-strings-package)
  - [Concurrency in Go: Goroutines, Channels, WaitGroups, and Mutexes](#concurrency-in-go-goroutines-channels-waitgroups-and-mutexes)
    - [Concurrency vs Parallelism](#concurrency-vs-parallelism)
    - [Goroutines](#goroutines)
    - [Channels](#channels)
    - [WaitGroup](#waitgroup)
    - [Mutex](#mutex)
  - [defer](#defer)
  - [Common Gotchas for JS Devs](#common-gotchas-for-js-devs)
  - [Mini Project: Word Counter CLI](#mini-project-word-counter-cli)
  - [Go Modules \& Project Structure](#go-modules--project-structure)
  - [Error Handling in Go](#error-handling-in-go)
  - [Simple HTTP Server Example](#simple-http-server-example)
  - [Next Steps \& Resources](#next-steps--resources)
  - [JavaScript to Go: Quick Reference Cheat Sheet](#javascript-to-go-quick-reference-cheat-sheet)
  - [Conclusion](#conclusion)

---

## Introduction

Are you a JavaScript developer looking to expand your backend skills, or just curious about a language that powers Docker, Kubernetes, and much of the modern cloud? Meet **Go** (aka Golang): a language created at Google by Ken Thompson, Rob Pike, and Robert Griesemer to make software development fast, fun, and scalable.

Go is designed for simplicity, speed, and reliability. It compiles to a single binary, has a powerful standard library, and makes concurrency (doing many things at once) a breeze. If you love JavaScript's flexibility but crave more performance and predictability, Go is a perfect next step.

### What You'll Learn

- How Go compares to JavaScript in syntax and philosophy
- Go's type system, variables, and data structures
- How to handle strings, bytes, and runes (Unicode!)
- Using Go's `strings` package for text manipulation
- Common pitfalls for JS devs switching to Go
- How to build and run Go code

---

## Why Learn Go

If you're a JavaScript developer looking to level up with a fast, modern language built for performance and scalability, it's time to meet Go.

**Go (or Golang)** is a middle-level programming language created at Google in 2007 by engineers who were tired of waiting around for their code to compile and dealing with overly complex systems. The result? A language that combines the performance of C (low-level) with the simplicity and readability of Python (high-level).

---

## Go vs JavaScript: Quick Comparison

| Feature           | JavaScript              | Go                        |
| ----------------- | ----------------------- | ------------------------- |
| Typing            | Dynamic                 | Static                    |
| Compilation       | Interpreted/JIT         | Compiled (to binary)      |
| Concurrency       | Event loop, async/await | Goroutines, channels      |
| Deployment        | Needs Node.js runtime   | Single binary             |
| Error Handling    | try/catch               | Explicit error returns    |
| Popular Use Cases | Web, APIs, scripting    | APIs, infra, CLI, servers |

---

## What is Go Good At?

Go shines when it comes to building fast, scalable backend systems. It's a top choice for writing APIs, web servers, CLI tools, and infrastructure-level software. Tools like **Docker**, **Kubernetes**, and **Terraform** are all written in Go, which says a lot about its speed and reliability.

One of Go's biggest superpowers is **concurrency**, the ability to run multiple tasks at the same time. In JavaScript, we use `async/await` and the event loop to handle asynchronous operations. In Go, we use goroutines, lightweight threads that are easy to spawn and manage.

Go also makes deployment a breeze. While Node.js apps often require npm install, package.json, and a dozen dependencies, Go compiles everything into a single binary file you can just drop on a server and run.

---

## When NOT to Use Go

> **Go is not ideal for:**
>
> - Front-end/browser-based development
> - Rapid prototyping with lots of UI
> - Projects needing generics-heavy data structures (though Go 1.18+ now supports generics, it's not as flexible as TypeScript)

**Go might not be ideal for:**

- Projects that require a lot of dynamic typing or runtime type changes (Go is statically typed and not as flexible as JavaScript or Python for dynamic data structures).
- Codebases that rely heavily on advanced generics or metaprogramming (Go's generics are intentionally simple and less expressive than those in TypeScript, Rust, or C++).
- Rapid prototyping where developer speed and a huge ecosystem of libraries (like npm for JS or PyPI for Python) are critical. Go's ecosystem is strong but not as broad for every domain.
- Projects where you need mature, specialized libraries for things like data science, machine learning, or scientific computing (Go's ecosystem is growing, but not as deep as Python's in these areas).
- Teams that require hot-reloading, scripting, or embedding code at runtime (Go is compiled and not designed for scripting or live code changes).

---

## Core Syntax Overview

---

### Hello, World!

**JavaScript:**

```js
console.log('Hello, World!');
```

**Go:**

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

---

### Variables

**JavaScript:**

```js
const name = 'Braily';
let age = 18;
let city = 'New York';
```

**Go:**

```go
var name string = "Braily"
// Type inference with `var`
var age = 18
// Shorthand declaration
city := "New York"
```

Go is statically typed, so once a variable has a type, it can't be reassigned to something else, no switching `age` from a number to a string like in JS.

---

### Data Types

#### Integers

Unlike JavaScript, which uses a single `number` type for all integers, Go provides several distinct integer types. Each type has its own range and memory usage, allowing you to choose the most appropriate one for your needs.

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

For example, if you need to store an RGB (Red, Green, Blue) value ranging from 0 to 255, the best choice is `uint8` (an unsigned 8-bit integer), since it efficiently covers exactly that range. If you need to store larger values, simply choose an integer type with a bigger bit size, such as `uint16`, `uint32`, or `uint64`, depending on your requirements.

##### Key Notes

- `int` will default to 32 or 64 bits depending on your system.
- `uint` types don't allow negative numbers but give you more room for positive values.
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

#### Arrays and Slices

##### Arrays

In Go, arrays have **fixed sizes** and contain elements of a single type.

```go
var a [3]int = [3]int{1, 2, 3}
fmt.Println(a) // >>> [1 2 3]
```

You can also let Go infer the length:

```go
b := [...]string{"Go", "is", "cool"}
fmt.Println(b) // >>> [Go is cool]
```

**Key Points**:

- Arrays are **value types**. Assigning or passing them copies the whole array.
- Their size is part of their type (`[3]int` != `[4]int`)

##### Slices

Slices are more flexible and commonly used than arrays.

```go
nums := []int{10, 20, 30, 40}
fmt.Println(nums) // >>> [10 20 30 40]
```

You can create a slice from an array:

```go
arr := [5]int{1, 2, 3, 4, 5}
slice := arr[1:4] // elements [2, 3, 4]
fmt.Println(slice)
```

You can also use `make` to create a slice with a given length and capacity:

```go
s := make([]int, 3, 5) // len = 3, cap = 5
fmt.Println(s) // >>> [0 0 0]
```

Slices are **references to arrays**, so modifying one will affect the original array:

```go
s := []int{1, 2, 3}
s[0] = 99
fmt.Println(s) // [99 2 3]
```

**Append and Slice Tricks**

```go
s := []int{1, 2}
s = append(s, 3, 4) // Creates a new array
fmt.Println(s) // >>> [1 2 3 4]
```

---

### Structs, Types, Methods, and Interfaces

Go uses structs to group related data together, similar to objects in JavaScript. You can also define methods on types (including structs) to add behavior.

**Structs Example:**

```go
type Person struct {
    Name string
    Age  int
}

func main() {
    p := Person{Name: "Alice", Age: 30}
    fmt.Println(p.Name, p.Age)
}
```

**Methods Example:**

```go
type Person struct {
    Name string
}

func (p Person) Greet() string {
    return "Hello, " + p.Name
}

func main() {
    p := Person{Name: "Bob"}
    fmt.Println(p.Greet()) // Output: Hello, Bob
}
```

**What are Interfaces?**

Interfaces in Go define a set of method signatures (behavior) that a type must implement. Any type that provides those methods "satisfies" the interface, even if it doesn't explicitly declare that it does. This allows you to write flexible and decoupled code, because functions can accept interfaces rather than concrete types. Interfaces are a key part of Go's approach to polymorphism and code reuse.

**What is Duck Typing?**

Duck typing is a concept where the type or class of an object is determined by its behavior (methods and properties), not by explicit inheritance or declaration. The phrase comes from "If it walks like a duck and quacks like a duck, it's a duck." In Go, any type that implements the methods required by an interface is considered to satisfy that interface, even if it doesn't explicitly declare it. This is similar to how JavaScript objects can be passed to functions as long as they have the expected methods or properties.

**Interfaces Example (Multiple Types):**

```go
type Greeter interface {
    Greet() string
}

type Person struct {
    Name string
}

func (p Person) Greet() string {
    return "Hello, " + p.Name
}

type Robot struct {
    ID int
}

func (r Robot) Greet() string {
    return fmt.Sprintf("Beep boop, I am robot #%d", r.ID)
}

func sayHello(g Greeter) {
    fmt.Println(g.Greet())
}

func main() {
    p := Person{Name: "Carol"}
    r := Robot{ID: 42}
    sayHello(p) // Output: Hello, Carol
    sayHello(r) // Output: Beep boop, I am robot #42
}
```

**JavaScript Comparison:**
JavaScript doesn't have interfaces, but you can use objects with the same method signatures (duck typing):

```js
function sayHello(greeter) {
  console.log(greeter.greet());
}
const person = {
  name: 'Carol',
  greet() {
    return `Hello, ${this.name}`;
  },
};
const robot = {
  id: 42,
  greet() {
    return `Beep boop, I am robot #${this.id}`;
  },
};
sayHello(person); // Hello, Carol
sayHello(robot); // Beep boop, I am robot #42
```

---

### Strings, Bytes, and Runes

In **JavaScript**, strings are sequences of UTF-16 code units. This usually feels like characters but isn't always, especially with emojis or characters from other languages.

In **Go**, strings are **UTF-8 encoded immutable slices of bytes**. That means:

- A string is a sequence of bytes.
- Characters can take up multiple bytes.
- Indexing directly gives you a **byte**, not a character.

#### Strings (Immutable UTF-8)

```go
greeting := "Hello, 世界"
fmt.Println(greeting)       // >>> Hello, 世界
fmt.Println(len(greeting))  // >>> 13 (bytes, not characters)
```

- Each character in `"Hello, 世界"` might take 1-3 bytes.
- Strings are immutable. You **can't** change characters via indexing.

**Accessing bytes (not characters)**:

```go
s := "世界"
fmt.Println(s[0])           // >>> 228 (byte, not '世')
```

#### []byte (Raw Bytes)

- A `byte` is an alias for `uint8`, just a number from 0-255.
- `[]byte` lets you inspect or manipulate the underlying raw data of a string.

```go
word := "résumé"
b := []byte(word)
fmt.Println(b)              // >>> [114 195 169 115 117 109 195 169]
fmt.Println(len(b))         // >>> 8
```

**Compare with JavaScript:**

```js
const word = 'résumé';
console.log(word.length); // 6 characters
console.log(Buffer.from(word)); // <Buffer 72 c3 a9 73 75 6d c3 a9>
```

#### Runes (Unicode Code Points)

A `rune` in Go is an **int32** representing a full Unicode character, even emojis and symbols from non-Latin scripts.

- Useful when dealing with **characters**, not bytes.
- Can handle multi-byte characters like emoji properly.

```go
emoji := "💖"
fmt.Println(len(emoji))       // >>> 4 (bytes)
fmt.Println(utf8.RuneCountInString(emoji)) // >>> 1
```

Use a `[]rune` to **see each character** properly:

```go
name := "résumé💖"
runes := []rune(name)

fmt.Println(len(runes))       // >>> 7
fmt.Printf("%q\n", runes)     // >>> ['r' 'é' 's' 'u' 'm' 'é' '💖']
```

#### Type Conversions

```go
s := "Go💖"

// string → []byte
b := []byte(s)
fmt.Println(b) // >>> [71 111 240 159 146 150]

// string → []rune
r := []rune(s)
fmt.Println(r) // >>> [71 111 128150]

// []rune → string
fmt.Println(string(r)) // >>> Go💖
```

#### Quick Comparison: JavaScript vs Go

| Concept        | JavaScript                    | Go                       |
| -------------- | ----------------------------- | ------------------------ |
| String         | `"Go💖"`                      | `"Go💖"`                 |
| Char (Unicode) | `"💖".charCodeAt(0)` → 55357  | `rune('💖')` → 128150    |
| Byte length    | `Buffer.byteLength("💖")` → 4 | `len("💖")` → 4          |
| Char length    | `"💖".length` → 2             | `utf8.RuneCountInString` |
| Char array     | `Array.from("résumé")`        | `[]rune("résumé")`       |

**TL;DR**:

| What you want            | Use this in Go                |
| ------------------------ | ----------------------------- |
| String of text           | `string`                      |
| Raw binary data          | `[]byte`                      |
| Unicode-safe characters  | `[]rune`                      |
| Count visible characters | `utf8.RuneCountInString(str)` |
| Loop over characters     | `for _, r := range str`       |

---

### Functions and Control Flow

#### Functions

**JavaScript:**

```js
function greet(name) {
  return 'Hello ' + name;
}
```

**Go:**

```go
func greet(name string) string {
	return "Hello " + name
}
```

In Go, you must declare the type of each parameter and the return value. The function block is enclosed by `{}` just like JS.

---

#### Returning Multiple Values

Go functions can return more than one value, which is commonly used for returning a result and an error.

```go
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, fmt.Errorf("cannot divide by zero")
    }
    return a / b, nil
}

result, err := divide(10, 2)
if err != nil {
    fmt.Println("Error:", err)
} else {
    fmt.Println("Result:", result)
}
```

**JavaScript Comparison:**

In JavaScript, you might return an object or array to simulate multiple return values:

```js
function divide(a, b) {
  if (b === 0) return [null, 'cannot divide by zero'];
  return [a / b, null];
}

const [result, error] = divide(10, 2);
if (error) {
  console.log('Error:', error);
} else {
  console.log('Result:', result);
}
```

---

#### Conditionals

Go uses familiar `if/else` logic but requires the conditions to evaluate to a **bool**, no more truthy/falsy magic like in JS.

```go
if age >= 18 {
	fmt.Println("You're an adult!")
} else {
	fmt.Println("You're still a minor!")
}
```

---

## Pointers

Go uses pointers to reference memory locations, similar to C, but without pointer arithmetic. Pointers are useful for modifying values in place and for efficient memory usage.

**Example:**

```go
func increment(n *int) {
    *n = *n + 1
}

num := 5
increment(&num)
fmt.Println(num) // Output: 6
```

- `*int` means "pointer to an int".
- `&num` gets the address of `num`.
- `*n` dereferences the pointer to access the value.

**JavaScript Comparison:**
JavaScript does not have pointers, but objects and arrays are passed by reference:

```js
function increment(obj) {
  obj.value++;
}
let num = { value: 5 };
increment(num);
console.log(num.value); // 6
```

---

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

---

### Using range

The `range` keyword is used to iterate over elements in a variety of data structures, including arrays, slices, maps, and strings. When iterating over a string, `range` yields the index and the Unicode code point (rune) at each position.

**Example: Iterating over runes in a string**

```go
str := "Go💖"
for i, r := range str {
    fmt.Printf("Index: %d, Rune: %c, Unicode: %U\n", i, r, r)
}
```

_This will print each Unicode character (rune) in the string, including multi-byte characters like emojis._

---

## Working with the strings Package

Go's standard library includes the powerful `strings` package for manipulating text. Here are some common tasks:

```go
import (
    "fmt"
    "strings"
)

func main() {
    s := "  Hello, Go!  "
    fmt.Println(strings.ToUpper(s))           // "  HELLO, GO!  "
    fmt.Println(strings.TrimSpace(s))         // "Hello, Go!"
    fmt.Println(strings.Contains(s, "Go"))    // true
    fmt.Println(strings.HasPrefix(s, "  H"))  // true
    fmt.Println(strings.ReplaceAll(s, "Go", "Gophers")) // "  Hello, Gophers!  "
    fmt.Println(strings.Split(s, ","))        // ["  Hello" " Go!  "]
}
```

**JavaScript Comparison:**

```js
const s = '  Hello, Go!  ';
console.log(s.toUpperCase()); // "  HELLO, GO!  "
console.log(s.trim()); // "Hello, Go!"
console.log(s.includes('Go')); // true
console.log(s.startsWith('  H')); // true
console.log(s.replaceAll('Go', 'Gophers')); // "  Hello, Gophers!  "
console.log(s.split(',')); // ["  Hello", " Go!  "]
```

---

## Concurrency in Go: Goroutines, Channels, WaitGroups, and Mutexes

Go's concurrency model is one of its superpowers. Unlike JavaScript's single-threaded event loop, Go lets you run multiple tasks at the same time using goroutines and channels.

### Concurrency vs Parallelism

- **Concurrency** is about dealing with lots of things at once (structuring your program to handle multiple tasks that may not actually run at the same time).
- **Parallelism** is about doing lots of things at the same time (actually running on multiple CPU cores).

Go makes it easy to write concurrent code, and if your machine has multiple cores, Go can run goroutines in parallel too.

### Goroutines

A goroutine is a lightweight thread managed by the Go runtime. Just add `go` before a function call to run it concurrently:

```go
package main

import (
    "fmt"
    "time"
)

func sayHello() {
    fmt.Println("Hello from a goroutine!")
}

func main() {
    go sayHello() // runs concurrently
    fmt.Println("Main function")
    time.Sleep(time.Second) // Give goroutine time to run
}
```

### Channels

Channels let goroutines communicate safely:

```go
package main

import (
    "fmt"
)

func main() {
    ch := make(chan string)
    go func() {
        ch <- "Hello from goroutine"
    }()
    msg := <-ch
    fmt.Println(msg)
}
```

- `ch <- value` sends a value into the channel.
- `<-ch` receives a value from the channel.

### WaitGroup

A `sync.WaitGroup` lets you wait for a group of goroutines to finish:

```go
package main

import (
    "fmt"
    "sync"
)

func worker(id int, wg *sync.WaitGroup) {
    defer wg.Done()
    fmt.Printf("Worker %d done\n", id)
}

func main() {
    var wg sync.WaitGroup
    for i := 1; i <= 3; i++ {
        wg.Add(1)
        go worker(i, &wg)
    }
    wg.Wait() // Wait for all workers to finish
    fmt.Println("All workers done")
}
```

### Mutex

A `sync.Mutex` is used to safely share data between goroutines:

```go
package main
import (
    "fmt"
    "sync"
)

func main() {
    var mu sync.Mutex
    count := 0
    var wg sync.WaitGroup
    for i := 0; i < 1000; i++ {
        wg.Add(1)
        go func() {
            mu.Lock()
            count++
            mu.Unlock()
            wg.Done()
        }()
    }
    wg.Wait()
    fmt.Println("Final count:", count)
}
```

**Why use a mutex?** Without it, multiple goroutines could try to update `count` at the same time, causing race conditions.

---

## defer

The `defer` keyword in Go schedules a function call to run after the function completes, just before it returns. This is especially useful for cleanup tasks like closing files, unlocking mutexes, or printing final messages.

**Example: File closing**

```go
package main
import (
    "fmt"
    "os"
)

func main() {
    f, err := os.Open("file.txt")
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    defer f.Close() // Will run at the end of main, even if there's a return or panic
    fmt.Println("File opened!")
    // ... do work with file ...
}
```

**Example: Multiple defers**

If you use multiple `defer` statements, they run in LIFO (last-in, first-out) order:

```go
func main() {
    defer fmt.Println("first")
    defer fmt.Println("second")
    fmt.Println("main body")
}
// Output:
// main body
// second
// first
```

**Common uses:**

- Closing files or network connections
- Unlocking mutexes
- Logging or printing final messages

**JavaScript Comparison:**
JavaScript doesn't have a direct equivalent, but you might use `finally` in a `try/catch/finally` block for similar cleanup:

```js
try {
  // ... work ...
} finally {
  // cleanup code
}
```

---

## Common Gotchas for JS Devs

- **No implicit type coercion:** Go won't convert types for you. `"5" + 1` is an error, not `"51"`.
- **Zero values:** Uninitialized variables have a default value (e.g., `0` for int, `""` for string, `nil` for pointers/slices/maps).
- **No exceptions:** Go uses explicit error returns, not try/catch.
- **No variable hoisting:** All variables must be declared before use.
- **No unused imports or variables:** The compiler will error if you import a package or declare a variable and don't use it.
- **No classes:** Use structs and interfaces instead.
- **No method overloading or default parameters.**

---

## Mini Project: Word Counter CLI

Let's build a simple CLI tool that reads a line of text from the user, counts the number of words and unique words, and prints word frequencies. This demonstrates string manipulation, maps, and user input.

```go
package main

import (
    "bufio"
    "fmt"
    "os"
    "strings"
)

func main() {
    reader := bufio.NewReader(os.Stdin)
    fmt.Print("Enter a sentence: ")
    line, _ := reader.ReadString('\n')
    line = strings.TrimSpace(line)
    words := strings.Fields(line)

    wordCount := make(map[string]int)
    for _, word := range words {
        wordCount[word]++
    }

    fmt.Printf("Total words: %d\n", len(words))
    fmt.Printf("Unique words: %d\n", len(wordCount))
    fmt.Println("Word frequencies:")
    for word, count := range wordCount {
        fmt.Printf("%s: %d\n", word, count)
    }
}
```

**Why not use `fmt.Scanf` for user input?**

- `fmt.Scanf` is best for simple, space-separated input (e.g., numbers or single words), but for names or sentences, `bufio.Reader` is preferred because it reads the whole line, including spaces. `fmt.Scanf` will only read up to the first space.

---

## Go Modules & Project Structure

Go uses modules to manage dependencies. To start a new project:

```sh
go mod init github.com/yourusername/yourproject
```

Typical Go project structure:

```
myproject/
  go.mod
  main.go
  pkg/      # reusable packages
  internal/ # private packages
```

---

## Error Handling in Go

Go does not use exceptions. Instead, functions that can fail return an `error` as a second return value:

```go
val, err := strconv.Atoi("123")
if err != nil {
    fmt.Println("Conversion failed:", err)
} else {
    fmt.Println("Value:", val)
}
```

---

## Simple HTTP Server Example

Go makes it easy to spin up a web server:

```go
package main
import (
    "fmt"
    "net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello from Go!")
}

func main() {
    http.HandleFunc("/", handler)
    fmt.Println("Server running at http://localhost:8080/")
    http.ListenAndServe(":8080", nil)
}
```

---

## Next Steps & Resources

- [Go by Example](https://gobyexample.com/)
- [A Tour of Go](https://go.dev/tour/)
- [Go Playground (try Go online!)](https://go.dev/play//)
- [Learn GO Fast: Full Tutorial (For non-beginners)](https://www.youtube.com/watch?v=8uiZC0l4Ajw)

---

## JavaScript to Go: Quick Reference Cheat Sheet

| JavaScript Concept        | Go Equivalent                    |
| ------------------------- | -------------------------------- |
| `let` / `const`           | `var` / `:=`                     |
| Array                     | Slice (`[]type`)                 |
| Object                    | Struct                           |
| Function                  | `func`                           |
| Class                     | Struct + Methods                 |
| Interface (TypeScript)    | Interface                        |
| `null` / `undefined`      | `nil`                            |
| `Promise` / `async/await` | Goroutine + Channel              |
| Exception (`try/catch`)   | Multiple return values + `error` |
| `finally`                 | `defer`                          |
| `for...of`                | `for _, v := range ...`          |
| `for...in`                | `for k := range ...`             |
| `Object.keys(obj)`        | `for k := range map`             |
| `console.log`             | `fmt.Println`                    |

---

## Conclusion

Go is a modern, efficient, and fun language that empowers JavaScript developers to build fast, scalable, and reliable backend systems. With its simple syntax, powerful concurrency model, and robust standard library, Go is a fantastic next step for anyone looking to level up their programming skills.

If you’re comfortable in JavaScript, you’re more ready for Go than you think. The syntax is different, but the logic and problem-solving skills you’ve built in JS will serve you well.

Ready to try Go? Dive into the resources above, experiment with the examples, and start building something awesome. Happy coding! 🚀

---

_Have questions or feedback? Feel free to reach out or leave a comment!_
