# ws.go

The `ws.go` file appears to be part of a client library for interacting with a trading or financial API over WebSockets. It defines a `WSClient` struct and associated methods for connecting to the API and fetching the recent block hash. Here's a brief overview of what each function does:

* `NewWSClient`: Connects to the Mainnet Trader API and returns a new `WSClient` instance.
* `NewWSClientTestnet`: Connects to the Testnet Trader API and returns a new `WSClient` instance.
* `NewWSClientDevnet`: Connects to the Devnet Trader API and returns a new `WSClient` instance.
* `NewWSClientLocal`: Connects to the local Trader API and returns a new `WSClient` instance.
* `NewWSClientWithOpts`: Connects to a custom Trader API specified by the `RPCOpts` argument and returns a new `WSClient` instance. It also initializes the `recentBlockHashStore` of the `WSClient` and starts a goroutine to update the stored block hash if `CacheBlockHash` is true.
* `RecentBlockHash`: Returns the recent block hash by calling the `get` method of the `recentBlockHashStore`.

The `WSClient` struct contains fields for the API endpoint address, the WebSocket connection, the client's private key, and the `recentBlockHashStore`. The `recentBlockHashStore` is used to store and update the most recent block hash in a Solana blockchain network.

The methods below are used to send various types of requests to the API and handle the responses. Each function takes in a context and a request object, sends the request to the server, and returns the server's response or an error. The functions use the `Request` method of the `WSClient`'s connection to send the requests. Here's a brief overview of what each function does:

