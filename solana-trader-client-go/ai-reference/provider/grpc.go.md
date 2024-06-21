# grpc.go

Pick up at line 115

The `grpc.go` file in the `provider` package defines a `GRPCClient` struct and methods for interacting with a remote gRPC server. Here's a brief overview of its contents:

1. `GRPCClient` struct: This struct has fields for the gRPC API client (`apiClient`), a Solana private key (`privateKey`), and a store for recent block hashes (`recentBlockHashStore`).
2. `NewGRPCClient`, `NewGRPCTestnet`, `NewGRPCDevnet`, `NewGRPCLocal`: These functions create a new `GRPCClient` connected to the Mainnet, Testnet, Devnet, and local Trader API, respectively.
3. `blxrCredentials` struct: This struct implements the `credentials.PerRPCCredentials` interface for providing custom authorization for the gRPC calls.
4. `NewGRPCClientWithOpts`: This function creates a new `GRPCClient` with custom options. It sets up the transport credentials, per-RPC credentials, and other dial options, and then dials the gRPC server. It also starts a goroutine to cache the recent block hash if the `CacheBlockHash` option is set.
5. `RecentBlockHash`: This method gets the recent block hash from the `recentBlockHashStore`.
6. `GetRecentBlockHash`: Fetches the most recent block hash from the blockchain.
7. `GetPriorityFee`: Fetches a priority fee estimate for a given percentile.
8. `GetRateLimit`: Fetches details of an account's rate limits.
9. `GetTransaction`: Fetches details of a recent transaction.
10. `GetRaydiumPoolReserve`: Fetches pool details for a given set of pairs or addresses on Raydium.
11. `GetRaydiumPools`: Fetches pools on Raydium.
12. `GetRaydiumQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it on Raydium.
13. `GetRaydiumPrices`: Fetches the USDC price of requested tokens on Raydium.
14. `PostRaydiumSwap`: Returns a partially signed transaction(s) for submitting a swap request on Raydium.
15. `PostRaydiumRouteSwap`: Returns a partially signed transaction(s) for submitting a swap request on Raydium.
16. `GetJupiterQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it on Jupiter.
17. `GetJupiterPrices`: Fetches the USDC price of requested tokens on Jupiter.
18. `PostJupiterSwap`: Returns a partially signed transaction(s) for submitting a swap request on Jupiter.
19. `PostJupiterSwapInstructions`: Returns instructions to build a transaction and submit it on Jupiter.
20. `PostRaydiumSwapInstructions`: Returns instructions to build a transaction and submit it on Raydium.
21. `PostJupiterRouteSwap`: Returns a partially signed transaction(s) for submitting a swap request on Jupiter.
22. `GetOrderbook`: Fetches the requested market's orderbook (e.g. asks and bids).
23. `GetMarketDepth`: Fetches the requested market's coalesced price data (e.g. asks and bids).
24. `GetPools`: Fetches pools for given projects.
25. `GetTrades`: Fetches the requested market's currently executing trades.
26. `GetTickers`: Fetches market tickers. If the market parameter is empty, it fetches tickers for all markets.
27. `GetOpenOrders`: Fetches all open orders for a given owner address and market.
28. `GetOrderByID`: Fetches an order by its ID.
29. `GetUnsettled`: Fetches all OpenOrders accounts for a given market with the amounts of unsettled funds.
30. `GetMarkets`: Fetches the list of all available named markets.
31. `GetBundleResult`: Fetches the result of a bundle operation using its UUID.
32. `GetAccountBalance`: Fetches all tokens associated with the owner address including Serum unsettled amounts.
33. `GetTokenAccounts`: Fetches all tokens associated with the owner address.
34. `GetPrice`: Fetches the USDC price of requested tokens.
35. `GetQuotes`: Fetches the possible amount(s) of outToken for an inToken and the route to achieve it.
36. `SignAndSubmit`: Signs the given transaction and submits it.
37. `signAndSubmitBatch`: Signs the given transactions and submits them in a batch.
38. `PostTradeSwap`: Returns a partially signed transaction for submitting a swap request.
39. `PostRouteTradeSwap`: Returns a partially signed transaction(s) for submitting a swap request.
40. `PostOrder`: Returns a partially signed transaction for placing a Serum market order.
41. `PostSubmit`: Posts the transaction string to the Solana network.
42. `PostSubmitBatch`: Posts a bundle of transactions string based on a specific SubmitStrategy to the Solana network.
43. `PostSubmitV2`: Posts the transaction string to the Solana network.
44. `PostSubmitBatchV2`: Posts a bundle of transactions string based on a specific SubmitStrategy to the Solana network.
45. `SubmitTradeSwap`: Builds a TradeSwap transaction then signs it, and submits to the network.
46. `SubmitRouteTradeSwap`: Builds a RouteTradeSwap transaction then signs it, and submits to the network.
47. `SubmitRaydiumSwap`: Builds a Raydium Swap transaction then signs it, and submits to the network.
48. `SubmitRaydiumRouteSwap`: Builds a Raydium RouteSwap transaction then signs it, and submits to the network.
49. `SubmitJupiterSwap`: This function builds a Jupiter Swap transaction, signs it, and submits it to the network. It first calls `PostJupiterSwap` to get the transaction details, then signs and submits the transaction using `signAndSubmitBatch`.
50. `SubmitJupiterSwapInstructions`: This function builds a Jupiter Swap transaction using specific instructions, signs it, and submits it to the network. It first calls `PostJupiterSwapInstructions` to get the swap instructions, then builds the transaction using these instructions. It sets the fee payer, recent block hash, and signs the transaction. Finally, it submits the transaction using `signAndSubmitBatch`.
51. `SubmitRaydiumSwapInstructions`: This function builds a Raydium Swap transaction using specific instructions, signs it, and submits it to the network. It first calls `PostRaydiumSwapInstructions` to get the swap instructions, then builds the transaction using these instructions. It sets the fee payer, recent block hash, and signs the transaction. Finally, it submits the transaction using `signAndSubmitBatch`.
52. `SubmitJupiterRouteSwap`: This function builds a Jupiter RouteSwap transaction, signs it, and submits it to the network. It first calls `PostJupiterRouteSwap` to get the transaction details, then signs and submits the transaction using `signAndSubmitBatch`.
53. `SubmitOrder`: This function builds a Serum market order, signs it, and submits it to the network. It first calls `PostOrder` to get the order details, then signs and submits the order using `SignAndSubmit`.
54. `PostCancelOrder`: This function builds a Serum cancel order. It takes in parameters such as the order ID, side, owner, market, open orders, and project, and makes a `PostCancelOrder` request to the API.
55. `SubmitCancelOrder`: This function builds a Serum cancel order, signs it, and submits it to the network. It first calls `PostCancelOrder` to get the order details, then signs and submits the order using `SignAndSubmit`.
56. `PostCancelByClientOrderID`: This function builds a Serum cancel order by client ID. It takes in parameters such as the client order ID, owner, market, open orders, and project, and makes a `PostCancelByClientOrderID` request to the API.
57. `SubmitCancelByClientOrderID`: This function builds a Serum cancel order by client ID, signs it, and submits it to the network. It first calls `PostCancelByClientOrderID` to get the order details, then signs and submits the order using `SignAndSubmit`.
58. `PostCancelAll`: This function builds a request to cancel all orders for a given market and owner. It takes in parameters such as the market, owner, open orders, and project, and makes a `PostCancelAll` request to the API.
59. `SubmitCancelAll`: This function signs and submits a batch of cancel all orders to the network. It first calls `PostCancelAll` to get the order details, then signs and submits the orders using `signAndSubmitBatch`.
60. `PostSettle`: This function returns a partially signed transaction for settling market funds. It takes in parameters such as the owner, market, base token wallet, quote token wallet, open orders account, and project, and makes a `PostSettle` request to the API.
61. `SubmitSettle`: This function builds a market SubmitSettle transaction, signs it, and submits it to the network. It first calls `PostSettle` to get the transaction details, then signs and submits the transaction using `SignAndSubmit`.
62. `PostReplaceByClientOrderID`: This function builds a request to replace an order by client ID. It takes in parameters such as the owner, payer, market, side, types, amount, price, project, and options, and makes a `PostReplaceByClientOrderID` request to the API.
63. `SubmitReplaceByClientOrderID`: This function builds a replace order by client ID, signs it, and submits it to the network. It first calls `PostReplaceByClientOrderID` to get the order details, then signs and submits the order using `SignAndSubmit`.
64. `PostReplaceOrder`: This function sends a request to replace an existing order on the blockchain. It takes in parameters such as the order ID, owner, payer, market, side, types, amount, price, project, and options, and makes a `PostReplaceOrder` request to the API.
65. `SubmitReplaceOrder`: This function sends a request to replace an existing order on the blockchain, signs it, and submits it to the network. It first calls `PostReplaceOrder` to get the order details, then signs and submits the order using `SignAndSubmit`.
66. `GetOrderbookStream`: This function subscribes to a stream for changes to the requested market updates (e.g. asks and bids). It takes in parameters such as the markets and limit, and makes a `GetOrderbooksStream` request to the API.
67. `GetMarketDepthsStream`: This function subscribes to a stream for changes to the requested market data updates (e.g. asks and bids). It takes in parameters such as the markets and limit, and makes a `GetMarketDepthsStream` request to the API.
68. `GetTradesStream`: This function subscribes to a stream for trades as they execute. It takes in parameters such as the market and limit, and makes a `GetTradesStream` request to the API.
69. `GetOrderStatusStream`: This function subscribes to a stream that shows updates to the owner's orders. It takes in parameters such as the market and owner address, and makes a `GetOrderStatusStream` request to the API.
70. `GetRecentBlockHashStream`: This function subscribes to a stream for getting recent block hash. It makes a `GetRecentBlockHashStream` request to the API.
71. `GetQuotesStream`: This function subscribes to a stream for getting recent quotes of tokens of interest. It takes in parameters such as the projects and token pairs, and makes a `GetQuotesStream` request to the API.
72. `GetPoolReservesStream`: This function subscribes to a stream for getting recent quotes of tokens of interest. It takes in a `GetPoolReservesStreamRequest` and makes a `GetPoolReservesStream` request to the API.
73. `GetPricesStream`: This function subscribes to a stream for getting recent prices of tokens of interest. It takes in parameters such as the projects and tokens, and makes a `GetPricesStream` request to the API.
74. `GetTickersStream`: This function subscribes to a stream for getting recent tickers of specified markets. It takes in a `GetTickersStreamRequest` and makes a `GetTickersStream` request to the API.
75. `GetSwapsStream`: This function subscribes to a stream for getting recent swaps on projects & markets of interest. It takes in parameters such as the projects, markets, and a boolean to include failed swaps or not, and makes a `GetSwapsStream` request to the API.
76. `GetNewRaydiumPoolsStream`: This function subscribes to a stream for getting recent swaps on projects & markets of interest. It makes a `GetNewRaydiumPoolsStream` request to the API.
77. `GetBlockStream`: This function subscribes to a stream for getting recent blocks. It makes a `GetBlockStream` request to the API.
78. `GetPriorityFeeStream`: This function subscribes to a stream of priority fees for a given percentile. It takes in parameters such as the project and percentile, and makes a `GetPriorityFeeStream` request to the API.
79. `GetBundleTipStream`: This function subscribes to a stream of bundle tip percentiles. It makes a `GetBundleTipStream` request to the API.
80. `GetOrderbookV2`: This function returns the requested market's orderbook (e.g. asks and bids). It takes in parameters such as the market and limit, and makes a `GetOrderbookV2` request to the API.
81. `GetMarketDepthV2`: This function returns the requested market's coalesced price data (e.g. asks and bids). It takes in parameters such as the market and limit, and makes a `GetMarketDepthV2` request to the API.
82. `GetTickersV2`: This function returns the requested market tickets. It takes in the market as a parameter and makes a `GetTickersV2` request to the API.
83. `GetOpenOrdersV2`: This function returns all open orders by owner address and market. It takes in parameters such as the market, owner, open orders address, order ID, and client order ID, and makes a `GetOpenOrdersV2` request to the API.
84. `GetUnsettledV2`: This function returns all OpenOrders accounts for a given market with the amounts of unsettled funds. It takes in parameters such as the market and owner address, and makes a `GetUnsettledV2` request to the API.
85. `GetMarketsV2`: This function returns the list of all available named markets. It makes a `GetMarketsV2` request to the API.
86. `PostOrderV2` and `PostOrderV2WithPriorityFee`: These functions return a partially signed transaction for placing a Serum market order. They take in parameters such as the owner, payer, market, side, order type, amount, price, and bundle tip, and make a `PostOrder` request to the API.
87. `SubmitOrderV2` and `SubmitOrderV2WithPriorityFee`: These functions build a Serum market order, sign it, and submit it to the network. They use the `PostOrderV2` and `PostOrderV2WithPriorityFee` functions to create the order, then sign and submit the order.
88. `PostCancelOrderV2`: This function builds a Serum cancel order. It takes in parameters such as the order ID, side, owner, market, and open orders, and makes a `PostCancelOrder` request to the API.
89. `SubmitCancelOrderV2`: This function builds a Serum cancel order, signs it, and submits it to the network. It uses the `PostCancelOrderV2` function to create the order, then signs and submits the order.
90. `PostSettleV2`: This function returns a partially signed transaction for settling market funds. It takes in parameters such as the owner, market, base token wallet, quote token wallet, and open orders account, and makes a `PostSettle` request to the API.
91. `SubmitSettleV2`: This function builds a market SubmitSettle transaction, signs it, and submits it to the network. It uses the `PostSettleV2` function to create the order, then signs and submits the order.
92. `PostReplaceOrderV2`: This function returns a partially signed transaction for replacing a Serum market order. It takes in parameters such as the order ID, owner, payer, market, side, order type, amount, price, and makes a `PostReplaceOrder` request to the API.
93. `SubmitReplaceOrderV2`: This function builds a Serum replace order, signs it, and submits it to the network. It uses the `PostReplaceOrderV2` function to create the order, then signs and submits the order.

\




\




