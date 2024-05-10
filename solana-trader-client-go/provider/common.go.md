# common.go

The `common.go` file is part of the `provider` package in Go. It defines constants, variables, types, and functions that are used across the package. Here's a brief overview of its contents:

1. Constants: `mainnetNY`, `mainnetUK`, `testnet`, and `devnet` are constants that represent the base URLs of different environments.
2. Variables: `MainnetNYHTTP`, `MainnetUKHTTP`, etc. are variables that represent the HTTP, WebSocket (WS), and gRPC endpoints for different environments. They are created by calling the `httpEndpoint`, `wsEndpoint`, and `grpcEndpoint` functions with the base URL and a boolean indicating whether the connection should be secure (HTTPS/WSS/gRPC over TLS).
3. Functions: `httpEndpoint`, `wsEndpoint`, and `grpcEndpoint` are functions that construct the full URL for HTTP, WS, and gRPC endpoints, respectively.
4. Error: `ErrPrivateKeyNotFound` is an error that is returned when a private key is not provided for signing a transaction.
5. Types: `PostOrderOpts`, `SubmitOpts`, and `RPCOpts` are types that define options for posting an order, submitting a transaction, and making RPC calls, respectively.
6. Function: `DefaultRPCOpts` is a function that creates a default `RPCOpts` object.
7. Map: `stringToAmm` is a map that converts a string to a `pb.Project` enum value.
8. Function: `ProjectFromString` is a function that converts a string to a `pb.Project` enum value.
9. Function: `buildBatchRequest` is a function that builds a batch request for submitting multiple transactions.
10. Function: `createBatchRequestEntry` is a function that creates a single entry in a batch request.
