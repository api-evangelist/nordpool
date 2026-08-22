# Nord Pool (nordpool)

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

Nord Pool, part of the Euronext group, operates Europe's leading power exchange, running day-ahead auctions and continuous intraday electricity markets across the Nordics, Baltics, Central Western Europe, and the UK. Its Market Data API delivers day-ahead prices, kWh-level electricity rates by bidding area, volumes, capacities, flows, and power system data, while WebSocket and REST trading APIs serve exchange members.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/nordpool/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/nordpool/refs/heads/main/apis.yml)

## Access Model (read this first)

Nord Pool's APIs are real and well-engineered, but access is layered:

- **Market Data API** (`data-api.nordpoolgroup.com`) — the docs and the full OpenAPI 3.0.4 definition are public (the copy in `openapi/nordpool-market-data-openapi.yml` is the provider's own definition, retrieved 2026-07-11), but getting data back requires a paid **Power Data Services** subscription and OAuth 2.0 credentials (`sts.nordpoolgroup.com`). Published day-ahead packages run about EUR 1,250–4,100/year per region; see `plans/`.
- **Trading APIs** (Intraday WebSocket/STOMP, Auction REST, Clearing, REMIT) — free of charge, but only for onboarded Nord Pool trading customers. Documentation and working Java/.NET examples are public on [GitHub](https://github.com/NordPool).
- **Public Data Portal API** (`dataportal-api.nordpoolgroup.com`) — the unauthenticated JSON backend of [data.nordpoolgroup.com](https://data.nordpoolgroup.com/) returns published day-ahead prices for free (verified live 2026-07-11; used by Home Assistant and others), but it is **unofficial**: no documentation, no SLA, and it may change at any time. The OpenAPI in `openapi/nordpool-data-portal-openapi.yml` is modeled from observed responses.

## Tags

- Day-Ahead Prices
- Electricity
- Energy Markets
- Power Exchange
- Intraday Trading
- Market Data
- Europe

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Nord Pool Day-Ahead Prices API

Day-ahead auction results from the Market Data API v2 - official day-ahead electricity prices per bidding area in 15-minute Market Time Unit resolution, price indices, buy and sell volumes, ATC capacities, flows, scheduled physical flows, flow-based constraints, and aggregated bidding curves, with history back to 1992. OAuth 2.0 secured; requires a paid Power Data Services subscription.

- **Human URL:** [https://www.nordpoolgroup.com/en/services/power-market-data-services/day-ahead-market-data/](https://www.nordpoolgroup.com/en/services/power-market-data-services/day-ahead-market-data/)
- **Base URL:** `https://data-api.nordpoolgroup.com`

#### Tags

- Day-Ahead Prices
- Electricity Prices
- Auctions
- Bidding Curves

#### Properties

- [Documentation](https://www.nordpoolgroup.com/en/services/power-market-data-services/day-ahead-market-data/)
- [API Reference](https://data-api.nordpoolgroup.com/index.html)
- [OpenAPI](openapi/nordpool-market-data-openapi.yml) — provider-published definition
- [Postman Collection](collections/nordpool.postman_collection.json)
- [Open Collection](collections/nordpool.opencollection.json)

### Nord Pool Intraday Market Data API

Intraday continuous market data from the Market Data API v2 - hourly and per-contract statistics, orders and order revisions, trades by contract, delivery start, or trade time, order books, and hub-to-hub capacities. OAuth 2.0 secured; requires a paid Power Data Services subscription.

- **Human URL:** [https://www.nordpoolgroup.com/en/services/power-market-data-services/intraday-market-data/](https://www.nordpoolgroup.com/en/services/power-market-data-services/intraday-market-data/)
- **Base URL:** `https://data-api.nordpoolgroup.com`

#### Tags

- Intraday
- Electricity
- Orders
- Trades

#### Properties

- [Documentation](https://www.nordpoolgroup.com/en/services/power-market-data-services/intraday-market-data/)
- [API Reference](https://data-api.nordpoolgroup.com/index.html)
- [OpenAPI](openapi/nordpool-market-data-openapi.yml) — provider-published definition
- [Postman Collection](collections/nordpool.postman_collection.json)
- [Open Collection](collections/nordpool.opencollection.json)

### Nord Pool Power System Data API

Operational power system data from the Market Data API v2 - production and consumption with forecasts by area and location, exchanges between areas, hydro reservoir reserves, balance market (mFRR) data, system price and turnover, daily exchange rates, and the Clean Horizon storage index. OAuth 2.0 secured; requires a paid Power Data Services subscription.

- **Human URL:** [https://www.nordpoolgroup.com/en/services/power-market-data-services/](https://www.nordpoolgroup.com/en/services/power-market-data-services/)
- **Base URL:** `https://data-api.nordpoolgroup.com`

#### Tags

- Power System
- Production
- Consumption
- Balancing

#### Properties

- [Documentation](https://www.nordpoolgroup.com/en/services/power-market-data-services/)
- [API Reference](https://data-api.nordpoolgroup.com/index.html)
- [OpenAPI](openapi/nordpool-market-data-openapi.yml) — provider-published definition
- [Postman Collection](collections/nordpool.postman_collection.json)
- [Open Collection](collections/nordpool.opencollection.json)

### Nord Pool Public Data Portal API

The free, unauthenticated JSON API behind Nord Pool's public Data Portal website, returning published day-ahead prices and price indices per delivery area in 15-minute resolution. Verified live on 2026-07-11, and widely used by open-source integrations such as Home Assistant, but it is not part of the officially documented developer offering and carries no SLA - endpoints in the referenced OpenAPI are modeled from observed responses.

- **Human URL:** [https://data.nordpoolgroup.com/](https://data.nordpoolgroup.com/)
- **Base URL:** `https://dataportal-api.nordpoolgroup.com`

#### Tags

- Day-Ahead Prices
- Free
- Electricity Prices
- Data Portal

#### Properties

- [Portal](https://data.nordpoolgroup.com/)
- [OpenAPI](openapi/nordpool-data-portal-openapi.yml) — modeled from observed responses

### Nord Pool Intraday Trading API

WebSocket API for continuous intraday power trading - clients speak STOMP over secure WebSocket (port 443) to parallel Market Data and Trading services for streaming contracts, order books, and capacities, and for order entry and private execution reports. A newer binary PMD v2 feed uses Protocol Buffers over WebSockets. Free to use but only for onboarded Nord Pool trading customers; channel names in the AsyncAPI are modeled from public GitHub examples.

- **Human URL:** [https://developers.nordpoolgroup.com/v1.0/docs/id-introduction](https://developers.nordpoolgroup.com/v1.0/docs/id-introduction)

#### Tags

- Intraday Trading
- WebSocket
- STOMP
- Order Entry

#### Properties

- [Documentation](https://developers.nordpoolgroup.com/v1.0/docs/id-introduction)
- [GitHub - public-intraday-api](https://github.com/NordPool/public-intraday-api)
- [GitHub - public-intraday-api-example](https://github.com/NordPool/public-intraday-api-example)
- [AsyncAPI](asyncapi/nordpool-intraday-asyncapi.yml) — modeled (transport confirmed, hosts/channels representative)

### Nord Pool Auction API

JSON REST API for day-ahead auction trading - integrated order submission and trade capture across the Nordic and Baltic auctions, CWE auctions, Poland, the GB Half Hourly Auction, and SEM-GB intraday auctions, with test systems available. Free to use but restricted to Nord Pool trading members; endpoints are not publicly documented, so no OpenAPI is modeled here.

- **Human URL:** [https://www.nordpoolgroup.com/en/trading/api/](https://www.nordpoolgroup.com/en/trading/api/)

#### Tags

- Day-Ahead Trading
- Auctions
- Order Entry
- Trade Capture

#### Properties

- [FAQ - Auction API](https://support.nordpoolgroup.com/support/solutions/articles/8000088508-faq-auction-api)
- [GitHub - AuctionApi-StarterKit](https://github.com/NordPool/AuctionApi-StarterKit)

## Common Properties

- [Website](https://www.nordpoolgroup.com/)
- [Developer Portal](https://developers.nordpoolgroup.com/)
- [LinkedIn](https://www.linkedin.com/company/nord-pool)
- [GitHub Organization](https://github.com/NordPool)
- [Trading API Overview](https://www.nordpoolgroup.com/en/trading/api/)
- [OAuth Scopes](scopes/nordpool-scopes.yml)
- [Plans](plans/nordpool-plans-pricing.yml)
- [Rate Limits](rate-limits/nordpool-rate-limits.yml)
- [FinOps](finops/nordpool-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
