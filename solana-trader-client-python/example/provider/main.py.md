# main.py

The `main.py` file is the main entry point for a trading bot that interacts with a trading platform using three different protocols: HTTP, WebSocket (WS), and gRPC.

The script retrieves environment variables for the API environment, whether to run slow streams, and whether to run trades. It also validates the API environment value.

The script is designed to be run as a standalone program. When run, it starts the asyncio event loop and runs the `main` function. The `main` function is an asynchronous function that runs three other asynchronous functions: `http`, `ws`, and `grpc`.

1. `http`: This function demonstrates how to create and submit an order using the HTTP protocol. It first sets up the HTTP provider based on the API environment, then performs a series of requests and transaction requests using the `do_requests` and `do_transaction_requests` functions from the `examples` module.
2. `ws`: This function demonstrates how to create and submit an order using the WebSocket protocol. It first sets up the WebSocket provider based on the API environment, then performs a series of requests, transaction requests, and streams using the `do_requests`, `do_transaction_requests`, and `do_stream` functions from the `examples` module.
3. `grpc`: This function demonstrates how to create and submit an order using the gRPC protocol. It first sets up the gRPC provider based on the API environment, then performs a series of requests, transaction requests, and streams using the `do_requests`, `do_transaction_requests`, and `do_stream` functions from the `examples` module.

