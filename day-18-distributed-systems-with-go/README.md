# Day 18: Distributed Systems with Go

## Overview
This day focuses on **Distributed Systems with Go**. You will learn how to build distributed systems using Go and explore tools like gRPC for communication between services.

## Tasks
- Task 1: Set up a basic gRPC server and client in Go.
- Task 2: Implement a distributed key-value store using Go.
- Task 3: Explore service discovery using tools like Consul or etcd.

## Resources
- [gRPC in Go](https://grpc.io/docs/languages/go/)
- [Building Distributed Systems with Go](https://www.oreilly.com/library/view/building-distributed-systems/9781492077534/)
- [Consul Documentation](https://www.consul.io/docs)

## Example Code
```go
// Example: Basic gRPC Server in Go
package main

import (
    "context"
    "fmt"
    "log"
    "net"

    "google.golang.org/grpc"
    pb "example.com/helloworld"
)

type server struct {
    pb.UnimplementedGreeterServer
}

func (s *server) SayHello(ctx context.Context, in *pb.HelloRequest) (*pb.HelloReply, error) {
    log.Printf("Received: %v", in.GetName())
    return &pb.HelloReply{Message: "Hello " + in.GetName()}, nil
}

func main() {
    lis, err := net.Listen("tcp", ":50051")
    if err != nil {
        log.Fatalf("failed to listen: %v", err)
    }
    s := grpc.NewServer()
    pb.RegisterGreeterServer(s, &server{})
    fmt.Println("gRPC server is running on port 50051")
    if err := s.Serve(lis); err != nil {
        log.Fatalf("failed to serve: %v", err)
    }
}
```

## Exercises
- Build a gRPC client to interact with the example server.
- Implement a distributed key-value store with multiple nodes communicating via gRPC.
- Use Consul or etcd for service discovery in your distributed system.