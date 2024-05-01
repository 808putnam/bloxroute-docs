# grpc.go

Pick up at line 115

The `grpc.go` file in the `provider` package defines a `GRPCClient` struct and methods for interacting with a remote gRPC server. Here's a brief overview of its contents:

1. `GRPCClient` struct: This struct has fields for the gRPC API client (`apiClient`), a Solana private key (`privateKey`), and a store for recent block hashes (`recentBlockHashStore`).
2. `NewGRPCClient`, `NewGRPCTestnet`, `NewGRPCDevnet`, `NewGRPCLocal`: These functions create a new `GRPCClient` connected to the Mainnet, Testnet, Devnet, and local Trader API, respectively.
3. `blxrCredentials` struct: This struct implements the `credentials.PerRPCCredentials` interface for providing custom authorization for the gRPC calls.
4. `NewGRPCClientWithOpts`: This function creates a new `GRPCClient` with custom options. It sets up the transport credentials, per-RPC credentials, and other dial options, and then dials the gRPC server. It also starts a goroutine to cache the recent block hash if the `CacheBlockHash` option is set.
5. `RecentBlockHash`: This method gets the recent block hash from the `recentBlockHashStore`.

