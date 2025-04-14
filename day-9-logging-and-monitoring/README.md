# Logging and Monitoring in Go

## Overview
This document covers the practices of logging and monitoring in Go applications, which are essential for maintaining and troubleshooting applications in a DevOps environment.

## Logging in Go
- **Standard Library**: Go provides a built-in `log` package for basic logging functionalities.
- **Third-Party Libraries**: Consider using libraries like `logrus` or `zap` for more advanced logging features such as structured logging and log levels.

### Example of Basic Logging
```go
package main

import (
    "log"
    "os"
)

func main() {
    // Create a log file
    file, err := os.OpenFile("app.log", os.O_CREATE|os.O_WRONLY|os.O_APPEND, 0666)
    if err != nil {
        log.Fatal(err)
    }
    defer file.Close()

    // Set output to the log file
    log.SetOutput(file)

    // Log messages
    log.Println("This is a log message.")
}
```

## Monitoring Go Applications
- **Metrics**: Use libraries like `prometheus/client_golang` to expose application metrics.
- **Health Checks**: Implement health check endpoints to monitor the status of your application.

### Example of Exposing Metrics
```go
package main

import (
    "net/http"
    "github.com/prometheus/client_golang/prometheus"
    "github.com/prometheus/client_golang/prometheus/promhttp"
)

var (
    requestCount = prometheus.NewCounterVec(
        prometheus.CounterOpts{
            Name: "http_requests_total",
            Help: "Total number of HTTP requests",
        },
        []string{"method"},
    )
)

func init() {
    prometheus.MustRegister(requestCount)
}

func handler(w http.ResponseWriter, r *http.Request) {
    requestCount.WithLabelValues(r.Method).Inc()
    w.Write([]byte("Hello, World!"))
}

func main() {
    http.Handle("/metrics", promhttp.Handler())
    http.HandleFunc("/", handler)
    http.ListenAndServe(":8080", nil)
}
```

## Exercises
- Add structured logging to a Go application using `logrus` or `zap`.
- Create a Go program that logs messages at different levels (e.g., info, warning, error).
- Integrate a monitoring tool like Prometheus to collect metrics from your Go application.

## Conclusion
Implementing effective logging and monitoring in your Go applications will help you maintain visibility into application performance and issues, which is crucial for successful DevOps practices.