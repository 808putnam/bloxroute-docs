# go.mod

The `go.mod` file is used by Go's dependency management system. It tracks the module's dependencies and their specific versions.&#x20;

This file is automatically updated when you add, remove, or upgrade dependencies using commands like `go get`, `go mod tidy`, etc.&#x20;

Here's a brief overview of its sections:

1. `module github.com/bloXroute-Labs/solana-trader-client-go`: This line declares the module path, which other modules can use to import this one.
2. `go 1.18`: This line specifies the Go version used by this module.
3. `require`: This section lists the module's direct dependencies along with their versions. For example, `github.com/gagliardetto/solana-go v1.8.4` means that this module depends on version 1.8.4 of the `github.com/gagliardetto/solana-go` module.
4. `require (indirect)`: This section lists the indirect dependencies of the module. These are dependencies that are not directly imported by this module but are imported by its direct dependencies.

