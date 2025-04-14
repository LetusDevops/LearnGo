# Day 16: Event-Driven Programming

## Overview
This day focuses on **Event-Driven Programming** in Go. You will learn how to implement event-driven architectures using Go and work with message queues like RabbitMQ and Kafka.

## Tasks
- Task 1: Set up a message broker (e.g., RabbitMQ or Kafka) locally or in the cloud.
- Task 2: Write a Go producer to publish messages to a queue.
- Task 3: Write a Go consumer to process messages from the queue.

## Resources
- [RabbitMQ Go Client](https://pkg.go.dev/github.com/streadway/amqp)
- [Kafka Go Client (Sarama)](https://github.com/Shopify/sarama)
- [Event-Driven Architecture Overview](https://martinfowler.com/articles/201701-event-driven.html)

## Example Code
```go
// Example: Publishing and Consuming Messages with RabbitMQ
package main

import (
    "fmt"
    "log"

    "github.com/streadway/amqp"
)

func failOnError(err error, msg string) {
    if err != nil {
        log.Fatalf("%s: %s", msg, err)
    }
}

func main() {
    conn, err := amqp.Dial("amqp://guest:guest@localhost:5672/")
    failOnError(err, "Failed to connect to RabbitMQ")
    defer conn.Close()

    ch, err := conn.Channel()
    failOnError(err, "Failed to open a channel")
    defer ch.Close()

    q, err := ch.QueueDeclare(
        "hello", // name
        false,   // durable
        false,   // delete when unused
        false,   // exclusive
        false,   // no-wait
        nil,     // arguments
    )
    failOnError(err, "Failed to declare a queue")

    body := "Hello, World!"
    err = ch.Publish(
        "",     // exchange
        q.Name, // routing key
        false,  // mandatory
        false,  // immediate
        amqp.Publishing{
            ContentType: "text/plain",
            Body:        []byte(body),
        })
    failOnError(err, "Failed to publish a message")
    fmt.Printf(" [x] Sent %s\n", body)
}
```

## Exercises
- Set up RabbitMQ or Kafka locally and test the example code.
- Modify the example to include multiple producers and consumers.
- Implement a retry mechanism for failed message processing.