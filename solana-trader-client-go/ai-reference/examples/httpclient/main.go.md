# main.go

The `main.go` file is the entry point of the application. It's written in Go and it's part of a trading client for the Solana blockchain. Here's a breakdown of its main components:

1. `httpClient` and `httpClientWithTimeout` functions: These functions create an HTTP client based on the environment configuration loaded from `config.Load()`. The client is used to interact with different environments (local, testnet, mainnet).
2. `main` function: This function initializes the logger and runs the `run` function, which executes a series of HTTP calls to the Solana trading API. If any of these calls fail, the application logs a fatal error.
3. `run` function: This function executes a series of HTTP calls to the Solana trading API. Each call is wrapped in the `logCall` function, which logs the name of the call and whether it failed. If any call fails, the `run` function returns `true`.
4. `logCall` function: This function logs the name of the HTTP call and whether it failed. It's used to wrap each HTTP call in the `run` function.
5. The file also contains code for placing and cancelling orders, but this code is commented out. If enabled, it would require the `PUBLIC_KEY`, `OPEN_ORDERS`, and `PAYER` environment variables to be set.

The rest of `main.go` file contains a series of functions that make HTTP calls to different endpoints of a trading API. Each function creates an HTTP client, sets a timeout for the request, makes the request, logs the result, and returns a boolean indicating whether an error occurred. Here's a breakdown of each function:

1. `callMarketsHTTP`: This function makes a request to the `GetMarketsV2` endpoint of the API, which likely returns information about different markets.
2. `callBundleResultHTTP`: This function makes a request to the `GetBundleResult` endpoint of the API with a hardcoded "uuid". This endpoint likely returns some sort of bundled result.
3. `callOrderbookHTTP`: This function makes three requests to the `GetOrderbookV2` endpoint of the API for different markets ("SOL-USDT", "SOLUSDT", "SOL:USDC"). This endpoint likely returns the order book for a specific market.
4. `callMarketDepthHTTP`: This function makes a request to the `GetMarketDepthV2` endpoint of the API for the "SOL-USDC" market. This endpoint likely returns the market depth for a specific market.
5. `callUnsettledHTTP`: This function makes a request to the `GetUnsettledV2` endpoint of the API for the "SOLUSDT" market and a specific account. This endpoint likely returns unsettled trades for a specific account in a specific market.
6. `callGetAccountBalanceHTTP`: This function makes a request to the `GetAccountBalance` endpoint of the API for a specific account. This endpoint likely returns the balance of a specific account.
7. `callGetTokenAccountsHTTP`: This function makes a request to the `GetTokenAccounts` endpoint of the API for a specific owner address. This endpoint likely returns the token accounts for a specific owner.
8. `callTradesHTTP`: This function makes a request to the `GetTrades` endpoint of the API for the "SOLUSDT" market. This endpoint likely returns recent trades for a specific market.
9. `callPoolsHTTP`: This function makes a request to the `GetPools` endpoint of the API, which likely returns information about different liquidity pools.
10. `callRaydiumPoolReserve`: This function makes a request to the `GetRaydiumPoolReserve` endpoint of the API, which likely returns information about the reserves of specific Raydium pools.
11. `callRaydiumPools`: This function makes a request to the `GetRaydiumPools` endpoint of the API, which likely returns information about Raydium pools.
12. `callGetRateLimit`: This function makes a request to the `GetRateLimit` endpoint of the API, which likely returns information about the rate limit of the API.
13. `callGetTransaction`: This function makes a request to the `GetTransaction` endpoint of the API, which likely returns information about a specific transaction.
14. `callPriceHTTP`: This function makes a request to the `GetPrice` endpoint of the API, which likely returns the price of specific tokens.
15. `callRaydiumPrices`: This function makes a request to the `GetRaydiumPrices` endpoint of the API, which likely returns the price of specific tokens on Raydium.
16. `callJupiterPrices`: This function makes a request to the `GetJupiterPrices` endpoint of the API, which likely returns the price of specific tokens on Jupiter.
17. `callTickersHTTP`: This function makes a request to the `GetTickersV2` endpoint of the API, which likely returns ticker information for a specific market.
18. `callGetQuotesHTTP`: This function makes a request to the `GetQuotes` endpoint of the API, which likely returns quote information for a specific token pair.
19. `callGetRaydiumQuotes`: This function makes a request to the `GetRaydiumQuotes` endpoint of the API, which likely returns quote information for a specific token pair on Raydium.
20. `callGetJupiterQuotes`: This function makes a request to the `GetJupiterQuotes` endpoint of the API, which likely returns quote information for a specific token pair on Jupiter.
21. `callPlaceOrderHTTP`: This function makes a request to place an order on a specific market. It first creates an order without submitting it, then signs and submits the order.
22. `callPlaceOrderHTTPWithPriorityFee`: This function is similar to `callPlaceOrderHTTP`, but it also includes a priority fee for the order.
23. `callPlaceOrderBundleUsingBatch`: This function places an order with a bundle using a Raydium swap. It first posts a Raydium swap, then signs the transaction and submits it as a batch.
24. `callPlaceOrderBundle`: This function places an order with a bundle using a Raydium swap. It first posts a Raydium swap, then signs the transaction and submits it.
25.
26. `callCancelByClientOrderIDHTTP`: This function cancels an order by its client ID after a delay of 60 seconds.
27. `callPostSettleHTTP`: This function submits a settlement request for a specific market after a delay of 60 seconds.
28. `cancelAll`: This function places two orders in the order book, checks if the orders are there, cancels all the orders, and then checks if all orders are cancelled. It also calls the `callPostSettleHTTP` function at the end.
29. `callReplaceByClientOrderID`: This function replaces an order in the order book by its client ID. It first places an order, checks if the order is in the order book, replaces the order with a new one, checks if the new order is in the order book, and finally cancels all orders.
30. `callReplaceOrder`: This function replaces an order in the order book. It first places an order, checks if the order is in the order book, replaces the order with a new one, checks if the new order is in the order book, and finally cancels all orders. The difference with the previous function is that this one uses the order ID to replace the order instead of the client ID.
31. `callGetRecentBlockHash`: This function makes a request to get the recent block hash from the blockchain.
32. `callTradeSwap`: This function submits a trade swap request. It logs the start of the test, creates a context with a timeout, and submits the trade swap request. If there's an error, it logs the error and returns true. If the request is successful, it logs the transaction signature and returns false.
33. `callRaydiumSwap`: This function submits a Raydium swap request. It follows a similar pattern to `callTradeSwap`, but the request is specific to a Raydium swap.
34. `callRaydiumRouteSwap`: This function submits a Raydium route swap request. It also follows a similar pattern, but the request is specific to a Raydium route swap.
35. `callJupiterRouteSwap`: This function submits a Jupiter route swap request. It follows a similar pattern, but the request is specific to a Jupiter route swap.
36. `callJupiterSwap`: This function submits a Jupiter swap request. It follows a similar pattern, but the request is specific to a Jupiter swap.
37. `callJupiterSwapInstructions`: This function submits a Jupiter swap instructions request. It follows a similar pattern, but the request is specific to a Jupiter swap instructions.
38. `callRouteTradeSwap`: This function submits a route trade swap request. It follows a similar pattern, but the request is specific to a route trade swap.
39. `callGetPriorityFee`: This function gets the priority fee. It creates a context with a timeout, makes the request, and logs the priority fee or any error that occurs.







\
