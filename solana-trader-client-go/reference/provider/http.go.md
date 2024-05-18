# http.go

The `http.go` file defines a `HTTPClient` struct and its associated methods for interacting with the Trader API in different environments (Mainnet, Testnet, Devnet, Local).

The `HTTPClient` struct includes fields for the base URL of the API, an HTTP client for making requests, a private key for authentication, and an authentication header.

The file provides several methods for creating new instances of `HTTPClient`:

* `NewHTTPClient`: Connects to Mainnet Trader API.
* `NewHTTPTestnet`: Connects to Testnet Trader API.
* `NewHTTPDevnet`: Connects to Devnet Trader API.
* `NewHTTPLocal`: Connects to local Trader API.
* `NewHTTPClientWithOpts`: Connects to a custom Trader API. This function takes in an HTTP client and RPC options as parameters. If the client is `nil`, it uses a default HTTP client.

Each of these methods uses the `DefaultRPCOpts` function to get the default RPC options for the specified environment, then creates a new `HTTPClient` with these options. The `HTTPClient` can then be used to make requests to the Trader API.

Each method belwo constructs a URL for the API request, makes the request using the `HTTPClient`'s HTTP client, and handles the response. If the request is successful, the method returns the data from the response. If an error occurs, the method returns the error.

Each function takes in a context and other parameters specific to the request, and returns a response object or an error. The functions use the `HTTPPostWithClient` and `HTTPGetWithClient` methods from the `connections` package to make the actual HTTP requests.

