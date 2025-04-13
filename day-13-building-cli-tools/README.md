# Day 13: Building CLI Tools

## Overview
This day focuses on **Building CLI Tools** in Go. You will learn how to create command-line tools using Go and explore libraries like `cobra` and `urfave/cli`.

## Tasks
- Task 1: Create a basic CLI tool using Go's `flag` package.
- Task 2: Use the `cobra` library to build a more advanced CLI tool.
- Task 3: Add subcommands and flags to your CLI tool.

## Resources
- [Go's flag Package](https://pkg.go.dev/flag)
- [Cobra Documentation](https://github.com/spf13/cobra)
- [urfave/cli Documentation](https://github.com/urfave/cli)

## Example Code
```go
// Example: Basic CLI Tool with Cobra
package main

import (
    "fmt"
    "github.com/spf13/cobra"
)

func main() {
    var rootCmd = &cobra.Command{
        Use:   "mycli",
        Short: "MyCLI is a simple CLI tool",
        Run: func(cmd *cobra.Command, args []string) {
            fmt.Println("Hello from MyCLI!")
        },
    }

    rootCmd.Execute()
}