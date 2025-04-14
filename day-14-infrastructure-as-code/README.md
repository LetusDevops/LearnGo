# Day 14: Infrastructure as Code (IaC)

## Overview
This day focuses on **Infrastructure as Code (IaC)**. You will learn how to use Go to interact with IaC tools like Terraform and Pulumi to automate infrastructure provisioning.

## Tasks
- Task 1: Write a Go program to interact with Terraform using the `terraform-exec` library.
- Task 2: Use Pulumi with Go to provision cloud resources.
- Task 3: Compare the benefits of using Go with IaC tools versus traditional scripting.

## Resources
- [Terraform Exec Library](https://github.com/hashicorp/terraform-exec)
- [Pulumi Go SDK](https://www.pulumi.com/docs/intro/languages/go/)
- [Infrastructure as Code Overview](https://www.hashicorp.com/resources/what-is-infrastructure-as-code)

## Example Code
```go
// Example: Using Pulumi with Go
package main

import (
    "github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
    pulumi.Run(func(ctx *pulumi.Context) error {
        bucket, err := ctx.NewResource("aws:s3/bucket:Bucket", "my-bucket", nil)
        if err != nil {
            return err
        }

        ctx.Export("bucketName", bucket.ID())
        return nil
    })
}
```

## Exercises
- Write a Go program to initialize and apply a Terraform configuration.
- Use Pulumi with Go to create a cloud resource (e.g., an S3 bucket).
- Compare the output of Terraform and Pulumi for the same infrastructure.