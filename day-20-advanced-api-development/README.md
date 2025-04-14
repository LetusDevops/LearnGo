# Day 20: Advanced API Development

## Overview
This day focuses on **Advanced API Development** in Go. You will learn how to build advanced REST and GraphQL APIs, implement middleware, and add features like rate limiting and authentication.

## Tasks
- Task 1: Build a REST API with advanced features like pagination and filtering.
- Task 2: Implement a GraphQL API using the `gqlgen` library.
- Task 3: Add middleware for rate limiting and authentication.

## Resources
- [Go REST API Best Practices](https://github.com/qiangxue/go-rest-api)
- [gqlgen Documentation](https://gqlgen.com/)
- [Rate Limiting in Go](https://pkg.go.dev/golang.org/x/time/rate)

## Example Code
```go
// Example: Middleware for Rate Limiting
package main

import (
    "fmt"
    "net/http"
    "time"

    "golang.org/x/time/rate"
)

var limiter = rate.NewLimiter(1, 3) // 1 request per second, burst of 3

func rateLimitedHandler(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        if !limiter.Allow() {
            http.Error(w, "Too Many Requests", http.StatusTooManyRequests)
            return
        }
        next.ServeHTTP(w, r)
    })
}

func mainHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "Welcome to Advanced API Development!")
}

func main() {
    mux := http.NewServeMux()
    mux.Handle("/", rateLimitedHandler(http.HandlerFunc(mainHandler)))

    fmt.Println("Server is running on port 8080")
    http.ListenAndServe(":8080", mux)
}
```

## Exercises
- Build a REST API with advanced features like sorting, filtering, and pagination.
- Create a GraphQL API using `gqlgen` and define custom resolvers.
- Add middleware for rate limiting and JWT-based authentication to your API.