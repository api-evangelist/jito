# Jito Labs (jito)

Jito Labs is the Solana MEV infrastructure company behind Jito-Solana, the MEV-enabled validator client run by the majority of Solana mainnet stake, and the Jito Block Engine, an off-chain auction service that accepts bundles and transactions from searchers and forwards them to the next leader. Together with the Jito Foundation it stewards JitoSOL — Solana's largest MEV-aware liquid staking token — the StakeNet validator scoring system, the Jito Restaking and Vault programs that power Node Consensus Networks, the merkle-based token distributor used for airdrops, and the JTO governance token.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/jito/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=opensource-api-evangelist&utm_content=repo)

## Tags

Solana, MEV, Block Engine, Bundles, Liquid Staking, JitoSOL, Restaking, JTO, DAO, Validator, Searcher, ShredStream, Crypto, DeFi

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## Block Engine Regions

| Network | Region | URL |
|---|---|---|
| Mainnet | Global | `https://mainnet.block-engine.jito.wtf` |
| Mainnet | Amsterdam | `https://amsterdam.mainnet.block-engine.jito.wtf` |
| Mainnet | Dublin | `https://dublin.mainnet.block-engine.jito.wtf` |
| Mainnet | Frankfurt | `https://frankfurt.mainnet.block-engine.jito.wtf` |
| Mainnet | London | `https://london.mainnet.block-engine.jito.wtf` |
| Mainnet | New York | `https://ny.mainnet.block-engine.jito.wtf` |
| Mainnet | Salt Lake City | `https://slc.mainnet.block-engine.jito.wtf` |
| Mainnet | Singapore | `https://singapore.mainnet.block-engine.jito.wtf` |
| Mainnet | Tokyo | `https://tokyo.mainnet.block-engine.jito.wtf` |
| Testnet | Global | `https://testnet.block-engine.jito.wtf` |
| Testnet | Dallas | `https://dallas.testnet.block-engine.jito.wtf` |
| Testnet | New York | `https://ny.testnet.block-engine.jito.wtf` |

## APIs

### Jito Block Engine JSON-RPC API
JSON-RPC API for submitting atomic bundles of up to five Solana transactions via `sendBundle`, plus `getBundleStatuses`, `getInflightBundleStatuses`, `getTipAccounts`, `getRandomTipAccount`, and a `sendTransaction` proxy.

