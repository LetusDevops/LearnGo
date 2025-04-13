# File: /golang-10-day-path/golang-10-day-path/day-5-file-and-network-operations/README.md

## Day 5: File and Network Operations

On Day 5, we will focus on file I/O and network operations in Go. This day is crucial for understanding how to handle data and communicate over networks, which are essential skills in DevOps.

### Objectives
- Learn how to read from and write to files in Go.
- Understand how to perform network operations, including creating a simple HTTP server.

### File I/O
- Go provides the `os` and `io/ioutil` packages for file operations.
- You will learn how to open, read, write, and close files.

### Network Operations
- Go's `net/http` package allows you to create HTTP servers and clients.
- You will build a simple HTTP server that responds to requests.

### Resources
- [Go File I/O Documentation](https://golang.org/pkg/os/#File)
- [Go HTTP Documentation](https://golang.org/pkg/net/http/)

### Example Code
Here is a simple example of reading a file and starting an HTTP server:

```go
package main

import (
    "fmt"
    "io/ioutil"
    "net/http"
)

func readFile(filename string) {
    data, err := ioutil.ReadFile(filename)
    if err != nil {
        fmt.Println("Error reading file:", err)
        return
    }
    fmt.Println(string(data))
}

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello, you've requested: %s\n", r.URL.Path)
}

func main() {
    readFile("example.txt")
    http.HandleFunc("/", handler)
    http.ListenAndServe(":8080", nil)
}
```

### Exercises
1. Create a program that reads a text file and prints its contents to the console.
2. Build an HTTP server that serves static files from a directory.

By the end of Day 5, you should be comfortable with file operations and basic network programming in Go. Happy coding!