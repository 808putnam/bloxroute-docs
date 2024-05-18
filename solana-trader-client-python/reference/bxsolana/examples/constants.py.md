# constants.py

The `constants.py` file defines several constants that are used throughout the application, particularly for interacting with the trading API.

The file also attempts to load these values from a `test_state.json` file. If this file exists and contains the appropriate keys, the constants are updated with the values from the file. If the file does not exist or an error occurs while reading it, the exception is ignored and the constants retain their default values.

This setup allows the application to use default values for testing or development, but easily switch to different values for production or different testing scenarios by updating the `test_state.json` file.

Here's a brief overview of each constant:

* `SIDE_BID` and `SIDE_ASK`: These constants represent the two sides of a trade. "bid" is a buy order, and "ask" is a sell order.
* `TYPE_LIMIT`, `TYPE_IOC`, and `TYPE_POST_ONLY`: These constants represent different types of orders that can be placed on the trading platform.
* `PUBLIC_KEY`, `USDC_WALLET`, `OPEN_ORDERS`, `MARKET`, and `ORDER_ID`: These constants are placeholders for values that will be used in the trading API. They are initially set to some default values.

