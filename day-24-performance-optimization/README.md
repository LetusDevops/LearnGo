# Day 24: Performance Optimization

## Overview
This day focuses on **Performance Optimization** in Go. You will learn how to profile and optimize Go applications using tools like `pprof` and `benchstat`.

## Tasks
- Task 1: Use `pprof` to profile a Go application and identify bottlenecks.
- Task 2: Optimize a Go program by improving its memory and CPU usage.
- Task 3: Benchmark your Go code and compare results using `benchstat`.

## Resources
- [Profiling Go Programs with pprof](https://pkg.go.dev/net/http/pprof)
- [Go Benchmarking Guide](https://dave.cheney.net/2013/06/30/how-to-write-benchmarks-in-go)
- [benchstat Tool](https://pkg.go.dev/golang.org/x/perf/cmd/benchstat)

## Example Code
```go
// Example: Profiling a Go Application with pprof
package main

import (
    "fmt"
    "net/http"
    _ "net/http/pprof"
    "time"
)

func slowFunction() {
    time.Sleep(2 * time.Second)
}

func main() {
    go func() {
        fmt.Println(http.ListenAndServe("localhost:6060", nil))
    }()

    for i := 0; i < 5; i++ {
        slowFunction()
    }
}
```

## Exercises
- Run the example code and use `pprof` to analyze its performance.
- Optimize the `slowFunction` to reduce its execution time.
- Write benchmarks for a Go function and compare results before and after optimization using `benchstat`.