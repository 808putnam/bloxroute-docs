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

