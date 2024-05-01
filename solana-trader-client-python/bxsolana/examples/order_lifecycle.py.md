# order\_lifecycle.py

The `order_lifecycle.py` file defines an asynchronous function `order_lifecycle` that simulates the lifecycle of an order in the trading system. This lifecycle includes placing an order, waiting for it to be opened, cancelling the order, and settling the funds. It prints messages at each step to indicate the progress of the order.

Here's a brief overview of each step:

1. `oss = p2.get_order_status_stream(...)`: This line starts a stream of order status updates for a specific market and owner.
2. `task = asyncio.create_task(oss.__anext__())`: This line creates a task that waits for the next order status update. This allows the function to continue executing other code while waiting for updates.
3. `client_order_id = await place_order(...)`: This line places an order with the specified parameters. It waits for the order to be placed and then stores the client order ID.
4. `async with async_timeout.timeout(crank_timeout)`: This block waits for the order to be opened. If the order status is `OPEN`, it prints a success message. If the order status is anything else, it prints an error message. If no update is received within `crank_timeout` seconds, it raises an exception.
5. `await cancel_order(...)`: This line cancels the previously placed order. It then waits for the order status to be `CANCELLED` in the same way as before.
6. `await settle_funds(...)`: This line settles the funds associated with the order.

