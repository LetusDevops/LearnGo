# Building a DevOps Tool with Go

In this section, we will apply everything we've learned throughout the 10-day path to build a small DevOps tool using Go. This project will help solidify your understanding of GoLang and its application in DevOps workflows.

## Project Overview

The goal of this project is to create a Command Line Interface (CLI) tool that can manage Docker containers. This tool will allow users to start, stop, and list containers directly from the command line.

## Features

- **Start a Docker container**: Command to start a specified container.
- **Stop a Docker container**: Command to stop a running container.
- **List all Docker containers**: Command to list all active and inactive containers.

## Getting Started

### Prerequisites

- Ensure you have Docker installed and running on your machine.
- Familiarity with GoLang and the concepts learned in the previous days.

### Project Structure

The project will be structured as follows:

```
golang-10-day-path
└── day-10-build-a-devops-tool
    ├── main.go
    └── README.md
```

### Implementation Steps

1. **Set up the Go module**: Initialize a new Go module for your project.
   ```bash
   go mod init devops-tool
   ```

2. **Create the main.go file**: This file will contain the main logic for your CLI tool.

3. **Use Docker API**: Leverage the Docker API to interact with Docker containers. You may use libraries such as `github.com/docker/docker/client`.

4. **Implement commands**: Create functions for starting, stopping, and listing containers.

5. **Testing**: Write tests to ensure your tool works as expected.

### Example Commands

- To start a container:
  ```bash
  go run main.go start <container_name>
  ```

- To stop a container:
  ```bash
  go run main.go stop <container_name>
  ```

- To list containers:
  ```bash
  go run main.go list
  ```

## Exercises
- Build a CLI tool to manage Docker containers (e.g., list, start, stop).
- Create a Go program to automate a CI/CD pipeline task (e.g., triggering builds).
- Develop a small tool to monitor system resources (e.g., CPU, memory usage).

## Conclusion

By the end of this project, you will have a functional CLI tool that demonstrates your ability to apply GoLang in a DevOps context. This project not only reinforces your learning but also provides a practical tool that can be used in real-world scenarios.

Happy coding!