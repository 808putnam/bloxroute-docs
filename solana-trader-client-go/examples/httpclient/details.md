# Details

## callPlaceOrderBundle

1. We setup a protobuf struct for a Raydium swap of 0.01 SOL for USDC.&#x20;
2. We then construct a post of the protobuf struct.&#x20;
3. We then sign and submit and get the transaction signature.

## callPlaceOrderBundleUsingBatch

1. We setup a protobuf struct for a Raydium swap of 0.01 SOL for USDC.&#x20;
2. We then remotely post the swap and get the transaction constructed.&#x20;
3. We then sign the transaction locally.
4. We then create a protobu batch entry for the transaction and a protobuf batch request to contain it.
5. We then remotely post the batch request.
6. TODO: Does this actually submit?

## callPostSettleHTTP

1. Sleep for 60 seconds.
2. Call SubmitSettleV2
3. Reference
   1. [https://docs.bloxroute.com/solana/trader-api-v2/api-endpoints/openbook/create-settle-transaction](https://docs.bloxroute.com/solana/trader-api-v2/api-endpoints/openbook/create-settle-transaction)
   2. Appears to be setting up OpenBook state for subsequent transactions. Does not submit to Solana

## cancelAll

Sets up a Limit Ask (sell) for SOL/USDC

How much SOL is needed to buy a single USDC.

order price: 170,200 lamports

order amount: 0.1

These limit orders are placed in orderbook.

We then sleep for 1 minute.

We then check if limit orders are there

We then cancel all orders

References

[https://www.investopedia.com/terms/b/basecurrency.asp](https://www.investopedia.com/terms/b/basecurrency.asp)

## callReplaceByClientOrderId

We start by placing an ordeer in openbook

We then get the order

We then replace the order

We then get the replaced order

We then cancel the order

## callReplaceOrder

We place an order in orderbook

We get the order

We submit replace order

We get the replaced order

We cancel the replaced order

## callGetRecentBlockHash

We the the recent blockhash











