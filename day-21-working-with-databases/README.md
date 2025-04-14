# Day 21: Working with Databases

## Overview
This day focuses on **Working with Databases** in Go. You will learn how to interact with SQL and NoSQL databases using Go and explore libraries like `gorm` and `mongo-go-driver`.

## Tasks
- Task 1: Connect to a SQL database (e.g., PostgreSQL or MySQL) and perform CRUD operations.
- Task 2: Use the `gorm` library to simplify database interactions.
- Task 3: Work with a NoSQL database (e.g., MongoDB) using the `mongo-go-driver`.

## Resources
- [GORM Documentation](https://gorm.io/)
- [MongoDB Go Driver Documentation](https://pkg.go.dev/go.mongodb.org/mongo-driver)
- [Database/SQL Package](https://pkg.go.dev/database/sql)

## Example Code
```go
// Example: Connecting to a PostgreSQL Database with GORM
package main

import (
    "fmt"
    "gorm.io/driver/postgres"
    "gorm.io/gorm"
)

type User struct {
    ID    uint   `gorm:"primaryKey"`
    Name  string
    Email string
}

func main() {
    dsn := "host=localhost user=postgres password=yourpassword dbname=testdb port=5432 sslmode=disable"
    db, err := gorm.Open(postgres.Open(dsn), &gorm.Config{})
    if err != nil {
        fmt.Println("Failed to connect to the database:", err)
        return
    }

    // Auto-migrate the User model
    db.AutoMigrate(&User{})

    // Create a new user
    user := User{Name: "John Doe", Email: "john.doe@example.com"}
    db.Create(&user)

    // Retrieve all users
    var users []User
    db.Find(&users)
    fmt.Println("Users:", users)
}