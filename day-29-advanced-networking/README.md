# Day 29: Advanced Networking

## Overview
This day focuses on **Advanced Networking** in Go. You will learn how to work with advanced networking concepts, implement custom protocols, and build load balancers using Go.

## Tasks
- Task 1: Build a TCP server and client in Go.
- Task 2: Implement a custom protocol for communication between services.
- Task 3: Create a simple load balancer to distribute traffic across multiple servers.

## Resources
- [Go net Package Documentation](https://pkg.go.dev/net)
- [Building TCP Servers in Go](https://tutorialedge.net/golang/go-building-a-tcp-server/)
- [Load Balancing Concepts](https://www.nginx.com/resources/glossary/load-balancing/)

## Example Code
```go
// Example: Simple TCP Server in Go
package main

import (
    "bufio"
    "fmt"
    "net"
)

func handleConnection(conn net.Conn) {
    defer conn.Close()
    fmt.Println("Client connected:", conn.RemoteAddr())
    scanner := bufio.NewScanner(conn)
    for scanner.Scan() {
        fmt.Println("Message from client:", scanner.Text())
        conn.Write([]byte("Message received\n"))
    }
}

func main() {
    listener, err := net.Listen("tcp", ":8080")
    if err != nil {
        fmt.Println("Error starting server:", err)
        return
    }
    defer listener.Close()
    fmt.Println("TCP server running on port 8080")

    for {
        conn, err := listener.Accept()
        if err != nil {
            fmt.Println("Error accepting connection:", err)
            continue
        }
        go handleConnection(conn)
    }
}
```

## Exercises
- Build a TCP client to communicate with the example server.
- Implement a custom protocol for exchanging structured data between the server and client.
- Create a load balancer in Go to distribute traffic across multiple instances of the TCP server.