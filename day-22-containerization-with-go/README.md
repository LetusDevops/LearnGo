# Day 22: Containerization with Go

## Overview
This day focuses on **Containerization with Go**. You will learn how to build and manage Docker containers using Go and explore libraries like `docker/docker`.

## Tasks
- Task 1: Write a Dockerfile to containerize a Go application.
- Task 2: Use the `docker/docker` library to interact with Docker from a Go program.
- Task 3: Build a CLI tool to manage Docker containers (e.g., start, stop, list).

## Resources
- [Docker Documentation](https://docs.docker.com/)
- [Docker Go SDK](https://pkg.go.dev/github.com/docker/docker)
- [Building Minimal Docker Images for Go Applications](https://medium.com/@povilasve/go-best-practices-organizing-dockerfiles-2312ae4f6e5c)

## Example Code
```go
// Example: Listing Docker Containers with Go
package main

import (
    "context"
    "fmt"
    "github.com/docker/docker/api/types"
    "github.com/docker/docker/client"
)

func main() {
    cli, err := client.NewClientWithOpts(client.FromEnv, client.WithAPIVersionNegotiation())
    if err != nil {
        panic(err)
    }

    containers, err := cli.ContainerList(context.Background(), types.ContainerListOptions{All: true})
    if err != nil {
        panic(err)
    }

    for _, container := range containers {
        fmt.Printf("Container ID: %s, Image: %s, Status: %s\n", container.ID[:10], container.Image, container.Status)
    }
}
```

## Exercises
- Write a Dockerfile to containerize a Go application and build the image.
- Use the `docker/docker` library to create a Go program that starts and stops containers.
- Build a CLI tool to list all running containers and their statuses.