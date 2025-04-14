# Day 28: Continuous Integration/Continuous Deployment (CI/CD)

## Overview
This day focuses on **Continuous Integration/Continuous Deployment (CI/CD)** in Go. You will learn how to automate CI/CD pipelines for Go applications using tools like GitHub Actions, GitLab CI, and Jenkins.

## Tasks
- Task 1: Set up a CI pipeline to run tests and build a Go application.
- Task 2: Add a CD pipeline to deploy the application to a server or cloud platform.
- Task 3: Integrate Docker into the CI/CD pipeline for containerized deployments.

## Resources
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)
- [Jenkins Pipeline Documentation](https://www.jenkins.io/doc/book/pipeline/)

## Example Code
```yaml
# Example: GitHub Actions Workflow for Go CI/CD
name: Go CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Set up Go
        uses: actions/setup-go@v4
        with:
          go-version: 1.20

      - name: Install Dependencies
        run: go mod tidy

      - name: Run Tests
        run: go test ./...

      - name: Build Application
        run: go build -o app

      - name: Docker Build and Push
        uses: docker/build-push-action@v4
        with:
          context: .
          push: true
          tags: your-dockerhub-username/your-app:latest