1. `GetTransaction`: Fetches details of a recent transaction.
2. `GetRateLimit`: Fetches details of an account's rate limits.
3. `GetRaydiumPoolReserve`: Fetches pool details for a given set of pairs or addresses on Raydium.
4. `GetRaydiumPools`: Fetches pools on Raydium.
5. `GetRaydiumQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it on Raydium.
6. `GetRaydiumPrices`: Fetches the USDC price of requested tokens on Raydium.
7. `PostRaydiumSwap`: Returns a partially signed transaction(s) for submitting a swap request on Raydium.
8. `PostRaydiumRouteSwap`: Returns a partially signed transaction(s) for submitting a swap request on Raydium.
9. `GetJupiterQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it on Jupiter.
10. `GetJupiterPrices`: Fetches the USDC price of requested tokens on Jupiter.
11. `PostJupiterSwap`: Returns a partially signed transaction(s) for submitting a swap request on Jupiter.
12. `PostJupiterSwapInstructions`: Returns a list of instructions that can be used to construct a custom transaction for a Jupiter swap.
13. `PostRaydiumSwapInstructions`: Posts instructions for a Raydium swap transaction.
14. `PostJupiterRouteSwap`: Posts a swap request on Jupiter.
15. `GetOrderbook`: Gets the orderbook (asks and bids) for a specific market.
16. `GetMarketDepth`: Gets the coalesced price data (asks and bids) for a specific market.
17. `GetTrades`: Gets the currently executing trades for a specific market.
18. `GetPools`: Gets pools for given projects.
19. `GetTickers`: Gets the market tickers.
20. `GetOpenOrders`: Gets all open orders by owner address and market.
21. `GetOrderByID`: Gets an order by its ID.
22. `GetMarkets`: Gets the list of all available named markets.
23. `GetUnsettled`: Gets all OpenOrders accounts for a given market with the amounts of unsettled funds.
24. `GetAccountBalance`: Gets all OpenOrders accounts for a given market with the amounts of unsettled funds.
25. `GetTokenAccounts`: Gets token accounts.
26. `GetPrice`: Gets the USDC price of requested tokens.
27. `GetQuotes`: Gets the possible amount(s) of outToken for an inToken and the route to achieve it.
28. `PostSubmit`: Posts the transaction string to the Solana network.
29. `PostSubmitBatch`: Posts a batch of transactions to the Solana network.
30. `PostSubmitV2`: Posts a single transaction to the Solana network.
31. `PostSubmitBatchV2`: Posts a batch of transactions to the Solana network, using version 2 of the API.
32. `SignAndSubmit`: Signs a given transaction and submits it to the network.
33. `SignAndSubmitBatch`: Signs a batch of transactions and submits them to the network.
34. `PostTradeSwap`: Posts a swap request and returns a partially signed transaction.
35. `SubmitTradeSwap`: Builds a TradeSwap transaction, signs it, and submits it to the network.
36. `PostRouteTradeSwap`: Posts a route swap request and returns a partially signed transaction.
37. `SubmitRouteTradeSwap`: Builds a RouteTradeSwap transaction, signs it, and submits it to the network.
38. `SubmitRaydiumSwap`: Builds a Raydium Swap transaction, signs it, and submits it to the network.
39. `SubmitRaydiumRouteSwap`: Builds a Raydium RouteSwap transaction, signs it, and submits it to the network.
40. `SubmitJupiterSwap`: Builds a Jupiter Swap transaction, signs it, and submits it to the network.
41. `SubmitJupiterSwapInstructions`: Builds a Jupiter Swap transaction with specific instructions, signs it, and submits it to the network.
42. `SubmitRaydiumSwapInstructions`: Builds a Raydium Swap transaction, signs it, and submits it to the network.
43. `SubmitJupiterRouteSwap`: Builds a Jupiter RouteSwap transaction, signs it, and submits it to the network.
44. `PostOrder`: Returns a partially signed transaction for placing a Serum market order.
45. `SubmitOrder`: Builds a Serum market order, signs it, and submits it to the network.
46. `PostCancelOrder`: Builds a Serum cancel order.
47. `SubmitCancelOrder`: Builds a Serum cancel order, signs it, and submits it to the network.
48. `PostCancelByClientOrderID`: Builds a Serum cancel order by client ID.
49. `SubmitCancelByClientOrderID`: Builds a Serum cancel order by client ID, signs it, and submits it to the network.
50. `PostCancelAll`: Sends a request to cancel all open orders for a given market and owner.
51. `SubmitCancelAll`: Submits a request to cancel all open orders for a given market and owner, signs it, and submits it to the network.
52. `PostSettle`: Returns a partially signed transaction for settling market funds.
53. `SubmitSettle`: Builds a market SubmitSettle transaction, signs it, and submits it to the network.
54. `PostReplaceByClientOrderID`: Returns a partially signed transaction for replacing an order by client ID.
55. `SubmitReplaceByClientOrderID`: Builds a transaction to replace an order by client ID, signs it, and submits it to the network.
56. `PostReplaceOrder`: Returns a partially signed transaction for replacing an order.
57. `SubmitReplaceOrder`: Builds a transaction to replace an order, signs it, and submits it to the network.
58. `GetRecentBlockHash`: Subscribes to a stream for getting recent block hash.
59. `GetPriorityFee`: Gets the priority fee for a given project and percentile.
60. `GetMarketsV2`: Returns the list of all available named markets.
61. `GetOrderbookV2`: Returns the requested market's orderbook (asks and bids).
62. `GetMarketDepthV2`: Returns the requested market's coalesced price data (asks and bids).
63. `GetTickersV2`: Returns the requested market tickets.
64. `GetOpenOrdersV2`: Returns all open orders by owner address and market.
65. `GetUnsettledV2`: Returns all OpenOrders accounts for a given market with the amounts of unsettled funds.
66. `GetBundleResult`: Returns the bundle result.
67. `PostOrderV2`: Returns a partially signed transaction for placing a Serum market order. Typically, you want to use SubmitOrder instead of this.
68. `PostOrderV2WithPriorityFee`: Returns a partially signed transaction for placing a Serum market order. Typically, you want to use SubmitOrder instead of this.
69. `SubmitOrderV2`: Builds a Serum market order, signs it, and submits to the network.
70. `SubmitOrderV2WithPriorityFee`: Builds a Serum market order, signs it, and submits to the network.
71. `PostCancelOrderV2`: Builds a Serum cancel order.
72. `SubmitCancelOrderV2`: Builds a Serum cancel order, signs and submits it to the network.
73. `PostSettleV2`: Returns a partially signed transaction for settling market funds. Typically, you want to use SubmitSettle instead of this.
74. `SubmitSettleV2`: Builds a market SubmitSettle transaction, signs it, and submits to the network.
75. `PostReplaceOrderV2`: Sends a request to replace an existing order with new parameters. It constructs the request, sends it to the server, and returns the server's response or an error.
76. `SubmitReplaceOrderV2`: Builds a transaction to replace an order, signs it, and submits it to the network. It uses `PostReplaceOrderV2` to create the order, then signs and submits the transaction.
77. `convertSliceArgument`: A helper function that converts a slice of elements implementing the `stringable` interface into a string representation suitable for use in a URL query string.
78. `convertStrSliceArgument`: A helper function that converts a slice of strings into a string representation suitable for use in a URL query string.

\
