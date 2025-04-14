# Working with APIs in Go

## Overview
On Day 6, we will focus on consuming and creating REST APIs using Go. This is a crucial skill for integrating applications and services in a DevOps environment.

## Learning Objectives
- Understand the principles of RESTful APIs.
- Learn how to make HTTP requests in Go.
- Create a simple REST API using Go.

## Resources
- [Go HTTP Package Documentation](https://pkg.go.dev/net/http)
- [Building a RESTful API with Go](https://medium.com/@mohitkumar/building-a-restful-api-with-go-1c7f3c1f1e6e)
- [GoLang API Examples](https://github.com/go-gorm/gorm)

## Sample Code
Here is a simple example of a REST API in Go:

```go
package main

import (
    "encoding/json"
    "net/http"
)

type Message struct {
    Text string `json:"text"`
}

func helloHandler(w http.ResponseWriter, r *http.Request) {
    message := Message{Text: "Hello, World!"}
    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(message)
}

func main() {
    http.HandleFunc("/hello", helloHandler)
    http.ListenAndServe(":8080", nil)
}
```

## Exercises
- Write a Go program to consume a REST API and parse the JSON response.
- Create a REST API using Go's `net/http` package.
- Use a router library like `gorilla/mux` to add routing to your API.

## Next Steps
After completing this day, you will be ready to automate DevOps tasks using Go in the following days.