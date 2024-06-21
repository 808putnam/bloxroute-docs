# main.py

The `main.py` file is the main entry point for a trading bot that interacts with a trading platform using three different protocols: WebSocket (WS), gRPC, and HTTP.

The script retrieves environment variables for public key, private key, open orders, base token wallet, and quote token wallet. It also sets up some constants for the market address, order side, order type, order price, and order amount.

The script is designed to be run as a standalone program. When run, it starts the asyncio event loop and runs the `main` function. The `main` function is an asynchronous function that runs three other asynchronous functions: `ws`, `grpc`, and `http`.

1. `ws`: This function demonstrates how to create, replace, and cancel an order using the WebSocket protocol. It first sets up two WebSocket providers, then performs the order lifecycle, cancels all orders, and replaces an order by client order ID using the `examples` module.
2. `grpc`: This function demonstrates how to create, replace, and cancel an order using the gRPC protocol. It sets up a gRPC provider, then performs the order lifecycle, cancels all orders, and replaces an order by client order ID using the `examples` module.
3. `http`: This function demonstrates how to cancel and replace an order using the HTTP protocol. It sets up an HTTP provider, then cancels all orders and replaces an order by client order ID using the `examples` module.

