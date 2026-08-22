# E.ON Next (eon-next)

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

E.ON Next Energy Limited is the United Kingdom retail supply arm of the E.ON Group, formed after E.ON's 2019 acquisition of npower and serving roughly five million British households and small businesses with electricity, gas, smart meters, solar, home batteries, heat pumps and EV charging tariffs. It sits at the retail end of the GB energy value chain — buying wholesale, settling through Elexon, reading SMETS2 smart meters over the licensed Smart DCC network, and billing the customer — and it runs its entire operation on Kraken, the API-first, GraphQL-based energy operating system licensed from Kraken Technologies (Octopus Energy Group), onto which 5.8 million customers were migrated between June 2020 and June 2022. Its API posture is the exact opposite of its platform's reputation: the Kraken architecture underneath is API-first, but almost nothing is published outward. There is no developer portal, no API documentation, no OpenAPI, and no third-party route to a customer's usage or billing data; developer.eonnext.com and docs.eonnext.com do not resolve, and both api.eonnext.com and data.eonnext.com answer every path with an unauthenticated AWS API Gateway 403 "Missing Authentication Token". The one machine-readable contract E.ON Next does publish is its customer identity layer — auth.eonnext.com, an Auth0 CIAM tenant, serves a complete anonymous OpenID Connect / RFC 8414 discovery document and JWKS — which describes how a customer signs in, not how a developer gets access. Britain mandated the metering infrastructure, not the data right: E.ON Next is bound by the Smart Energy Code and the DCC, which is live and implemented, but no consumer data-portability mandate equivalent to Australia's CDR or Ontario's Green Button applies to it, and none of the open GB market data (NESO Carbon Intensity, Elexon BSC, DNO open-data portals) originates here. Consumer data is closed, market data is published by other parties, and the only public contract is identity.

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
- Identity

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