1. `GetTransaction`: Fetches details of a recent transaction.
2. `GetBundleResult`: Fetches the result of a bundle.
3. `GetRateLimit`: Fetches details of an account's rate limits.
4. `GetRaydiumPoolReserve`: Fetches pool details for a given set of pairs or addresses on Raydium.
5. `GetRaydiumPools`: Fetches pools on Raydium.
6. `GetRaydiumQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it on Raydium.
7. `GetRaydiumPrices`: Fetches the USDC price of requested tokens on Raydium.
8. `PostRaydiumSwap`: Returns a partially signed transaction(s) for submitting a swap request on Raydium.
9. `PostRaydiumRouteSwap`: Returns a partially signed transaction(s) for submitting a swap request on Raydium.
10. `GetJupiterQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it on Jupiter.
11. `GetJupiterPrices`: Fetches the USDC price of requested tokens on Jupiter.
12. `PostJupiterSwap`: Returns a partially signed transaction(s) for submitting a swap request on Jupiter.
13. `PostJupiterSwapInstructions`: Returns instructions to build a transaction and submit it on Jupiter.
14. `PostRaydiumSwapInstructions`: Returns instructions to build a transaction and submit it on Raydium.
15. `PostJupiterRouteSwap`: Returns a partially signed transaction(s) for submitting a swap request on Jupiter.
16. `GetOrderbook`: Returns the requested market's orderbook (e.g. asks and bids).
17. `GetMarketDepth`: Returns the requested market's coalesced price data (e.g. asks and bids).
18. `GetTrades`: Returns the requested market's currently executing trades.
19. `GetPools`: Returns pools for given projects.
20. `GetTickers`: Returns the requested market tickets.
21. `GetOpenOrders`: Returns all open orders by owner address and market.
22. `GetOrderByID`: Returns an order by id.
23. `GetUnsettled`: Returns all OpenOrders accounts for a given market with the amounts of unsettled funds.
24. `GetAccountBalance`: Returns all OpenOrders accounts for a given market with the amounts of unsettled funds.
25. `GetTokenAccounts`: Returns all tokens associated with the owner address.
26. `GetMarkets`: Returns the list of all available named markets.
27. `GetPrice`: Returns the USDC price of requested tokens.
28. `GetQuotes`: Returns the possible amount(s) of outToken for an inToken and the route to achieve it.
29. `GetPriorityFee`: Returns an suggested priority fee based on a given percentile.
30. `PostTradeSwap`: Returns a partially signed transaction for submitting a swap request.
31. `PostTradeSwapWithPriorityFee`: Returns a partially signed transaction for submitting a swap request with a specified compute limit and compute price.
32. `PostRouteTradeSwap`: Returns a partially signed transaction for submitting a swap request.
33. `PostOrder`: Returns a partially signed transaction for placing a Serum market order.
34. `PostSubmit`: Posts the transaction string to the Solana network.
35. `PostSubmitBatch`: Posts a bundle of transactions string based on a specific SubmitStrategy to the Solana network.
36. `PostSubmitV2`: Posts the transaction string to the Solana network with an option to use a bundle.
37. `PostSubmitBatchV2`: Posts a bundle of transactions string based on a specific SubmitStrategy to the Solana network.
38. `SignAndSubmit`: Signs the given transaction and submits it.
39. `SignAndSubmitBatch`: Signs the given transactions and submits them.
40. `SubmitTradeSwap`: Builds a TradeSwap transaction, signs it, and submits it to the network.
41. `SubmitTradeSwapWithPriorityFee`: Builds a TradeSwap transaction with a priority fee, signs it, and submits it to the network.
42. `SubmitRouteTradeSwap`: Builds a RouteTradeSwap transaction, signs it, and submits it to the network.
43. `SubmitRaydiumSwap`: Builds a Raydium Swap transaction, signs it, and submits it to the network.
44. `SubmitRaydiumRouteSwap`: Builds a Raydium RouteSwap transaction, signs it, and submits it to the network.
45. `SubmitJupiterSwap`: Builds a Jupiter Swap transaction, signs it, and submits it to the network.
46. `SubmitJupiterSwapInstructions`: Builds a Jupiter Swap transaction with specific instructions, signs it, and submits it to the network.
47. `SubmitRaydiumSwapInstructions`: Builds a Raydium Swap transaction with specific instructions, signs it, and submits it to the network.
48. `SubmitJupiterRouteSwap`: Builds a Jupiter RouteSwap transaction, signs it, and submits it to the network.
49. `SubmitOrder`: Builds a Serum market order, signs it, and submits it to the network.
50. `PostCancelOrder`: Builds a Serum cancel order.
51. `SubmitCancelOrder`: Builds a Serum cancel order, signs it, and submits it to the network.
52. `PostCancelByClientOrderID`: Builds a Serum cancel order by client ID.
53. `SubmitCancelByClientOrderID`: Builds a Serum cancel order by client ID, signs it, and submits it to the network.
54. `PostCancelAll`: Sends a request to cancel all orders for a given market and owner.
55. `SubmitCancelAll`: Signs and submits the cancel all orders request to the network.
56. `PostSettle`: Returns a partially signed transaction for settling market funds.
57. `SubmitSettle`: Builds a market SubmitSettle transaction, signs it, and submits to the network.
58. `PostReplaceByClientOrderID`: Returns a partially signed transaction for replacing an order by client ID.
59. `SubmitReplaceByClientOrderID`: Builds a replace order transaction by client ID, signs it, and submits it to the network.
60. `PostReplaceOrder`: Returns a partially signed transaction for replacing an order.
61. `SubmitReplaceOrder`: Builds a replace order transaction, signs it, and submits it to the network.
62. `Close`: Closes the WebSocket connection.
63. `GetOrderbooksStream`: Subscribes to a stream for changes to the requested market updates (e.g. asks and bids).
64. `GetMarketDepthsStream`: Subscribes to a stream for changes to the requested market data updates (e.g. asks and bids).
65. `GetTradesStream`: Subscribes to a stream for trades as they execute.
66. `GetNewRaydiumPoolsStream`: Subscribes to a stream for new Raydium Pools when they are created.
67. `GetOrderStatusStream`: Subscribes to a stream that shows updates to the owner's orders.
68. `GetRecentBlockHashStream`: Subscribes to a stream for getting recent block hash.
69. `GetQuotesStream`: Subscribes to a stream for getting recent quotes of tokens of interest.
70. `GetPoolReservesStream`: Subscribes to a stream for getting recent quotes of tokens of interest.
71. `GetPricesStream`: Subscribes to a stream for getting recent quotes of tokens of interest.
72. `GetTickersStream`: Subscribes to a stream for getting recent tickers of specified markets.
73. `GetSwapsStream`: Subscribes to a stream for getting recent swaps on projects & markets of interest.
74. `GetBlockStream`: Subscribes to a stream for getting recent blocks.
75. `GetPriorityFeeStream`: Subscribes to a stream for getting a recent priority fee estimate based on a percentile.
76. `GetBundleTipStream`: Subscribes to a stream of recent bundle tip percentiles.
77. `GetMarketsV2`: Returns the list of all available named markets.
78. `GetBundleResults`: Returns the status of a bundle based on uuid.
79. `GetOrderbookV2`: Returns the requested market's orderbook (e.g. asks and bids).
80. `GetMarketDepthV2`: Returns the requested market's coalesced price data (e.g. asks and bids).
81. `GetTickersV2`: Returns the requested market tickets.
82. `GetOpenOrdersV2`: Returns all open orders by owner address and market.
83. `GetUnsettledV2`: Returns all OpenOrders accounts for a given market with the amounts of unsettled funds.
84. `PostOrderV2`: Returns a partially signed transaction for placing a Serum market order.
85. `SubmitOrderV2`: Builds a Serum market order, signs it, and submits to the network.
86. `PostCancelOrderV2`: Returns a partially signed transaction for cancelling a Serum market order.
87. `SubmitCancelOrderV2`: Builds a Serum cancel order transaction, signs it, and submits it to the network.
88. `PostSettleV2`: Returns a partially signed transaction for settling market funds. Typically, you want to use `SubmitSettleV2` instead of this.
89. `SubmitSettleV2`: Builds a market SubmitSettle transaction, signs it, and submits it to the network.
90. `PostReplaceOrderV2`: Returns a partially signed transaction for replacing an order.
91. `SubmitReplaceOrderV2`: Builds a replace order transaction, signs it, and submits it to the network.

\


