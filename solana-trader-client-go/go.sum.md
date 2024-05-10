# go.sum

The `go.sum` file is used in Go modules to ensure the integrity of the module. It contains the expected cryptographic checksums of the content of specific module versions.

Each line in `go.sum` is of the form:

1. `<module-path>` and `<version>` together specify a particular version of a module.
2. The optional `/go.mod` suffix indicates that the hash is for the module's `go.mod` file. If the suffix is absent, the hash is for the module's source code.
3. `<hash>` is the cryptographic hash.

When you add a new dependency or update an existing one, the `go` command updates `go.sum` with the relevant lines for that dependency and its dependencies. When you build or test your code, the `go` command checks the entries in `go.sum` against the downloaded dependencies to ensure nothing has changed.

If a `go.sum` file is not present, the `go` command will create one. If a module provides a `go.sum` file, the `go` command will use it to verify downloaded dependencies. If a downloaded dependency doesn't match its expected checksum, the `go` command reports an error.