**E.ON Next Customer Identity (OpenID Connect)** — `https://auth.eonnext.com/` — the only machine-readable contract E.ON Next publishes. An Auth0-hosted E.ON group CIAM tenant (certificate CN `eon-next-uk.eon-ciam.auth0app.com`) that serves a complete anonymous [OIDC discovery document](https://auth.eonnext.com/.well-known/openid-configuration), the RFC 8414 [authorization-server metadata](https://auth.eonnext.com/.well-known/oauth-authorization-server) alias, and the [JWKS](https://auth.eonnext.com/.well-known/jwks.json). It authenticates customers into the online account and mobile app. It is not a developer programme: no third-party client registration path is documented, no resource server or domain scope is advertised, and no energy data is reachable through it.

_No developer API, and no consumer data API, is documented by E.ON Next._

The full probe is recorded in [review.yml](review.yml). Every candidate developer host and path was checked anonymously on 2026-07-27 and re-checked in the round-2 enrichment sweep: `developer.eonnext.com`, `developers.eonnext.com`, `docs.eonnext.com` and `status.eonnext.com` do not resolve; `api.eonnext.com` and `data.eonnext.com` return the AWS API Gateway `{"message":"Missing Authentication Token"}` 403 on every path including `/v1/graphql/`, `/openapi.json`, `/openapi.yaml`, `/swagger.json`, `/api-docs`, `/redoc`, `/rapidoc` and `/health`; and `/developers`, `/api`, `/docs`, `/data`, `/open-data`, `/api-docs` and `/llms.txt` on `www.eonnext.com` all return 404. The company's own sitemap index enumerates 414 URLs, none of which contain a developer, API, docs, or open-data path segment. No first-party SDK exists in npm or PyPI.

## Regulatory Posture

- **Mandate regime:** `smart-meter-infrastructure` — the GB Smart Metering Implementation Programme, the Smart Energy Code, and the licensed Smart DCC monopoly.
- **Mandate status:** `live-implemented`, **for the infrastructure obligation only**. Smart meters are installed and communicating over the DCC, and SEC accession is mandatory for every GB supplier. That mandate produces no supplier-published endpoint — the API in this regime belongs to the DCC, not to E.ON Next.
- **Consumer data right:** none. There is no UK equivalent of Australia's CDR (energy) or Ontario's Green Button regulation. DESNZ's energy smart data scheme call for evidence closed 10 March 2025 with no published government response, and smart data schemes under the Data (Use and Access) Act 2025 require sector-specific secondary legislation that has not been made for energy.
- **Data standard:** SMETS2 / Smart Energy Code infrastructure only. No Green Button/ESPI, CDR Consumer Data Standards, OCPP/OCPI, OpenADR, IEEE 2030.5, or IEC CIM reference found.
- **Consumer data vs market data:** closed on both. No consumer usage/billing API, and no open grid or market data — in Britain that is published by NESO, Elexon, and the DNOs, not by a retailer.
- **Access gate:** `none-published`. A developer wanting GB smart-meter data programmatically must become a Smart Energy Code party in the DCC "Other User" role, or use a consent intermediary that already holds that status. The route bypasses the supplier by design.
- **Auth model:** customer identity only. `auth.eonnext.com` (Auth0 CIAM) serves a full anonymous OIDC/RFC 8414 discovery document — authorization code with PKCE, device code, CIBA, token exchange, `private_key_jwt` and mTLS client authentication with certificate-bound tokens, DPoP (ES256), and a dedicated MFA challenge endpoint. Every advertised scope is a standard OIDC or Auth0 claim scope; there is no domain scope and no resource server. No API-key programme, no partner accreditation, and no documented third-party client registration. See [authentication/](authentication/eon-next-authentication.yml) and [scopes/](scopes/eon-next-scopes.yml).

## Platform Note

E.ON Next runs on Kraken and the vendor's own [case study](https://kraken.tech/case-studies/eon-next) describes an "API-first architecture and GraphQL-enabled services". The same platform under Octopus Energy's brand powers a real public developer portal at `developer.octopus.energy`. Licensing an API-first platform does not license an API-first posture.

## Artifacts

- [well-known/](well-known/eon-next-well-known.yml) — every `/.well-known/` path on every host with its observed status, plus the harvested [security.txt](well-known/eon-next-security.txt), [OIDC discovery](well-known/eon-next-openid-configuration.json), [RFC 8414 metadata](well-known/eon-next-oauth-authorization-server.json) and [JWKS](well-known/eon-next-jwks.json).
- [authentication/](authentication/eon-next-authentication.yml) — the OIDC/OAuth 2.0 posture of `auth.eonnext.com`, and the undisclosed AWS API Gateway scheme on `api`/`data`.
- [scopes/](scopes/eon-next-scopes.yml) — the 14 advertised scopes. All identity, zero domain scopes.
- [conformance/](conformance/eon-next-conformance.yml) — the identity standards implemented, and the API and energy-data standards searched for and not found.
- [security/](security/eon-next-domain-security.yml) — TLS/HSTS/DNSSEC/CAA/SPF/DMARC across five hosts, and the [disclosure channel](security/eon-next-vulnerability-disclosure.yml).
- [llms/](llms/eon-next-llms.txt) — what an agent can and cannot call here, generated (E.ON Next publishes no `llms.txt`).

## Common Properties

- [Website](https://www.eonnext.com/)
- [LinkedIn](https://www.linkedin.com/company/e-on-next)
- [Blog](https://www.eonnext.com/blog)
- [Support](https://www.eonnext.com/help)
- [Forum](https://community.eonnext.com/)
- [Pricing](https://www.eonnext.com/tariffs)
- [About](https://www.eonnext.com/about)
- [Login](https://www.eonnext.com/dashboard/sign-in)
- [Terms and Conditions](https://www.eonnext.com/terms-and-conditions)
- [Privacy](https://www.eonnext.com/privacy)
- [security.txt](https://www.eonnext.com/.well-known/security.txt)

## Maintainers

- Kin Lane — kin@apievangelist.com
