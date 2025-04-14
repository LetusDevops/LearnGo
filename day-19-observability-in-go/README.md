# Day 19: Observability in Go

## Overview
This day focuses on **Observability in Go**. You will learn how to implement observability in Go applications using tracing, metrics, and logging tools.

## Tasks
- Task 1: Add structured logging to a Go application using `logrus`.
- Task 2: Implement metrics collection using Prometheus and expose a `/metrics` endpoint.
- Task 3: Add distributed tracing to a Go application using OpenTelemetry.

## Resources
- [Logrus Documentation](https://github.com/sirupsen/logrus)
- [Prometheus Go Client](https://prometheus.io/docs/guides/go-application/)
- [OpenTelemetry Go SDK](https://opentelemetry.io/docs/instrumentation/go/)

## Example Code
```go
// Example: Exposing Metrics with Prometheus
package main

import (
    "net/http"

    "github.com/prometheus/client_golang/prometheus"
    "github.com/prometheus/client_golang/prometheus/promhttp"
)

var (
    httpRequests = prometheus.NewCounterVec(
        prometheus.CounterOpts{
            Name: "http_requests_total",
            Help: "Total number of HTTP requests",
        },
        []string{"method", "endpoint"},
    )
)

func init() {
    prometheus.MustRegister(httpRequests)
}

func handler(w http.ResponseWriter, r *http.Request) {
    httpRequests.WithLabelValues(r.Method, r.URL.Path).Inc()
    w.Write([]byte("Hello, Observability!"))
}

func main() {
    http.Handle("/metrics", promhttp.Handler())
    http.HandleFunc("/", handler)
    http.ListenAndServe(":8080", nil)
}