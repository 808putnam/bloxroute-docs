# ws.go

The `ws.go` file defines a `WS` struct and associated methods for handling WebSocket connections. Here's a breakdown:

1. `WS`: This struct represents a WebSocket connection. It includes fields for managing the connection, such as a mutex for message handling, a context for managing goroutines, a channel for writing messages, and maps for tracking requests and subscriptions.
2. `NewWS`: This function creates a new `WS` instance. It connects to a WebSocket endpoint, creates a new context, initializes the `WS` struct, and starts the read, write, and ping loops in separate goroutines.
3. `connect`: This function connects to a WebSocket endpoint with a specified authorization header. It sets several headers, including an authorization header and headers for the SDK name and version.
4. `readLoop`: This method continuously reads messages from the WebSocket connection. It handles different types of messages, such as RPC responses and subscription updates. If an error occurs while reading a message, it attempts to reconnect to the WebSocket endpoint.
5. `writeLoop`: This method continuously writes messages to the WebSocket connection. If an error occurs while writing a message, it closes the connection.
6. `pingLoop`: This method continuously sends ping messages to the WebSocket connection at a specified interval. If an error occurs while sending a ping message, it closes the connection.
7. `processRPCResponse`: This method processes an RPC response. It finds the request associated with the response and sends the response to the request's channel.
8. `processSubscriptionUpdate`: Processes updates from a subscription, deserializes the feed update, and sends the result to the subscription channel.
9. `Request`: Sends a JSON-RPC request over the WebSocket connection, waits for a response, and unmarshals the response into the provided response message.
10. `request`: A helper function for `Request` that sends a JSON-RPC request, sets up a listener for the response, and handles the response or any errors.
11. `WSStreamAny`: Starts a WebSocket stream with any type of data, marshals the stream parameters, and returns a function to receive the streamed data.
12. `WSStreamProto`: Similar to `WSStreamAny`, but specifically for streams of Protocol Buffers messages.
13. `wsStream`: A helper function for `WSStreamAny` and `WSStreamProto` that starts a WebSocket stream, subscribes to a stream, and returns a function to receive the streamed data.
14. `Close`: Closes the WebSocket connection and all active subscriptions.

In summary, this file provides a way to manage WebSocket connections, including reading and writing messages, handling RPC responses and subscription updates, and managing connection errors.
