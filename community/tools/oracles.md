# Oracles

Checkout the oracles that our community is using or has built! 

> Please open a pull request if you'd like a project to be added to this list (guidance: succinct overview of the project / solution highlighting main features, include OP Mainnet / Testnet link or relevant documentation -- character count limit: 500). 

## Supra

[Supra](https://supra.com/) is a novel, high-throughput Oracle & IntraLayer: A vertically integrated toolkit of cross-chain solutions (data oracles, asset bridges, automation network, and more) that interlink all blockchains, public (L1s and L2s) or private (enterprises).

Supra provides decentralized oracle price feeds that can be used for on-chain and off-chain use-cases such as spot and perpetual DEXes, lending protocols, and payments protocols. Supra's oracle chain and consensus algorithm make it the fastest-to-finality oracle provider, with layer-1 security guarantees. The pull oracle has a sub-second response time. Aside from speed and security, Supra's rotating node architecture gathers data from 40+ data sources and applies a robust calculation methodology to get the most accurate value. The node provenance on the data dashboard also provides a fully transparent historical audit trail. Supra's Distributed Oracle Agreement (DORA) paper was accepted into ICDCS 2023, oldest distributed systems conference.

Check out our developer docs [here](https://docs.supra.com/oracles/overview).

## Tellor

[Tellor](https://tellor.io/) is a permissionless, censorship-resistant, and customizable oracle.

The Tellor protocol can secure putting any verifiable data onchain, from spot price feeds, TWAPs, random numbers, to EVM calldata - you can even [specify your own "query type"](https://github.com/tellor-io/dataSpecs/issues/new?assignees=\&labels=\&template=new_query_type.yaml\&title=%5BNew+Data+Request+Form%5D%3A+) to build a feed to fit your specific needs.

As described in the oracles overview section of this page, we are an oracle protocol that has "a mechanism to reward entities that provide accurate information and penalize those that provide incorrect information." Therefore it is necessary to allow some reasonable [amount of time](https://docs.tellor.io/tellor/getting-data/solidity-integration#reading-data) between an oracle update and using that data, to allow for a potential dispute (probabilistic finality).

Tellor is a pull oracle where users fund (tip) a specific feed to get updated data reports and then read the data from our oracle contract, however under certain circumstances it can act similar to a push oracle; if you are reading from a feed that is already being updated by others, or if you are [running your own data reporter.](https://docs.tellor.io/tellor/reporting-data/introduction)

To learn more about using tellor please [read our docs](https://docs.tellor.io) or [get in touch](https://github.com/ethereum-optimism/developers/discussions).

[Tellor contract addresses on OP Mainnet and the testnets can be found here.](https://docs.tellor.io/tellor/the-basics/contracts-reference#optimism)

## Band

[Band](https://bandprotocol.com/vrf) provides a source of [onchain randomness](https://bandprotocol.com/vrf).
[You can learn how to use it here](https://docs.bandchain.org/products/vrf/getting-started).
It is a single-transaction pull oracle.

## Universal Market Access (UMA)

[UMA](https://umaproject.org/) is a generic oracle.
It lets any contract request information (ask a question), and any staked entity can provide an answer.
Other external entities can dispute the proposed answer by providing their own answer and putting up their own stake.
In the case of dispute the question goes to a vote of token holders.
The token holders that vote with the majority are assumed to be truthful and get rewarded.
The external entities that proposed the correct answer are rewarded.
Those that proposed the wrong answer lose their stake.

[See here for the UMA addresses on OP Mainnet](https://github.com/UMAprotocol/protocol/blob/master/packages/core/networks/10.json).

[See here for instructions on how to use UMA](https://docs.umaproject.org/build-walkthrough/build-process).

UMA is a pull Oracle, it does not get information until it is requested by a contract.
This means that a decentralized application needs to issue two transactions.
First, a transaction that causes a contract on the blockchain to ask for the information.
Later (in the case of UMA 48 hours later if there is no dispute, longer if there is), a second transaction needs to be triggered to cause the contract to read from the Oracle and see the response to the request.

## Uniswap

Technically speaking [Uniswap](https://uniswap.io/) is not an oracle, because the information comes from onchain sources.
However, Uniswap pools do provide [quotes that give the relative price of tokens](https://docs.uniswap.org/concepts/protocol/oracle).

<Callout type="warning">
  Using onchain token prices, especially those in low liquidity pools, makes you vulnerable to price manipulation.
</Callout>

To use Uniswap as an Oracle:

1.  See [the list of pools on OP Mainnet](https://info.uniswap.org/#/optimism/).

2.  To find the pool address, [look at the Uniswap factory](https://explorer.optimism.io/address/0x1f98431c8ad98523631ae4a59f267346ea31f984#readContract).
    Use **getPool** with these parameters:

    | Parameter           | Meaning                                                                                                                        |    |
    | ------------------- | ------------------------------------------------------------------------------------------------------------------------------ | -- |
    | One token address   | [Address of the ERC-20 contract for that token on OP Mainnet (chainId 10)](https://static.optimism.io/optimism.tokenlist.json) |    |
    | Other token address | [Address of the ERC-20 contract for that token on OP Mainnet (chainId 10)](https://static.optimism.io/optimism.tokenlist.json) | \\ |
    | Pool fee            | The pool fee percentage times ten thousand. For example, for 0.3% enter `3000`                                                 |    |

3.  In your contract, use [IUniswapV3PoolState](https://github.com/Uniswap/v3-core/blob/main/contracts/interfaces/pool/IUniswapV3PoolState.sol) and [IUniswapV3PoolDerivedState](https://github.com/Uniswap/v3-core/blob/main/contracts/interfaces/pool/IUniswapV3PoolDerivedState.sol) to get the pool state.

