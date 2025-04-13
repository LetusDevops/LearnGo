# Day 11: Advanced Concurrency

## Overview
This day focuses on **Advanced Concurrency** in Go. You will dive deeper into goroutines, channels, and worker pools, and learn how to optimize concurrent programs for performance.

## Tasks
- Task 1: Learn about advanced patterns in goroutines and channels.
- Task 2: Implement a worker pool to process tasks concurrently.
- Task 3: Optimize a concurrent program for better performance.

## Resources
- [Go Concurrency Patterns](https://go.dev/doc/effective_go#concurrency)
- [Goroutines and Channels](https://tour.golang.org/concurrency/1)
- [Concurrency in Go by Katherine Cox-Buday](https://www.oreilly.com/library/view/concurrency-in-go/9781491941294/)

## Example Code
```go
// Example: Worker Pool in Go
package main

import (
    "fmt"
    "time"
)

func worker(id int, jobs <-chan int, results chan<- int) {
    for job := range jobs {
        fmt.Printf("Worker %d started job %d\n", id, job)
        time.Sleep(time.Second) // Simulate work
        fmt.Printf("Worker %d finished job %d\n", id, job)
        results <- job * 2
    }
}

func main() {
    const numJobs = 5
    jobs := make(chan int, numJobs)
    results := make(chan int, numJobs)

    // Start workers
    for w := 1; w <= 3; w++ {
        go worker(w, jobs, results)
    }

    // Send jobs
    for j := 1; j <= numJobs; j++ {
        jobs <- j
    }
    close(jobs)

    // Collect results
    for a := 1; a <= numJobs; a++ {
        fmt.Printf("Result: %d\n", <-results)
    }
}