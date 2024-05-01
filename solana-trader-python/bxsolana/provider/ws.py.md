# ws.py

The `ws.py` file defines a `WsProvider` class for interacting with a WebSocket-based JSON-RPC API. This class extends the `Provider` class and implements methods for connecting to the API, sending requests, and handling responses.

Here's a brief overview of the class and its methods:

* `__init__`: Initializes a new instance of the `WsProvider` class. It sets up the WebSocket connection with the appropriate headers and loads the private key from the environment or a provided string.
* `connect`: Connects to the WebSocket API.
* `private_key`: Returns the private key.
* `close`: Closes the WebSocket connection.
* `_unary_unary`: Sends a unary-unary request to the API. This means it sends a single request and expects a single response. It also handles the renaming of "clientOrderId" and "orderId" fields to "clientOrderID" and "orderID", respectively.
* `_unary_stream`: Sends a unary-stream request to the API. This means it sends a single request and expects a stream of responses. It subscribes to updates for a specific subscription ID and yields the responses as they arrive.

The file also defines several helper functions:

* `_ws_endpoint`: Extracts the endpoint from a route.
* `ws`, `ws_testnet`, `ws_devnet`, `ws_local`: These functions return a new instance of the `WsProvider` class with the appropriate endpoint.
* `_validated_response`: Validates the response from the API. It checks that the response is a dictionary, does not contain a "message" field (which would indicate an error), and contains all the expected fields.
* `camelcase`: Converts a string to camel case. It's used in `_validated_response` to match the field names in the response with the field names in the expected response type.
