# stream\_utils.py

The `stream_utils.py` file contains a function `do_stream` that streams various types of data from a trading platform. Each stream is started using the provided `api` object, which is an instance of the `Provider` class. The responses are converted to JSON and printed to the console.

Here's a brief overview of each stream:

1. `get_market_depths_stream`: Streams market depth updates for the "SOLUSDC" market.
2. `get_orderbooks_stream`: Streams order book updates for the "SOLUSDC" market.
3. `get_tickers_stream`: Streams ticker updates for various markets. This stream is only started if `run_slow` is `True`.
4. `get_trades_stream`: Streams trade updates for the "SOLUSDC" market. This stream is only started if `run_slow` is `True`.
5. `get_swaps_stream`: Streams swap events for the Raydium project. This stream is only started if `run_slow` is `True`.
6. `get_pool_reserves_stream`: Streams pool reserve updates for the Raydium project. This stream is only started if `run_slow` is `True`.
7. `get_prices_stream`: Streams price updates for the Raydium project. This stream is only started if `run_slow` is `True`.
8. `get_new_raydium_pools_stream`: Streams updates for new Raydium pools. This stream is only started if `run_slow` is `True`.
9. `get_priority_fee_stream`: Streams priority fee updates. This stream is only started if `run_slow` is `True`.

