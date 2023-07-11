```solidity
// SPDX-License-Identifier: Apache License 2.0
pragma solidity ^0.8.17;

/// @title Provides functions for deriving a pool address from the factory, tokens, and the fee
library ComputePoolAddresses {
	bytes32 internal constant POOL_INIT_CODE_HASH = 0xe34f199b19b2b4f47f68442619d555527d244f78a3297ea89325f843f87b8b54;
	
	/// @notice Deterministically computes the pool address using Create2.
	/// @param factory The Uniswap V3 factory contract address
	/// @param token0 The token0 of the pool
	/// @param token1 The token1 of the pool
	/// @param fee The fee of the pool
	/// @return pool The contract address of the V3 pool
	function computeAddress(address factory, address token0, address token1, uint24 fee)
		internal
		pure
		returns (address pool)
	{
		require(token0 < token1);
		bytes32 _salt = keccak256(abi.encodePacked(token0, token1, fee));
		bytes32 hash = keccak256(abi.encodePacked(bytes1(0xff), address(factory), _salt, POOL_INIT_CODE_HASH));
		pool = address(uint160(uint256(hash)));
	}
}
```

```solidity
function getPositionRebalanceParams(uint256 tokenId)

external

pure

returns (RebalancePosition memory)

{

Position memory position = positions[tokenId];

ComputeLiquidityAmounts.calculatePositionHoldings(

IUniswapV3PoolState(position.pool), position

);

}
```

```
(address poolAddress,,,,,,,) = butler.positions(state.positionId);

(, int24 currentTick,,,,,) = butler.getPoolSlot0(poolAddress);

  

int24 newLowerTick;

int24 newUpperTick;

  

assembly {

let tickSpacing := 60

let tickRangeQuantity := 10

  

newLowerTick := sub(currentTick, mul(tickSpacing, tickRangeQuantity))

newUpperTick := add(currentTick, mul(tickSpacing, tickRangeQuantity))

}

  

(

uint256 currentAmount0,

uint256 currentAmount1,

uint256 neededAmount0,

uint256 neededAmount1

) = butler.getPositionCurrentAndNeededAmountsForTicks(

state.positionId, newLowerTick, newUpperTick

);
```