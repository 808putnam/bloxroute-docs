# main.py

The `main.py` file is the main entry point for a trading bot that interacts with a trading platform using three different protocols: WebSocket (WS), gRPC, and HTTP.

The script retrieves environment variables for public key, private key, open orders, base token wallet, and quote token wallet. It also sets up some constants for the market address, order side, order type, order price, and order amount.

&#x20;The script is designed to be run as a standalone program. When run, it starts the asyncio event loop and runs the `main` function. The `main` function is an asynchronous function that runs three other asynchronous functions: `ws`, `grpc`, and `http`.

1. `ws`: This function demonstrates how to create and submit an order using the WebSocket protocol. It first posts an order request, then signs the transaction, and finally submits the signed transaction. It also prints the status of the transaction bundle.
2. `grpc`: This function demonstrates how to perform a Raydium swap using the gRPC protocol. It first posts a swap request, then signs the transaction, and finally submits the signed transaction. It also prints the status of the transaction bundle.
3. `http`: This function demonstrates how to perform a Raydium swap using the HTTP protocol. It first posts a swap request, then signs the transaction, and finally submits the signed transaction. It also prints the status of the transaction bundle.

