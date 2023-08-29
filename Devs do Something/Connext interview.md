Interoperability Trilema [source](https://blog.connext.network/the-interoperability-trilemma-657c2cf69f17)
- Generalisability: ability to go to other chains very easily
- Trust minimization: Minimum amounts of actors you have to trust
- Extensibility: Ability to compose your bridge and technology (become a DeFi building block)

Optimistic bridges -> only one that solves trilema [source](https://blog.connext.network/optimistic-bridges-fb800dc7b0e0)
- Uses latency period to allow for one of the end watchers to prove fraud in the origin chain before messages are seen valid in the dest chain
- 1 -> N model, anybody can report fraud to take the right countermeasures

Lifecycle of a Connext tx (ETH -> OP):
1. User sends funds on ETH L1 with unauthenticated calldata (deposit liquidity on Uniswap on Optimism)
2. Connext routers (network of LPs) will submit bids to find who will submit tx on the dest chain
3. Sequencer receives the bids of the LPs
4. Router checks for fraud transactions
5. Router provide the liquidity on behalf of you on Uniswap
6. At the end of the fraud period, 

You can't have a fully functional cross-chain system using validity proofs or zk technology
	Problems around consensus, availability, it doesn't scale
	[source](https://blog.connext.network/validity-proofs-are-not-effective-for-bridging-blockchains-85b5e3b22a35)

Cross-chain arbitrage
	it's not possible, there are actors that can execute on both networks quicker than the bridge takes to move funds from one chain to another



