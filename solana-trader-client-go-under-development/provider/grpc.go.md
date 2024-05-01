# grpc.go

The file, `grpc.go`, is part of a client for interacting with a gRPC service. It defines a `GRPCClient` struct and methods for this struct to interact with a remote gRPC server.

The `GRPCClient` struct has a field `apiClient` of type `pb.ApiClient` which is the client stub for the gRPC service. This stub is used to call the remote gRPC methods.

The file also defines several methods for the `GRPCClient` struct, each of which corresponds to a method in the gRPC service. These methods include `GetRecentBlockHash`, `GetPriorityFee`, `GetRateLimit`, `GetTransaction`, and others. Each of these methods takes a context and a request object, and returns a response object and an error.

The file also includes methods for creating a new `GRPCClient` for different environments (Mainnet, Testnet, Devnet, Local) and with custom options.

The `blxrCredentials` struct and its methods implement the `credentials.PerRPCCredentials` interface for providing custom authorization for the gRPC calls.

