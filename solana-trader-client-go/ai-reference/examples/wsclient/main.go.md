# main.go

The `main.go` file is the entry point of a Go application that interacts with the Solana blockchain via the bloXroute Labs' Solana Trader Client using WebSocket (WS) and gRPC.

Here's a brief overview of what the main parts of the file do:

1. `main()`: This function initializes the logger and runs the `run()` function. If `run()` returns `true`, indicating that one or more examples failed, it logs a fatal error.
2. `run()`: This function loads the configuration, creates a new WebSocket client based on the environment specified in the configuration, and then makes a series of calls to various functions that interact with the blockchain. Each of these calls is logged, and if any of them fail, the `failed` variable is set to `true`. The function returns `true` if any calls failed and `false` otherwise.
3. `logCall()`: This function logs the execution of a function and its result. It takes a string representing the name of the function and a function that returns a boolean indicating whether the function failed. It logs the name of the function being executed, executes the function, and if the function returns `true`, logs that the function failed.
4. The file also contains several constants and imports necessary for the application to run.
5. `callMarketsWS`: This function fetches market data from the blockchain. It sends a `GetMarketsV2` request and logs the received market data or any errors that occur. It returns a boolean indicating whether an error occurred (true if there was an error, false otherwise).
6. `callBundleResultWS`: This function fetches the result of a bundle transaction from the blockchain. It sends a `GetBundleResult` request with a specific UUID and logs the received bundle result or any errors that occur. It returns a boolean indicating whether an error occurred (true if there was an error, false otherwise).
7. `callOrderbookWS`: This function fetches orderbook data for three different markets ("SOL-USDT", "SOLUSDT", "SOL:USDT") from the blockchain and logs the received data or any errors that occur.
8. `callMarketDepthWS`: This function fetches market depth data for the "SOL:USDT" market from the blockchain and logs the received data or any errors that occur.
9. `callTradesWS`: This function fetches trade data for the "SOLUSDC" market from the blockchain and logs the received data or any errors that occur.
10. `callPoolsWS`: This function fetches pool data for the Raydium project from the blockchain and logs the received data or any errors that occur.
11. `callGetRateLimitWS`: This function fetches the rate limit from the blockchain and logs the received data or any errors that occur.
12. `callGetTransactionWS`: This function fetches a specific transaction from the blockchain and logs the received data or any errors that occur.
13. `callRaydiumPoolReserveWS`: This function fetches reserve data for specific Raydium pools from the blockchain and logs the received data or any errors that occur.
14. `callRaydiumPoolsWS`: This function fetches pool data for the Raydium project from the blockchain and logs the received data or any errors that occur.
15. `callPriceWS`: This function fetches price data for specific tokens from the blockchain and logs the received data or any errors that occur.
16. `callRaydiumPricesWS`: This function fetches price data for specific tokens from the Raydium project on the blockchain and logs the received data or any errors that occur.
17. `callJupiterPricesWS`: This function fetches price data for specific tokens from the Jupiter project on the blockchain and logs the received data or any errors that occur.
18. `callOpenOrdersWS`: This function fetches open order data for a specific market and user from the blockchain and logs the received data or any errors that occur.
19. `callUnsettledWS`: This function fetches unsettled transactions for a specific market and user from the blockchain and logs the received data or any errors that occur.
20. `callAccountBalanceWS`: This function fetches the balance of a specific account from the blockchain and logs the received data or any errors that occur.
21. `callGetTokenAccountsWS`: This function fetches token accounts for a specific owner from the blockchain and logs the received data or any errors that occur.
22. `callTickersWS`: This function fetches ticker data for a specific market from the blockchain and logs the received data or any errors that occur.
23. `callGetQuotes`: This function fetches quote data for a specific token pair from the blockchain and logs the received data or any errors that occur.
24. `callGetRaydiumQuotes`: This function fetches quote data for a specific token pair from the Raydium project on the blockchain and logs the received data or any errors that occur.
25. `callGetJupiterQuotes`: This function fetches quote data for a specific token pair from the Jupiter project on the blockchain and logs the received data or any errors that occur.
26. `callOrderbookWSStream`: This function starts a stream of orderbook data for a specific market from the blockchain and logs the received data or any errors that occur.
27. `callMarketDepthWSStream`: This function starts a stream of market depth data for a specific market from the blockchain and logs the received data or any errors that occur.
28. `callTradesWSStream`: This function starts a stream of trade data for the "SOL/USDC" market from the blockchain and logs the received data or any errors that occur.
29. `callGetNewRaydiumPoolsStream`: This function starts a stream of new pool data from the Raydium project on the blockchain and logs the received data or any errors that occur.
30. `callRecentBlockHashWSStream`: This function starts a stream of recent block hash data from the blockchain and logs the received data or any errors that occur.
31. `callPoolReservesWSStream`: This function starts a stream of pool reserve data for specific Raydium pools from the blockchain and logs the received data or any errors that occur.
32. `orderLifecycleTest`: This function tests the lifecycle of an order by placing an order, checking its status, cancelling it, and then checking its status again. It logs the results of each step or any errors that occur.
33. `callPlaceOrderWS`: This function places an order on the blockchain and logs the result or any errors that occur.
34. `callPlaceOrderBundle`: This function places an order on the blockchain using the Raydium Swap protocol. It specifies the owner address, the tokens to swap ("USDC" to "SOL"), the slippage, and the amount to swap. It then signs and submits the transaction, logging the signature or any errors that occur.
35. `callPlaceOrderBundleWithBatch`: This function is similar to `callPlaceOrderBundle`, but it uses a different slippage and submits the transaction as a batch.
36. `callCancelByClientOrderIDWS`: This function cancels an order on the blockchain using the client order ID. It logs the client order ID or any errors that occur.
37. `callPostSettleWS`: This function settles an order on the blockchain. It logs the signature of the transaction or any errors that occur.
38. `cancelAll`: This function places two orders on the blockchain, checks that they are in the order book, cancels them, and then checks that they are no longer in the order book. It logs the signatures of the transactions and any errors that occur.
39. `callReplaceByClientOrderID`: This function replaces an existing order on the blockchain using the client order ID. It first places an order, checks that it is in the order book, replaces it with a new order at half the original price, checks that the new order is in the order book, and then cancels all orders. It logs the signatures of the transactions and any errors that occur.
40. `callReplaceOrder`: This function is similar to `callReplaceByClientOrderID`, but it uses a different method to replace the order. Instead of using the client order ID, it uses the order ID. It first places an order, checks that it is in the order book, replaces it with a new order at half the original price using the order ID, checks that the new order is in the order book, and then cancels all orders. It logs the signatures of the transactions and any errors that occur.
41. `callTradeSwap`: This function submits a trade swap request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
42. `callTradeSwapWithPriorityFee`: Similar to `callTradeSwap`, but it also includes a compute limit and compute price in the request.
43. `callRaydiumSwap`: This function submits a Raydium swap request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
44. `callRouteTradeSwap`: This function submits a route trade swap request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
45. `callRaydiumRouteSwap`: This function submits a Raydium route swap request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
46. `callJupiterSwap`: This function submits a Jupiter swap request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
47. `callJupiterSwapInstructions`: This function submits a Jupiter swap instructions request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
48. `callRaydiumSwapInstructions`: This function submits a Raydium swap instructions request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
49. `callJupiterRouteSwap`: This function submits a Jupiter route swap request to the blockchain, logs the transaction signature, and returns a boolean indicating whether an error occurred.
50. `callPricesWSStream`: This function starts a stream of price data from the blockchain, logs each response received, and returns a boolean indicating whether an error occurred.
51. `callGetTickersWSStream`: This function starts a stream of ticker data from the blockchain, logs each response received, and returns a boolean indicating whether an error occurred.
52. `callSwapsWSStream`: This function starts a stream of swap data from the blockchain, logs each response received, and returns a boolean indicating whether an error occurred.
53. `callBlockWSStream`: This function starts a stream of block data from the blockchain, logs each response received, and returns a boolean indicating whether an error occurred.
54. `callGetPriorityFeeWSStream`: This function starts a stream of priority fee data from the blockchain, logs each response received, and returns a boolean indicating whether an error occurred.
55. `callGetPriorityFeeWS`: This function fetches the priority fee from the blockchain, logs the fee, and returns a boolean indicating whether an error occurred.
56. `callGetBundleTipWSStream`: This function starts a stream of bundle tip data from the blockchain, logs each response received, and returns a boolean indicating whether an error occurred.

\
