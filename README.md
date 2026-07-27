# E.ON Next (eon-next)

E.ON Next Energy Limited is the United Kingdom retail supply arm of the E.ON Group, formed after E.ON's 2019 acquisition of npower and serving roughly five million British households and small businesses with electricity, gas, smart meters, solar, home batteries, heat pumps and EV charging tariffs. It sits at the retail end of the GB energy value chain — buying wholesale, settling through Elexon, reading SMETS2 smart meters over the licensed Smart DCC network, and billing the customer — and it runs its entire operation on Kraken, the API-first, GraphQL-based energy operating system licensed from Kraken Technologies (Octopus Energy Group), onto which 5.8 million customers were migrated between June 2020 and June 2022. Its API posture is the exact opposite of its platform's reputation: the Kraken architecture underneath is API-first, but nothing is published outward. There is no developer portal, no API documentation, no OpenAPI, and no third-party route to a customer's usage or billing data; developer.eonnext.com and docs.eonnext.com do not resolve, and api.eonnext.com answers every path with an unauthenticated AWS API Gateway 403 "Missing Authentication Token". Britain mandated the metering infrastructure, not the data right — E.ON Next is bound by the Smart Energy Code and the DCC, which is live and implemented, but no consumer data-portability mandate equivalent to Australia's CDR or Ontario's Green Button applies to it, and none of the open GB market data (NESO Carbon Intensity, Elexon BSC, DNO open-data portals) originates here. Consumer data is closed, market data is published by other parties, and this profile is identity-only by evidence.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/eon-next/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/eon-next/refs/heads/main/apis.yml)

## Tags

- Energy
- United Kingdom
- Utilities
- Electricity
- Gas
- Smart Metering
- Energy Retail
- Kraken
- Solar
- EV Charging

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

_No public APIs are documented by E.ON Next._

The full probe is recorded in [review.yml](review.yml). Every candidate developer host and path was checked anonymously on 2026-07-27: `developer.eonnext.com`, `developers.eonnext.com` and `docs.eonnext.com` do not resolve; `api.eonnext.com` and `data.eonnext.com` return the AWS API Gateway `{"message":"Missing Authentication Token"}` 403 on every path including `/v1/graphql/`, `/openapi.json`, `/swagger.json` and `/.well-known/openid-configuration`; and `/developers`, `/api`, `/docs`, `/data`, `/open-data` and `/api-docs` on `www.eonnext.com` all return 404. The company's own sitemap index enumerates 364 URLs, none of which contain a developer, API, docs, or open-data path segment.

## Regulatory Posture

- **Mandate regime:** `smart-meter-infrastructure` — the GB Smart Metering Implementation Programme, the Smart Energy Code, and the licensed Smart DCC monopoly.
- **Mandate status:** `live-implemented`, **for the infrastructure obligation only**. Smart meters are installed and communicating over the DCC, and SEC accession is mandatory for every GB supplier. That mandate produces no supplier-published endpoint — the API in this regime belongs to the DCC, not to E.ON Next.
- **Consumer data right:** none. There is no UK equivalent of Australia's CDR (energy) or Ontario's Green Button regulation. DESNZ's energy smart data scheme call for evidence closed 10 March 2025 with no published government response, and smart data schemes under the Data (Use and Access) Act 2025 require sector-specific secondary legislation that has not been made for energy.
- **Data standard:** SMETS2 / Smart Energy Code infrastructure only. No Green Button/ESPI, CDR Consumer Data Standards, OCPP/OCPI, OpenADR, IEEE 2030.5, or IEC CIM reference found.
- **Consumer data vs market data:** closed on both. No consumer usage/billing API, and no open grid or market data — in Britain that is published by NESO, Elexon, and the DNOs, not by a retailer.
- **Access gate:** `none-published`. A developer wanting GB smart-meter data programmatically must become a Smart Energy Code party in the DCC "Other User" role, or use a consent intermediary that already holds that status. The route bypasses the supplier by design.
- **Auth model:** none published. No OIDC discovery document is served anonymously; the only authentication is a customer web/mobile account login.

## Platform Note

E.ON Next runs on Kraken and the vendor's own [case study](https://kraken.tech/case-studies/eon-next) describes an "API-first architecture and GraphQL-enabled services". The same platform under Octopus Energy's brand powers a real public developer portal at `developer.octopus.energy`. Licensing an API-first platform does not license an API-first posture.

## Common Properties

- [Website](https://www.eonnext.com/)
- [LinkedIn](https://www.linkedin.com/company/e-on-next)
- [Blog](https://www.eonnext.com/blog)
- [Support](https://www.eonnext.com/help)
- [Forum](https://community.eonnext.com/)
- [Pricing](https://www.eonnext.com/tariffs)
- [About](https://www.eonnext.com/about)
- [Privacy](https://www.eonnext.com/privacy)
- [security.txt](https://www.eonnext.com/.well-known/security.txt)

## Maintainers

- Kin Lane — kin@apievangelist.com
