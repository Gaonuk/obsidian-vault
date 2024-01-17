- https://github.com/delvtech
- https://github.com/yieldprotocol/vault-v2/tree/master
- https://docs.element.fi/element/element-smart-contracts
- https://docs.balancer.fi/concepts/vault/#separating-token-accounting-and-pool-logic
- https://github.com/balancer/balancer-v2-monorepo
- https://github.com/0xProject/protocol/tree/development
- https://github.com/Rari-Capital/vaults
- https://github.com/makerdao/dss
- https://docs.0xprotocol.org/en/latest/architecture/overview.html
- https://github.com/mudgen/awesome-diamonds
- https://github.com/dragonfly-xyz/useful-solidity-patterns/tree/main
- https://hackernoon.com/solidity-tutorial-understanding-design-patterns-part-1
- https://docs.makerdao.com/
- https://fravoll.github.io/solidity-patterns/
- https://github.com/ourzora/v3
- https://jacob.energy/hyperstructures.html
- https://github.com/aave/aave-v3-core/tree/master
- [Create2 Factory](https://t.co/VafvpVkT7j)
- [Create3](https://github.com/0xsequence/create3/tree/master)
- [All about EVM data locations](https://betterprogramming.pub/solidity-tutorial-all-about-data-locations-dabd33212471)
- [ourZora Contract overview](https://twitter.com/onnnnnnnion/status/1672231606436896768?s=20)
- https://www.rareskills.io/post/solidity-style-guide
- [Generate Docusaurus site with comments in Solidity](https://gist.github.com/PaulRBerg/32c195862d206b560f5eb620824b54a0)





```typescript
struct DecodedCallInstruction {
	address _allowanceTarget;
	address _buyToken;
	bytes _callData;
	uint256 _minBuyAmount;
	uint256 _sellAmount;
	address _sellToken;
	address payable _target;
}

function test_json() public {
	bytes memory testStruct = json.parseRaw(".callInstructions");
	DecodedCallInstruction[] memory decodedCalls = abi.decode(testStruct, (DecodedCallInstruction[]));
	
	ITradeIssuerV2.ContractCallInstruction[] memory instructions = new ITradeIssuerV2.ContractCallInstruction[](decodedCalls.length);
	
	for (uint256 i = 0; i < decodedCalls.length; ++i) {
		DecodedCallInstruction memory decodedCall = decodedCalls[i];
		instructions[i] = ITradeIssuerV2.ContractCallInstruction({
			_target: payable(decodedCall._target),
			_allowanceTarget: decodedCall._allowanceTarget,
			_sellToken: IERC20(decodedCall._sellToken),
			_sellAmount: decodedCall._sellAmount,
			_buyToken: IERC20(decodedCall._buyToken),
			_minBuyAmount: decodedCall._minBuyAmount,
			_callData: decodedCall._callData
		});
	}
}
```