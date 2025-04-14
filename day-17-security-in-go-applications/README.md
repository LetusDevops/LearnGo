# Day 17: Security in Go Applications

## Overview
This day focuses on **Security in Go Applications**. You will learn how to secure your Go applications by implementing encryption, authentication, and authorization mechanisms.

## Tasks
- Task 1: Implement password hashing using Go's `bcrypt` package.
- Task 2: Secure data transmission using TLS in a Go web server.
- Task 3: Add JWT-based authentication to a Go REST API.

## Resources
- [Go bcrypt Package](https://pkg.go.dev/golang.org/x/crypto/bcrypt)
- [TLS in Go](https://pkg.go.dev/crypto/tls)
- [JWT in Go](https://pkg.go.dev/github.com/golang-jwt/jwt/v4)

## Example Code
```go
// Example: Password Hashing with bcrypt
package main

import (
    "fmt"
    "golang.org/x/crypto/bcrypt"
)

func main() {
    password := "mysecurepassword"

    // Hash the password
    hashedPassword, err := bcrypt.GenerateFromPassword([]byte(password), bcrypt.DefaultCost)
    if err != nil {
        fmt.Println("Error hashing password:", err)
        return
    }
    fmt.Println("Hashed Password:", string(hashedPassword))

    // Compare the hashed password with a plain text password
    err = bcrypt.CompareHashAndPassword(hashedPassword, []byte(password))
    if err != nil {
        fmt.Println("Password does not match!")
    } else {
        fmt.Println("Password matches!")
    }
}
```

## Exercises
- Implement password hashing and verification using the `bcrypt` package.
- Secure a Go web server with TLS and serve HTTPS traffic.
- Add JWT-based authentication to a REST API and secure specific endpoints.