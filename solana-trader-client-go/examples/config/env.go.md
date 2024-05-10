# env.go

The `env.go` file is part of the `config` package in Go. It is responsible for loading and managing environment variables for the application. Here's a breakdown of its main components:

1. `Example` struct: This struct holds the configuration for the application, including the environment (`Env`), and two boolean flags (`RunSlowStream` and `RunTrades`).
2. `BoolPtr` function: This is a helper function that returns a pointer to a boolean value.
3. `Load` function: This function loads the environment variables and returns an `Example` struct. It reads the `RUN_SLOW_STREAM` and `RUN_TRADES` environment variables and sets them in the `Example` struct. If these variables are not set or are set to "false", their corresponding fields in the `Example` struct will be `false`.
4. `Env` type and constants: `Env` is a type for environment variables, with constants for `mainnet`, `testnet`, and `local`.
5. `loadEnv` function: This function loads the `.env` file using the `godotenv` package and reads the `API_ENV` environment variable. It returns the corresponding `Env` constant based on the value of `API_ENV`. If `API_ENV` is not set or its value is not supported, it defaults to `EnvMainnet`.
