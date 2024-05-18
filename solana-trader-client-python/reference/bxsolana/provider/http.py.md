# http.py

The `http.py` file defines a `HttpProvider` class that is used to interact with an HTTP API. This class inherits from the `Provider` class and overrides several of its methods. It also defines several additional attributes and methods.&#x20;

Most methods use the `map_response` function to handle the HTTP response and return a response object. The specific type of the response object depends on the method.

The file also contains helper functions for serializing a list and projects, and functions for creating an HttpProvider with different endpoints.

1. `_endpoint`, `_endpoint_v2`, `_session`, `_private_key`: These are private attributes that store the HTTP API endpoints, an `aiohttp.ClientSession` object for making HTTP requests, and a private key for signing transactions, respectively.
2. `__init__`: This is the constructor of the class. It initializes the private attributes and sets up the HTTP session with necessary headers.
3. `connect` and `close`: These are asynchronous methods that do nothing and close the HTTP session, respectively.
4. `private_key`: This method returns the private key.
5. `get_rate_limit`, `get_transaction`, `get_bundle_result_v2`: These are asynchronous methods that send GET requests to the HTTP API and return the responses. They use the `map_response` function to handle the HTTP responses.
6. `get_raydium_pools`: This method sends a GET request to the `/raydium/pools` endpoint and returns the response.
7. `get_raydium_pool_reserve`: This method sends a GET request to the `/raydium/pool-reserves` endpoint with a list of pairs or addresses as query parameters and returns the response.
8. `get_raydium_quotes`: This method sends a GET request to the `/raydium/quotes` endpoint with several query parameters (in token, out token, in amount, slippage) and returns the response.
9. `get_jupiter_quotes`: This method is similar to `get_raydium_quotes`, but it sends the request to the `/jupiter/quotes` endpoint instead.
10. `get_raydium_prices`: This method sends a GET request to the `/raydium/prices` endpoint with a list of tokens as query parameters and returns the response.
11. `get_jupiter_prices`: This method is similar to `get_raydium_prices`, but it sends the request to the `/jupiter/prices` endpoint instead.
12. `post_jupiter_swap`: This method sends a POST request to the `/jupiter/swap` endpoint with a JSON payload and returns the response.
13. `post_raydium_swap`: This method sends a POST request to the `/raydium/swap` endpoint with a JSON payload and returns the response.
14. `post_jupiter_route_swap`: This method sends a POST request to the `/jupiter/route-swap` endpoint with a JSON payload and returns the response.
15. `post_raydium_route_swap`: This method sends a POST request to the `/raydium/route-swap` endpoint with a JSON payload and returns the response.
16. `get_markets_v2`: This method sends a GET request to the `/openbook/markets` endpoint and returns the response.
17. `get_orderbook_v2`: This method sends a GET request to the `/openbook/orderbooks/{market}` endpoint with a market and limit as query parameters and returns the response.
18. `get_market_depth_v2`: This method sends a GET request to the `/openbook/depth/{market}` endpoint with a market and limit as query parameters and returns the response.
19. `get_tickers_v2`: This method sends a GET request to the `/openbook/tickers/{market}` endpoint with a market as a path parameter and returns the response.
20. `get_open_orders_v2`: This method sends a GET request to the `/openbook/open-orders/{market}` endpoint with several query parameters (address, openOrdersAddress, orderID, clientOrderID) and returns the response.
21. `get_unsettled_v2`: This method sends a GET request to the `/openbook/unsettled/{market}` endpoint with an ownerAddress as a query parameter and returns the response.
22. `post_order_v2`: This method sends a POST request to the `/openbook/place` endpoint with a JSON payload and returns the response.
23. `post_cancel_order_v2`: This method sends a POST request to the `/openbook/cancel` endpoint with a JSON payload and returns the response.
24. `post_settle_v2`: This method sends a POST request to the `/openbook/settle` endpoint with a JSON payload and returns the response.
25. `post_replace_order_v2`: This method sends a POST request to the `/openbook/replace` endpoint with a JSON payload and returns the response.
26. `get_markets`: This method sends a GET request to the `/market/markets` endpoint and returns the response.
27. `get_quotes`: This method sends a GET request to the `/market/quote` endpoint with several query parameters (inToken, outToken, inAmount, slippage, limit, projects) and returns the response.
28. `post_route_trade_swap`: This method sends a POST request to the `/trade/route-swap` endpoint with a JSON payload and returns the response.
29. `get_orderbook`: This method sends a GET request to the `/market/orderbooks/{market}` endpoint with a market, limit, and project as query parameters and returns the response.
30. `get_market_depth`: This method sends a GET request to the `/market/depth/{market}` endpoint with a market, limit, and project as query parameters and returns the response.
31. `get_tickers`: This method sends a GET request to the `/market/tickers/{market}` endpoint with a market and project as query parameters and returns the response.
32. `get_orders`: This method is not implemented.
33. `get_open_orders`: This method sends a GET request to the `/trade/orders/{market}` endpoint with several query parameters (address, openOrdersAddress, types, project) and returns the response.
34. `get_order_by_id`: This method is not implemented.
35. `get_unsettled`: This method sends a GET request to the `/trade/unsettled/{market}` endpoint with an ownerAddress and project as query parameters and returns the response.
36. `get_account_balance`: This method sends a GET request to the `/balance` endpoint with an ownerAddress as a query parameter and returns the response.
37. `get_token_accounts`: This method sends a GET request to the `/account/token-accounts` endpoint with an ownerAddress as a query parameter and returns the response.
38. `get_pools`: This method sends a GET request to the `/market/pools` endpoint with a list of projects as query parameters and returns the response.
39. `get_price`: This method sends a GET request to the `/market/price` endpoint with a list of tokens as query parameters and returns the response.
40. `get_recent_block_hash`: This method sends a GET request to the `/system/blockhash` endpoint and returns the response.
41. `get_priority_fee`: This method sends a GET request to the `/system/priority-fee` endpoint with a project and optional percentile as query parameters and returns the response.
42. `post_trade_swap`: This method sends a POST request to the `/trade/swap` endpoint with a JSON payload and returns the response.
43. `post_order`: This method sends a POST request to the `/trade/place` endpoint with a JSON payload and returns the response.
44. `post_cancel_order`: This method sends a POST request to the `/trade/cancel` endpoint with a JSON payload and returns the response.
45. `post_cancel_by_client_order_id`: This method sends a POST request to the `/trade/cancelbyid` endpoint with a JSON payload and returns the response.
46. `post_cancel_all`: This method sends a POST request to the `/trade/cancelall` endpoint with a JSON payload and returns the response.
47. `post_settle`: This method sends a POST request to the `/trade/settle` endpoint with a JSON payload and returns the response.
48. `post_submit` and `post_submit_v2`: These methods send a POST request to the `/trade/submit` or `/submit` endpoint with a JSON payload and return the response. If the transaction is None, a ValueError is raised.
49. `post_submit_batch` and `post_submit_batch_v2`: These methods send a POST request to the `/trade/submit-batch` or `/submit-batch` endpoint with a JSON payload and return the response.
50. `post_replace_by_client_order_id`: This method sends a POST request to the `/trade/replacebyclientid` endpoint with a JSON payload and returns the response. If the payload contains a "clientOrderId", it is replaced with "clientOrderID".
51. `post_replace_order`: This method sends a POST request to the `/trade/replace` endpoint with a JSON payload and returns the response. If the payload contains an "orderId", it is replaced with "orderID".
52. `_unary_stream`: This method is not implemented and raises a NotImplementedError.





















