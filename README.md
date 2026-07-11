# Nord Pool (nordpool)

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
