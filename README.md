# Jito Labs (jito)

Jito Labs is the Solana MEV infrastructure company behind Jito-Solana, the MEV-enabled validator client that runs on the majority of Solana mainnet stake, and the Jito Block Engine, an off-chain auction service that accepts bundles and transactions from searchers and forwards them to the next leader. Together with the Jito Foundation it stewards JitoSOL — Solana's largest MEV-aware liquid staking token — the StakeNet validator scoring system, the Jito Restaking and Vault programs that power Node Consensus Networks, the merkle-based token distributor used for airdrops, and the JTO governance token. Developer surfaces include a JSON-RPC API for bundle and transaction submission, a public REST tip floor and WebSocket tip stream for pricing, the ShredStream gRPC service for sub-slot Solana shreds, and the open mev-protos repository that defines the canonical Auth, Block Engine, Bundle, Packet, Relayer, Searcher, Shared, and ShredStream gRPC interfaces — with official SDKs in TypeScript, Python, Rust, and Go.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/jito/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/jito/refs/heads/main/apis.yml)

## Scope

- **Position:** Producing
- **Access:** 3rd-Party

## Tags

- Solana
- MEV
- Block Engine
- Bundles
- Liquid Staking
- JitoSOL
- Restaking
- JTO
- DAO
- Validator
- Searcher
- ShredStream
- Crypto
- DeFi

## Timestamps

- **Created:** 2026-05-24T00:00:00.000Z
- **Modified:** 2026-05-24

## APIs

### Jito Block Engine JSON-RPC API

JSON-RPC API for submitting atomic bundles of up to five Solana transactions to the Jito Block Engine via sendBundle, plus getBundleStatuses, getInflightBundleStatuses, getTipAccounts, getRandomTipAccount, and a sendTransaction proxy. Endpoints are exposed from regional Block Engine clusters in Amsterdam, Dublin, Frankfurt, London, New York, Salt Lake City, Singapore, Tokyo, and global mainnet and testnet front-doors.

