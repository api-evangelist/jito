# Jito Labs

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Jito Labs is the Solana MEV infrastructure company behind Jito-Solana, the MEV-enabled validator client that runs on the majority of Solana mainnet stake, and the Jito Block Engine, an off-chain auction service that accepts bundles and transactions from searchers and forwards them to the next leader. Together with the Jito Foundation it stewards JitoSOL — Solana's largest MEV-aware liquid staking token — the StakeNet validator scoring system, the Jito Restaking and Vault programs that power Node Consensus Networks, the merkle-based token distributor used for airdrops, and the JTO governance token. Developer surfaces include a JSON-RPC API for bundle and transaction submission, a public REST tip floor and WebSocket tip stream for pricing, the ShredStream gRPC service for sub-slot Solana shreds, and the open mev-protos repository that defines the canonical Auth, Block Engine, Bundle, Packet, Relayer, Searcher, Shared, and ShredStream gRPC interfaces — with official SDKs in TypeScript, Python, Rust, and Go.

**Areas:** Solana · MEV · Block Engine · Bundles · Liquid Staking · JitoSOL · Restaking · JTO · DAO · Validator · Searcher · ShredStream

## Jito Labs on APIs.io

Everything profiled for Jito Labs is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/jito/](https://apis.io/providers/jito/)** — or go straight to one of the APIs or properties below.

### APIs (10)

- [Jito Streaming Surfaces](https://apis.io/apis/jito/jito-streaming/) — Real-time streaming surfaces from Jito infrastructure — the wss tip_stream for continuous bundle-tip percentile updates, the ShredstreamProxy…
- [Jito Searcher gRPC Service](https://apis.io/apis/jito/jito-searcher-grpc/) — gRPC SearcherService exposing SubscribeBundleResults, SendBundle, GetNextScheduledLeader, GetConnectedLeaders, GetConnectedLeadersRegioned, GetTipAccounts,…
- [Jito Block Engine Validator gRPC](https://apis.io/apis/jito/jito-block-engine-validator-grpc/) — gRPC interface between Jito-Solana validators / relayers and the Block Engine — BlockEngineValidator with SubscribePackets, SubscribeBundles,…
- [Jito Relayer gRPC](https://apis.io/apis/jito/jito-relayer-grpc/) — Relayer gRPC service that sits in front of a Jito-Solana validator, exposing GetTpuConfigs and SubscribePackets so the validator can receive deduplicated…
- [JitoSOL Stake Pool](https://apis.io/apis/jito/jitosol-stake-pool/) — JitoSOL — Solana's MEV-aware liquid staking token, backed by an instance of the SPL Stake Pool program. Deposit SOL or an existing stake account to receive…
- [Jito Restaking And Vaults](https://apis.io/apis/jito/jito-restaking/) — Jito Restaking — the on-chain program suite (Restaking + Vault) that lets SPL tokens be restaked into Vaults whose security is rented to NCNs (Node…
- [Jito-Solana Validator Client](https://apis.io/apis/jito/jito-solana/) — Jito-Solana — the Jito Foundation MEV-enabled fork of the Solana validator client. Adds the Block Engine / Relayer integration that makes the bundle auction…
- [Jito Labs Bundles API](https://apis.io/apis/jito/jito-bundles-api/) — Submit and inspect atomic Solana transaction bundles.
- [Jito Labs Tips API](https://apis.io/apis/jito/jito-tips-api/) — Bundle tip pricing data.
- [Jito Labs Transactions API](https://apis.io/apis/jito/jito-transactions-api/) — Direct sendTransaction proxy to validator leaders.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Jito Streaming Surfaces](https://apis.io/asyncapis/jito/jito-streaming-asyncapi/)

#### Event channels (3)

Individual events and webhooks the provider emits.

- [/api/v1/bundles/tip_stream](https://apis.io/channels/jito/api-v1-bundles-tip-stream/)
- [SearcherService.SubscribeBundleResults](https://apis.io/channels/jito/searcherservice-subscribebundleresults/)
- [ShredstreamProxy.SubscribeEntries](https://apis.io/channels/jito/shredstreamproxy-subscribeentries/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Jito Agentic Access](https://apis.io/agentic-access/jito/jito-agentic-access/)

#### JSON Schema (5)

The data models the API reads and writes.

- [Jito Bundle](https://apis.io/schemas/jito/jito-bundle/)
- [Jito Bundle Status](https://apis.io/schemas/jito/jito-bundle-status/)
- [JitoSOL Stake Position](https://apis.io/schemas/jito/jito-jitosol-stake/)
- [Jito NCN (Node Consensus Network)](https://apis.io/schemas/jito/jito-ncn/)
- [Jito Bundle Tip Floor](https://apis.io/schemas/jito/jito-tip-floor/)

#### JSON Structure (2)

Data models expressed in JSON Structure.

- [Jito Bundle Status Structure](https://apis.io/json-structure/jito/jito-bundle-status-structure/)
- [Jito Bundle Structure](https://apis.io/json-structure/jito/jito-bundle-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Jito Context](https://apis.io/jsonld/jito/jito-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Jito Vocabulary](https://apis.io/vocabularies/jito/jito-vocabulary/)

#### Examples (4)

Example requests and responses.

- [Jito Getbundlestatuses Example](https://apis.io/examples/jito/jito-getBundleStatuses-example/)
- [Jito Gettipaccounts Example](https://apis.io/examples/jito/jito-getTipAccounts-example/)
- [Jito Sendbundle Example](https://apis.io/examples/jito/jito-sendBundle-example/)
- [Jito Sendbundle Response Example](https://apis.io/examples/jito/jito-sendBundle-response-example/)

#### Collections (5)

Postman and Open Collection request collections.

- [Jito Block Engine JSON-RPC API](https://apis.io/collections/jito/open-jito-block-engine/)
- [Jito Block Engine JSON-RPC Bundles API](https://apis.io/collections/jito/open-jito-bundles-api/)
- [Jito Bundles Tip Floor API](https://apis.io/collections/jito/open-jito-bundles-tip-floor/)
- [Jito Block Engine JSON-RPC Bundles Tips API](https://apis.io/collections/jito/open-jito-tips-api/)
- [Jito Block Engine JSON-RPC Bundles Transactions API](https://apis.io/collections/jito/open-jito-transactions-api/)

#### Governance rules (3)

Spectral rulesets for the provider's contracts.

- [Jito Labs — asyncapi rules](https://apis.io/rules/jito/jito-asyncapi-spectral-rules/)
- [Jito Labs — jsonschema rules](https://apis.io/rules/jito/jito-jsonschema-spectral-rules/)
- [Jito Labs API Rules](https://apis.io/rules/jito/jito-rules/)

#### Security (1)

Authentication, trust centre, and vulnerability disclosure.

- [Jito Domain Security](https://apis.io/security/jito/jito-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Jito Plans Pricing](https://apis.io/plans/jito/jito-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Jito Rate Limits](https://apis.io/rate-limits/jito/jito-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Jito Finops](https://apis.io/finops/jito/jito-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://jito.wtf)
- [Documentation](https://docs.jito.wtf)
- [Blog](https://www.jito.wtf/blog/)
- [GitHub](https://github.com/jito-labs)

## API Evangelist rating

**Kin Score 37.6** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 65.1 |
| Contract governance | 27.3 |
| Operational transparency | 5.3 |
| Developer ergonomics | 57.1 |
| Access clarity | 7.9 |

**Agent readiness 17.7** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | — |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 10.8** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/jito/](https://apis.io/providers/jito/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Jito Labs: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/jito/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
