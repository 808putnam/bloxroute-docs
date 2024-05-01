# base.py

The `base.py` file defines an abstract base class `Provider` that is used as a blueprint for creating other classes. This class inherits from `api.ApiStub` and `ABC` (Abstract Base Class).

The `Provider` class has the methods show below. Each method returns the signature of the submitted transaction(s) or the response from the batch submission, which can be used to verify that the transaction was successfully submitted.

The `NotConnectedException` is a custom exception class. It's used to signal that a required connection is not established.

* `__aenter__` and `__aexit__`: These are special methods in Python that define a context manager. This allows the class's instances to be used with the `with` statement. `__aenter__` is called when entering the context and `__aexit__` is called when exiting the context. In this case, a connection is established when entering the context and closed when exiting.
* `connect`, `private_key`, and `close`: These are abstract methods, meaning they must be implemented by any non-abstract child class. `connect` and `close` are coroutines, meaning they are designed to be used with Python's `async` and `await` keywords for asynchronous programming.
* `require_private_key`: This method returns the private key if it's set, otherwise it raises an `EnvironmentError`.
* `submit_order`: This is a coroutine that is designed to submit an order, but the implementation is not shown in the provided code.
* `submit_cancel_order`: This method cancels an order given its ID and other details. It sends a POST request to cancel the order, signs the resulting transaction with a private key, and then submits the signed transaction.
* `submit_cancel_by_client_order_id`: This method is similar to `submit_cancel_order`, but it cancels an order given a client order ID instead of an order ID.
* `submit_cancel_all`: This method cancels all orders for a given market and owner. It sends a POST request to cancel all orders, signs each resulting transaction with a private key, and then submits each signed transaction.
* `submit_settle`: This method settles an order given its details. It sends a POST request to settle the order, signs the resulting transaction with a private key, and then submits the signed transaction.
* `submit_replace_by_client_order_id`: This method replaces an order given its client order ID and other details. It sends a POST request to replace the order, signs the resulting transaction with a private key, and then submits the signed transaction.
* `submit_replace_order`: This method is similar to `submit_replace_by_client_order_id`, but it replaces an order given an order ID instead of a client order ID.
* `submit_post_trade_swap`: This method posts a trade swap given various details. It sends a POST request to perform the trade swap, signs each resulting transaction with a private key, and then submits each signed transaction in a batch.
* `submit_post_route_trade_swap`: This method is similar to `submit_post_trade_swap`, but it posts a route trade swap instead of a trade swap.
