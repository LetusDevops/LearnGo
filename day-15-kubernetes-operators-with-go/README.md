# Day 15: Kubernetes Operators with Go

## Overview
This day focuses on **Kubernetes Operators with Go**. You will learn how to build Kubernetes operators using the `controller-runtime` library to manage custom resources in Kubernetes.

## Tasks
- Task 1: Set up a Kubernetes cluster for development (e.g., Minikube or Kind).
- Task 2: Create a custom resource definition (CRD) for your operator.
- Task 3: Implement a Kubernetes operator using the `controller-runtime` library.

## Resources
- [Kubernetes Operators Overview](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)
- [Kubebuilder Documentation](https://book.kubebuilder.io/)
- [Controller Runtime Library](https://pkg.go.dev/sigs.k8s.io/controller-runtime)

## Example Code
```go
// Example: Basic Kubernetes Operator with Controller Runtime
package main

import (
    "context"
    "fmt"
    "sigs.k8s.io/controller-runtime/pkg/client"
    "sigs.k8s.io/controller-runtime/pkg/manager"
)

func main() {
    mgr, err := manager.New(manager.GetConfigOrDie(), manager.Options{})
    if err != nil {
        fmt.Println("Error creating manager:", err)
        return
    }

    // Example: List all pods in the cluster
    k8sClient := mgr.GetClient()
    pods := &corev1.PodList{}
    err = k8sClient.List(context.TODO(), pods, &client.ListOptions{})
    if err != nil {
        fmt.Println("Error listing pods:", err)
        return
    }

    for _, pod := range pods.Items {
        fmt.Println("Pod Name:", pod.Name)
    }
}
```

## Exercises
- Create a custom resource definition (CRD) for managing a specific application (e.g., a database).
- Implement a controller that watches the CRD and performs actions based on its state.
- Deploy your operator to a Kubernetes cluster and test its functionality.