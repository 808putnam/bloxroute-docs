# common.proto

The `common.proto` file is a Protocol Buffers (protobuf) file. It defines common data structures and enumerations (enums) that are used across the project. These structures are used in messages and services defined in other protobuf files. Here's a brief overview of the main components:

* `OrderType`: An enum representing the type of an order. It can be a market order, limit order, immediate or cancel order, or a post order.
* `PerpOrderType`: An enum representing the type of a perpetual order. It can be unknown, market, limit, trigger market, or trigger limit.
* `PerpPositionSide`: An enum representing the side of a perpetual position. It can be unknown, long, or short.
* `PostOnlyParams`: An enum representing parameters for post-only orders. It can be none, must post only, or try post only.
* `MarginContract`: An enum representing different types of margin contracts. It can be all spots, SOL spot, USDC spot, MSOL spot, WBTC spot, WETH spot, or USDT spot.
* `PerpContract`: An enum representing different types of perpetual contracts.
* `PerpCollateralType`: An enum representing different types of collateral actions in a perpetual contract. It can be deposit, withdrawal, or transfer.
* `PerpCollateralToken`: An enum representing different types of collateral tokens in a perpetual contract. It can be USDC or SOL.
* `Infinity`: An enum representing different states of infinity. It can be not infinite, positive infinity, or negative infinity.
* `PriceImpactPercent` and `PriceImpactPercentV2`: Messages representing the price impact percent. They contain a percent field and an infinity field.
* `Fee`: A message representing a fee. It contains an amount field, a mint field, and a percent field.
