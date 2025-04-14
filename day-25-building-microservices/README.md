# Day 25: Building Microservices

## Overview
This day focuses on **Building Microservices** in Go. You will learn how to design and implement microservices using Go and explore frameworks like `go-kit` and `micro`.

## Tasks
- Task 1: Build a simple microservice with RESTful endpoints.
- Task 2: Use `go-kit` to implement a microservice with service discovery and logging.
- Task 3: Deploy multiple microservices and enable communication between them.

## Resources
- [Go-Kit Documentation](https://gokit.io/)
- [Micro Framework Documentation](https://m3o.com/)
- [Designing Microservices](https://martinfowler.com/microservices/)

## Example Code
```go
// Example: Simple Microservice with RESTful Endpoints
package main

import (
    "encoding/json"
    "fmt"
    "net/http"
)

type Response struct {
    Message string `json:"message"`
}

func helloHandler(w http.ResponseWriter, r *http.Request) {
    response := Response{Message: "Hello, Microservices!"}
    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(response)
}

func main() {
    http.HandleFunc("/hello", helloHandler)
    fmt.Println("Microservice running on port 8080")
    http.ListenAndServe(":8080", nil)
}
```

## Exercises
- Build a RESTful microservice with endpoints for CRUD operations.
- Use `go-kit` to add service discovery and logging to your microservice.
- Deploy multiple microservices and enable communication using gRPC or HTTP.