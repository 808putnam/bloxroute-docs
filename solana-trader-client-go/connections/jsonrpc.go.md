# jsonrpc.go

The `jsonrpc.go` file defines several types and methods for handling JSON-RPC subscriptions and unsubscriptions. Here's a breakdown:

1. `FeedUpdate`: This struct represents a feed update from a subscription. It includes the subscription ID and the result of the update, which is a raw JSON message.
2. `SubscribeParams`: This struct represents the parameters for a subscription. It includes the stream name and options for the stream, which are a raw JSON message. It also includes methods to marshal and unmarshal these parameters to and from JSON.
3. `UnsubscribeParams`: This struct represents the parameters for an unsubscription. It includes the subscription ID. It also includes methods to marshal and unmarshal these parameters to and from JSON.

In summary, this file provides types and methods for handling JSON-RPC subscriptions and unsubscriptions, including marshaling and unmarshaling the parameters and handling feed updates.
