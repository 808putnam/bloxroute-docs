# constants.py

The `constants.py` file defines several constants and functions related to the configuration of different environments (mainnet, testnet, devnet, and local) for Solana.

The constants at the top of the file define the base URLs for the different environments.

The `http_endpoint` and `ws_endpoint` functions are used to construct full URLs for HTTP and WebSocket endpoints, respectively. They take a base URL and a boolean indicating whether the connection should be secure (HTTPS/WSS) or not (HTTP/WS).

The rest of the constants are specific URLs for each environment, constructed using the base URLs and the `http_endpoint` and `ws_endpoint` functions. These constants include HTTP endpoints, WebSocket endpoints, gRPC hosts, and gRPC ports for each environment.