**Human URL:** [https://docs.jito.wtf/lowlatencytxnsend](https://docs.jito.wtf/lowlatencytxnsend)

- [Documentation](https://docs.jito.wtf/lowlatencytxnsend)
- [API Reference (json_rpc/http.md)](https://github.com/jito-labs/mev-protos/blob/master/json_rpc/http.md)
- [OpenAPI](openapi/jito-block-engine-openapi.yml)
- [JSON Schema — Bundle](json-schema/jito-bundle-schema.json)
- [JSON Schema — Bundle Status](json-schema/jito-bundle-status-schema.json)
- [JSON Structure — Bundle](json-structure/jito-bundle-structure.json)
- [JSON Structure — Bundle Status](json-structure/jito-bundle-status-structure.json)
- [Example — sendBundle](examples/jito-sendBundle-example.json)
- [Example — sendBundle response](examples/jito-sendBundle-response-example.json)
- [Example — getBundleStatuses](examples/jito-getBundleStatuses-example.json)
- [Example — getTipAccounts](examples/jito-getTipAccounts-example.json)
- [Naftiko Capability — Bundle Submission](capabilities/bundle-submission.yaml)
- [Naftiko Capability — Transaction Relay](capabilities/transaction-relay.yaml)
- [Naftiko Capability (shared) — Jito Bundle](capabilities/shared/jito-bundle.yaml)

### Jito Bundles Tip Floor API
Public REST endpoint exposing the recent tip floor — landed-tips percentiles (25th / 50th / 75th / 95th / 99th plus EMA50) — used by searchers to size the SOL tip on `sendBundle`.

**Human URL:** [https://bundles.jito.wtf/api/v1/bundles/tip_floor](https://bundles.jito.wtf/api/v1/bundles/tip_floor)

- [OpenAPI](openapi/jito-bundles-tip-floor-openapi.yml)
- [JSON Schema — Tip Floor](json-schema/jito-tip-floor-schema.json)
- [Example — Tip Floor](examples/jito-tip-floor-example.json)
- [Naftiko Capability — Tip Pricing](capabilities/tip-pricing.yaml)

### Jito Streaming Surfaces
Real-time feeds — the `wss://bundles.jito.wtf/api/v1/bundles/tip_stream` WebSocket for tip percentiles, `ShredstreamProxy.SubscribeEntries` for sub-slot shred delivery, and `SearcherService.SubscribeBundleResults` for bundle inclusion / rejection.

- [AsyncAPI](asyncapi/jito-streaming-asyncapi.yml)
- [Naftiko Capability — ShredStream](capabilities/shredstream.yaml)
- [ShredStream Proxy Client](https://github.com/jito-labs/shredstream-proxy)

### Jito Searcher gRPC Service
gRPC `SearcherService` exposing `SubscribeBundleResults`, `SendBundle`, `GetNextScheduledLeader`, `GetConnectedLeaders`, `GetConnectedLeadersRegioned`, `GetTipAccounts`, and `GetRegions`. Authenticated via the `AuthService` challenge + token-refresh flow.

- [searcher.proto](https://github.com/jito-labs/mev-protos/blob/master/searcher.proto)
- [auth.proto](https://github.com/jito-labs/mev-protos/blob/master/auth.proto)
- [Searcher Examples](https://github.com/jito-labs/searcher-examples)

### Jito Block Engine Validator gRPC
`BlockEngineValidator` (`SubscribePackets`, `SubscribeBundles`, `GetBlockBuilderFeeInfo`, `GetBlockEngineEndpoints`) and `BlockEngineRelayer` (`SubscribeAccountsOfInterest`, `SubscribeProgramsOfInterest`, `StartExpiringPacketStream`) for Jito-Solana validators and relayers.

- [block_engine.proto](https://github.com/jito-labs/mev-protos/blob/master/block_engine.proto)

### Jito Relayer gRPC
`Relayer` service exposing `GetTpuConfigs` and `SubscribePackets` for the TPU proxy used by Jito-Solana validators.

- [relayer.proto](https://github.com/jito-labs/mev-protos/blob/master/relayer.proto)
- [jito-relayer repository](https://github.com/jito-foundation/jito-relayer)

### JitoSOL Stake Pool
MEV-aware liquid staking token backed by the SPL Stake Pool program. SOL deposits mint JitoSOL whose exchange rate accrues both staking rewards and the validator set's share of MEV captured by the Block Engine. StakeNet drives validator selection.

- [Stakers Portal](https://www.jito.network/stakers/)
- [stake-pool repository](https://github.com/jito-foundation/stake-pool)
- [spl-stake-pool-js](https://github.com/jito-foundation/spl-stake-pool-js)
- [stakenet repository](https://github.com/jito-foundation/stakenet)
- [JSON Schema — Stake Position](json-schema/jito-jitosol-stake-schema.json)
- [Naftiko Capability — JitoSOL Staking](capabilities/jitosol-staking.yaml)

### Jito Restaking And Vaults
On-chain Restaking + Vault programs enabling SPL tokens to be restaked into NCN-secured workloads. Includes the Tip Router NCN, the Rewards NCN that distributes payment to other NCNs, a BLS NCN reference implementation, and an NCN template.

- [restaking](https://github.com/jito-foundation/restaking)
- [jito-tip-router](https://github.com/jito-foundation/jito-tip-router)
- [jito-rewards-ncn](https://github.com/jito-foundation/jito-rewards-ncn)
- [ncn-template](https://github.com/jito-foundation/ncn-template)
- [jito-bls-ncn](https://github.com/jito-foundation/jito-bls-ncn)
- [JSON Schema — NCN](json-schema/jito-ncn-schema.json)
- [Naftiko Capability — Restaking](capabilities/restaking.yaml)

### Jito Foundation Governance
JTO token-holder governance via Jito Realms, plus the merkle-based token distributor used for airdrops and reward distribution.

- [Governance Portal](https://gov.jito.network)
- [governance-ui](https://github.com/jito-foundation/governance-ui)
- [distributor](https://github.com/jito-foundation/distributor)

### Jito-Solana Validator Client
Jito Foundation's MEV-enabled fork of the Solana validator client. The substrate that exposes the auction interface to the Block Engine at the validator layer.

- [jito-solana](https://github.com/jito-foundation/jito-solana)
- [jito-programs](https://github.com/jito-foundation/jito-programs)
- [jito-bell (notifications)](https://github.com/jito-foundation/jito-bell)
- [geyser-grpc-plugin](https://github.com/jito-labs/geyser-grpc-plugin)
- [solana-accountsdb-connector](https://github.com/jito-foundation/solana-accountsdb-connector)

## SDKs

| Language | Repository |
|---|---|
| TypeScript (SDK) | [jito-labs/jito-ts](https://github.com/jito-labs/jito-ts) |
| TypeScript (JSON-RPC) | [jito-labs/jito-js-rpc](https://github.com/jito-labs/jito-js-rpc) |
| Python (SDK) | [jito-labs/jito-python](https://github.com/jito-labs/jito-python) |
| Python (JSON-RPC) | [jito-labs/jito-py-rpc](https://github.com/jito-labs/jito-py-rpc) |
| Rust (SDK) | [jito-labs/jito-rs](https://github.com/jito-labs/jito-rs) |
| Rust (JSON-RPC) | [jito-labs/jito-rust-rpc](https://github.com/jito-labs/jito-rust-rpc) |
| Go (JSON-RPC) | [jito-labs/jito-go-rpc](https://github.com/jito-labs/jito-go-rpc) |

## Cross-Cutting Artifacts

- [Spectral Rules](rules/jito-rules.yml)
- [Vocabulary](vocabulary/jito-vocabulary.yml)
- [JSON-LD Context](json-ld/jito-context.jsonld)
- [Plans And Pricing](plans/jito-plans-pricing.yml)
- [Rate Limits](rate-limits/jito-rate-limits.yml)
- [FinOps](finops/jito-finops.yml)

## Common Resources

- [Jito Labs](https://www.jito.network)
- [Jito Documentation](https://docs.jito.wtf)
- [Jito Labs GitBook (MEV)](https://jito-labs.gitbook.io/mev/)
- [Jito Foundation GitBook (MEV)](https://jito-foundation.gitbook.io/mev/)
- [Jito Explorer](https://explorer.jito.wtf/)
- [Jito Labs GitHub](https://github.com/jito-labs)
- [Jito Foundation GitHub](https://github.com/jito-foundation)
- [mev-protos (canonical .proto files)](https://github.com/jito-labs/mev-protos)
- [Discord](https://discord.gg/jito)
- [Jito on X](https://twitter.com/jito_sol)
- [Jito Labs on X](https://twitter.com/jito_labs)
