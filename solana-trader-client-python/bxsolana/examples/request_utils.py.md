# request\_utils.py

The `request_utils.py` file contains a single asynchronous function `do_requests` that interacts with the trading API to fetch various types of data. Each request is sent using the provided `api` object, which is an instance of the `Provider` class. The responses are converted to JSON and printed to the console.

Here's a brief overview of each request:

1. `get_raydium_pool_reserve`: This request fetches the reserve of a Raydium pool for specific pairs or addresses.
2. `get_transaction`: This request fetches a specific transaction by its signature.
3. `get_rate_limit`: This request fetches the current rate limit for the API.
4. `get_market_depth_v2`: This request fetches the market depth for the "SOLUSDC" market.
5. `get_priority_fee`: This request fetches the priority fee for the Raydium project.
6. `get_markets_v2`: This request fetches all markets.
7. `get_orderbook_v2`: This request fetches the order book for the "SOLUSDC" market.
8. `get_tickers_v2`: This request fetches the ticker for the "SOLUSDC" market.
9. `get_tickers_v2`: Fetches all tickers.
10. `get_price`: Fetches the prices of the specified tokens.
11. `get_raydium_prices`: Fetches the prices of the specified tokens from the Raydium project.
12. `get_jupiter_prices`: Fetches the prices of the specified tokens from the Jupiter project.
13. `get_pools`: Fetches all pools from the Raydium project.
14. `get_raydium_pools`: Fetches all pools from the Raydium project.
15. `get_quotes`: Fetches quotes for a specified in-token, out-token, and amount from the Raydium project.
16. `get_raydium_quotes`: Fetches quotes for a specified in-token, out-token, and amount from the Raydium project.
17. `get_jupiter_quotes`: Fetches quotes from the Jupiter project for a specified in-token, out-token, and amount.
18. `get_open_orders_v2`: Fetches open orders for a specified account.
19. `get_unsettled_v2`: Fetches unsettled amounts for a specified market and owner address.
20. `get_account_balance`: Fetches the account balance for a specified owner address.
21. `get_token_accounts`: Fetches token accounts for a specified owner address.
22. `post_order_v2`: Posts an order to sell a specified amount of SOL for USDC at a specified price.
23. `post_cancel_order_v2`: Cancels an order by its order ID or client ID.
24. `post_settle_v2`: Settles an order for a specified owner address, market, base token wallet, quote token wallet, and open orders address.
25. `post_replace_order_v2`: Replaces an order by its order ID or client ID.
26. `post_trade_swap`: Posts a trade swap for a specified project, owner address, in-token, in-amount, out-token, and slippage.
27. `post_raydium_swap`: Posts a Raydium swap for a specified owner address, in-token, in-amount, out-token, and slippage.
28. `post_jupiter_swap`: Posts a Jupiter swap for a specified owner address, in-token, in-amount, out-token, and slippage.
29. `post_route_trade_swap`: Posts a route trade swap for a specified project, owner address, slippage, and steps.
30. `post_raydium_route_swap`: Posts a Raydium route swap for a specified owner address, slippage, and steps.





