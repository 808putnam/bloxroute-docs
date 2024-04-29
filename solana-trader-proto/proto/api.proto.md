# api.proto

The `api.proto` file is a Protocol Buffers (protobuf) file. Protocol Buffers is a language-neutral, platform-neutral, extensible mechanism for serializing structured data. It's used for developing APIs and transmitting data between different services.

This specific `api.proto` file defines the structure and metadata for the "Trader API", which is an API for interacting with trader services on the Solana blockchain. Here's a breakdown of its main components:

* `syntax = "proto3";` specifies that this protobuf file uses version 3 of the protobuf language.
* `package api;` defines the package name for this protobuf file.
* `option go_package = "github.com/bloXroute-Labs/solana-trader-proto/api";` specifies the package name for the generated Go code.
* The `import` statements import other protobuf files that are used in this file.
* The `option (grpc.gateway.protoc_gen_openapiv2.options.openapiv2_swagger)` block defines metadata for the Swagger (OpenAPI) documentation. This includes security definitions, API information (title, version, description), and contact information.

