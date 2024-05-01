# transaction\_request\_utils.py

The `transaction_request_utils.py` file contains a function `do_transaction_requests` that performs various transaction-related requests to a trading platform. Each request is sent using the provided `api` object, which is an instance of the `Provider` class. The responses are printed to the console.

Here's a brief overview of each request:

1. `submit_order_with_client_id`: Submits an order with a specified client ID. This is a helper function used by `submit_order`.
2. `submit_order`: Submits an order to sell 0.1 SOL for USDC at a price of 150,000 USD/SOL. It generates a random client ID for the order and returns this ID along with the signature of the order.
3. `submit_replace_by_client_order_id`: Submits a request to replace an order by its client ID. The new order is to sell 0.1 SOL for USDC at a price of 150,000 USD/SOL.
4. `submit_replace_order`: Submits a request to replace an order. The new order is to sell 0.1 SOL for USDC at a price of 150,000 USD/SOL.
5. `submit_cancel_order`: Submits a request to cancel an order.
6. `submit_cancel_by_client_order_id`: Submits a request to cancel an order by its client ID.
7. `submit_settle`: Submits a request to settle an order.
8. `mark_transaction_with_memo`: Marks a transaction with a memo. This function first posts a trade swap request, then adds a memo to the serialized transaction, signs the transaction with a private key, and finally submits the signed transaction.
