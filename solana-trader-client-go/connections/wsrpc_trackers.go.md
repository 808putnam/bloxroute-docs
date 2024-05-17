# wsrpc\_trackers.go

The `wsrpc_trackers.go` file defines several types and methods for tracking WebSocket RPC subscriptions and requests. Here's a breakdown:

1. `subscriptionEntry`: This struct represents an active subscription on a connection. It includes a channel to send updates on, a boolean to indicate if the subscription is active, and a cancel function to cancel the subscription.
2. `close()`: This method on the `subscriptionEntry` struct closes the update channel and cancels the subscription.
3. `responseUpdate`: This struct represents an update to a response. It includes the response itself and a boolean to indicate if the lock is held.
4. `requestTracker`: This struct is used to track a request. It includes a channel to send response updates on and a boolean to indicate if a lock is required. The lock can be used to ensure that processing completes before the next message is processed, which can be useful for registering a subscription before processing any potential updates on the connection.

In summary, this file provides types and methods for tracking WebSocket RPC subscriptions and requests, including handling
