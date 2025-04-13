# Functions and Packages in Go

## Overview
On Day 2, we will focus on understanding functions and packages in Go. Functions are fundamental building blocks in Go programming, allowing you to encapsulate code for reuse and organization. Packages help in organizing related functions and types, promoting modular programming.

## Learning Objectives
- Understand the syntax and structure of functions in Go.
- Learn how to create and use packages.
- Explore the concept of visibility and scope in Go.

## Key Concepts

### Functions
- **Definition**: A function is a block of code that performs a specific task.
- **Syntax**:
  ```go
  func functionName(parameters) returnType {
      // function body
  }
  ```

### Packages
- **Definition**: A package is a collection of Go files in the same directory that are compiled together.
- **Creating a Package**:
  1. Create a new directory for your package.
  2. Add Go files with the `package` keyword at the top.
  
### Example
Here’s a simple example of a function and a package:

1. **Creating a Package**:
   - Create a directory named `mypackage`.
   - Inside `mypackage`, create a file named `mypackage.go`:
     ```go
     package mypackage

     func Add(a int, b int) int {
         return a + b
     }
     ```

2. **Using the Package**:
   - In your main Go file, import and use the package:
     ```go
     package main

     import (
         "fmt"
         "path/to/mypackage"
     )

     func main() {
         result := mypackage.Add(5, 3)
         fmt.Println("Result:", result)
     }
     ```

## Resources
- [Go Functions Documentation](https://golang.org/doc/effective_go.html#functions)
- [Go Packages Documentation](https://golang.org/doc/code.html#Packages)

## Exercises
1. Create a package that includes functions for basic arithmetic operations (addition, subtraction, multiplication, division).
2. Write a main program that imports your arithmetic package and uses its functions.

Happy coding!