- **Human URL:** [https://docs.jito.wtf/lowlatencytxnsend](https://docs.jito.wtf/lowlatencytxnsend)
- **Base URL:** `https://mainnet.block-engine.jito.wtf/api/v1/bundles`

#### Tags

- Solana
- MEV
- Bundles
- Block Engine

#### Properties

- [Documentation](https://docs.jito.wtf/lowlatencytxnsend)
- [API Reference](https://github.com/jito-labs/mev-protos/blob/master/json_rpc/http.md)
- [OpenAPI](openapi/jito-block-engine-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/jito-bundle-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/jito-bundle-status-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/jito-bundle-structure.json)
- [JSON Structure](json-structure/jito-bundle-status-structure.json)
- [Example](examples/jito-sendBundle-example.json)
- [Example](examples/jito-sendBundle-response-example.json)
- [Example](examples/jito-getBundleStatuses-example.json)
- [Example](examples/jito-getTipAccounts-example.json)

### Jito Bundles Tip Floor API

Public REST endpoint exposing the recent tip floor — landed-tips percentiles (25th/50th/75th/95th/99th plus EMA50) — used by searchers to size the SOL tip on sendBundle. Pairs with the tip_stream WebSocket for continuous updates.

- **Human URL:** [https://bundles.jito.wtf/api/v1/bundles/tip_floor](https://bundles.jito.wtf/api/v1/bundles/tip_floor)
- **Base URL:** `https://bundles.jito.wtf`

#### Tags

- Solana
- MEV
- Tips
- Pricing

#### Properties

- [Documentation](https://docs.jito.wtf/lowlatencytxnsend)
- [OpenAPI](openapi/jito-bundles-tip-floor-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/jito-tip-floor-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Example](examples/jito-tip-floor-example.json)

### Jito Streaming Surfaces

Real-time streaming surfaces from Jito infrastructure — the wss tip_stream for continuous bundle-tip percentile updates, the ShredstreamProxy SubscribeEntries gRPC method for sub-slot Solana shred delivery, and the SearcherService SubscribeBundleResults gRPC stream of bundle inclusion and rejection events.

- **Human URL:** [https://github.com/jito-labs/shredstream-proxy](https://github.com/jito-labs/shredstream-proxy)

#### Tags

- Solana
- MEV
- Streaming
- ShredStream
- WebSocket
- gRPC

#### Properties

- [Documentation](https://github.com/jito-labs/shredstream-proxy)
- [API Reference](https://github.com/jito-labs/mev-protos/blob/master/shredstream.proto)
- [AsyncAPI](asyncapi/jito-streaming-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Jito Searcher gRPC Service

gRPC SearcherService exposing SubscribeBundleResults, SendBundle, GetNextScheduledLeader, GetConnectedLeaders, GetConnectedLeadersRegioned, GetTipAccounts, and GetRegions. Authenticated via the AuthService challenge + token-refresh flow. The native interface used by Jito's official Rust, TypeScript, Python, and Go searcher clients.

- **Human URL:** [https://github.com/jito-labs/mev-protos/blob/master/searcher.proto](https://github.com/jito-labs/mev-protos/blob/master/searcher.proto)

#### Tags

- Solana
- MEV
- gRPC
- Searcher

#### Properties

- [API Reference](https://github.com/jito-labs/mev-protos/blob/master/searcher.proto)
- [API Reference](https://github.com/jito-labs/mev-protos/blob/master/auth.proto)
- [Code Examples](https://github.com/jito-labs/searcher-examples)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Jito Block Engine Validator gRPC

gRPC interface between Jito-Solana validators / relayers and the Block Engine — BlockEngineValidator with SubscribePackets, SubscribeBundles, GetBlockBuilderFeeInfo, GetBlockEngineEndpoints, and BlockEngineRelayer with SubscribeAccountsOfInterest, SubscribeProgramsOfInterest, and StartExpiringPacketStream.

- **Human URL:** [https://github.com/jito-labs/mev-protos/blob/master/block_engine.proto](https://github.com/jito-labs/mev-protos/blob/master/block_engine.proto)

#### Tags

- Solana
- MEV
- gRPC
- Validator

#### Properties

- [API Reference](https://github.com/jito-labs/mev-protos/blob/master/block_engine.proto)
- [Repository](https://github.com/jito-foundation/jito-solana)
- [Repository](https://github.com/jito-foundation/jito-relayer)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Jito Relayer gRPC

Relayer gRPC service that sits in front of a Jito-Solana validator, exposing GetTpuConfigs and SubscribePackets so the validator can receive deduplicated packets from the Block Engine and the public TPU.

- **Human URL:** [https://github.com/jito-foundation/jito-relayer](https://github.com/jito-foundation/jito-relayer)

#### Tags

- Solana
- Relayer
- gRPC
- Validator

#### Properties

- [Repository](https://github.com/jito-foundation/jito-relayer)
- [API Reference](https://github.com/jito-labs/mev-protos/blob/master/relayer.proto)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### JitoSOL Stake Pool

JitoSOL — Solana's MEV-aware liquid staking token, backed by an instance of the SPL Stake Pool program. Deposit SOL or an existing stake account to receive JitoSOL whose exchange rate accrues both staking rewards and the validator set's share of MEV captured by the Block Engine. StakeNet drives validator selection on chain.

- **Human URL:** [https://www.jito.network/stakers/](https://www.jito.network/stakers/)

#### Tags

- Solana
- Liquid Staking
- JitoSOL
- MEV

#### Properties

- [Documentation](https://www.jito.network/stakers/)
- [Repository](https://github.com/jito-foundation/stake-pool)
- [SDK](https://github.com/jito-foundation/spl-stake-pool-js)
- [Repository](https://github.com/jito-foundation/stakenet)
- [JSON Schema](json-schema/jito-jitosol-stake-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Jito Restaking And Vaults

Jito Restaking — the on-chain program suite (Restaking + Vault) that lets SPL tokens be restaked into Vaults whose security is rented to NCNs (Node Consensus Networks). Includes the tip router, the rewards NCN that distributes payment to other NCNs, an NCN template, and a BLS NCN reference implementation.

- **Human URL:** [https://github.com/jito-foundation/restaking](https://github.com/jito-foundation/restaking)

#### Tags

- Solana
- Restaking
- Vaults
- NCN

#### Properties

- [Repository](https://github.com/jito-foundation/restaking)
- [Repository](https://github.com/jito-foundation/jito-tip-router)
- [Repository](https://github.com/jito-foundation/jito-rewards-ncn)
- [Repository](https://github.com/jito-foundation/ncn-template)
- [Repository](https://github.com/jito-foundation/jito-bls-ncn)
- [JSON Schema](json-schema/jito-ncn-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Jito Foundation Governance

Jito DAO governance — JTO token holders direct treasury, fee parameters, and the JitoSOL validator selection policy through Realms. Includes the Jito Realms governance UI fork and the merkle-based token distributor used for airdrops and reward distribution.

- **Human URL:** [https://gov.jito.network](https://gov.jito.network)

#### Tags

- Solana
- Governance
- JTO
- DAO

#### Properties

- [Portal](https://gov.jito.network)
- [Repository](https://github.com/jito-foundation/governance-ui)
- [Repository](https://github.com/jito-foundation/distributor)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Jito-Solana Validator Client

Jito-Solana — the Jito Foundation MEV-enabled fork of the Solana validator client. Adds the Block Engine / Relayer integration that makes the bundle auction possible at the validator layer. Ships alongside the Jito programs, the Geyser gRPC plugin for account streaming, the Jito Bell notification system, and an accountsdb connector.

- **Human URL:** [https://github.com/jito-foundation/jito-solana](https://github.com/jito-foundation/jito-solana)

#### Tags

- Solana
- Validator
- MEV
- Rust

#### Properties

- [Repository](https://github.com/jito-foundation/jito-solana)
- [Repository](https://github.com/jito-foundation/jito-programs)
- [Repository](https://github.com/jito-foundation/jito-bell)
- [Repository](https://github.com/jito-labs/geyser-grpc-plugin)
- [Repository](https://github.com/jito-foundation/solana-accountsdb-connector)
- [Postman Collection](collections/jito-block-engine.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-block-engine.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/jito-bundles-tip-floor.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/jito-bundles-tip-floor.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.jito.network)
- [Portal](https://www.jito.network/stakers/)
- [Documentation](https://docs.jito.wtf)
- [Documentation](https://docs.jito.wtf/lowlatencytxnsend)
- [Repository](https://github.com/jito-labs/jito-docs)
- [Documentation](https://jito-labs.gitbook.io/mev/)
- [Documentation](https://jito-foundation.gitbook.io/mev/)
- [Console](https://explorer.jito.wtf/)
- [GitHub Organization](https://github.com/jito-labs)
- [GitHub Organization](https://github.com/jito-foundation)
- [Repository](https://github.com/jito-labs/mev-protos)
- [SDK](https://github.com/jito-labs/jito-ts)
- [SDK](https://github.com/jito-labs/jito-rs)
- [SDK](https://github.com/jito-labs/jito-python)
- [SDK](https://github.com/jito-labs/jito-js-rpc)
- [SDK](https://github.com/jito-labs/jito-py-rpc)
- [SDK](https://github.com/jito-labs/jito-rust-rpc)
- [SDK](https://github.com/jito-labs/jito-go-rpc)
- [Code Examples](https://github.com/jito-labs/searcher-examples)
- [Code Examples](https://github.com/jito-labs/mev-bot)
- [Tool](https://github.com/jito-labs/shredstream-proxy)
- [Tool](https://github.com/jito-labs/block_engine_simple)
- [Repository](https://github.com/jito-foundation/jito-solana)
- [Repository](https://github.com/jito-foundation/jito-relayer)
- [Repository](https://github.com/jito-foundation/restaking)
- [Repository](https://github.com/jito-foundation/stakenet)
- [Repository](https://github.com/jito-foundation/jito-programs)
- [Documentation](https://github.com/jito-foundation/jito-omnidocs)
- [Twitter](https://twitter.com/jito_sol)
- [Twitter](https://twitter.com/jito_labs)
- [Forum](https://discord.gg/jito)
- [Spectral Rules](rules/jito-rules.yml)
- [Vocabulary](vocabulary/jito-vocabulary.yml)
- [JSON-LD](json-ld/jito-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Plans](plans/jito-plans-pricing.yml)
- [Rate Limits](rate-limits/jito-rate-limits.yml)
- [Fin Ops](finops/jito-finops.yml)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)
- [Solutions](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
