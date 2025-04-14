# Day 12: Go Modules and Dependency Management

## Overview
This day focuses on **Go Modules and Dependency Management**. You will learn how to manage dependencies effectively in Go projects using Go modules.

## Tasks
- Task 1: Initialize a Go module and understand the `go.mod` file.
- Task 2: Add and update dependencies in a Go project.
- Task 3: Explore versioning and replace directives in `go.mod`.

## Resources
- [Go Modules: Introduction](https://go.dev/blog/using-go-modules)
- [Managing Dependencies](https://golang.org/ref/mod)
- [Practical Guide to Go Modules](https://blog.golang.org/using-go-modules)

## Example Code
```go
// Example: Using Go Modules
package main

import (
    "fmt"
    "rsc.io/quote"
)

func main() {
    fmt.Println(quote.Hello())
}
```

## Exercises
- Initialize a new Go module and explore the `go.mod` file.
- Add a dependency to your project and use it in your code.
- Use the `replace` directive in `go.mod` to point to a local module.