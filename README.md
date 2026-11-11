# DPLA API — Postman Collection

A Postman (v2.1) collection of 18 requests for the **[Digital Public Library of America](https://dp.la) API (v2)**. DPLA gives one search across about 50 million items from US libraries, archives, museums and state digital libraries: photographs, newspapers, city directories, local histories, oral histories and more.

**Import link** (Postman → Import → Link):
```
https://raw.githubusercontent.com/mikeyeves/DPLA-API-Postman/main/DPLA_API.postman_collection.json
```

## Setup (one time)
1. Open the collection's **Variables** and set `email` to your own address.
2. Run **0. Get an API key → Request a free API key** (POST). DPLA emails you a 32-character key.
3. Paste the key into the `dpla_api_key` variable. The collection-level API-key auth then adds `api_key=…` to every request automatically.

## Folders
| Folder | Requests | Notes |
|---|---|---|
| 0. Get an API key | 1 | `POST /v2/api_key/{email}` |
| ★ Search items | 12 | Keyword search, title phrase, obituaries, genealogy subjects, date range, place, state, type, contributing institution, facets, sorting, nearest to a point |
| Items | 2 | Look up one item by id, or up to 50 at once |
| Collections | 3 | Search collections and list the items in one |

Each search request has a **Visualizer** table showing title, date, type, place, contributing institution and a thumbnail.

## Status
DPLA requires a key, so these requests have **not been run live**. They follow the official [DPLA API reference](https://pro.dp.la/developers/requests). An unauthenticated call returns `invalid_api_key`, which confirms the endpoint is up.

## Query cheat-sheet
| Goal | parameters |
|---|---|
| Keyword | `q=Krupl` or `q=Krupl OR Krüpl` or `q=Bukov*` |
| Field search | `sourceResource.title="..."`, `sourceResource.description=...`, `sourceResource.subject.name=Genealogy` |
| Dates | `sourceResource.date.after=1880&sourceResource.date.before=1930` |
| Place | `sourceResource.spatial=Passaic`, `sourceResource.spatial.state=New Jersey` |
| Exact field match | `provider.name=...&exact_field_match=true` |
| Paging | `page_size` (max 500), `page` (max 100) |
| Facets | `facets=provider.name,sourceResource.type&page_size=0` |

## Genealogy tips
- DPLA aggregates the US state digital newspaper and photo projects, such as the Digital Library of Georgia, Portal to Texas History and Ohio Memory. Searching **surname + town** often surfaces local photos, directories and church histories.
- The `isShownAt` link takes you to the item on the contributing institution's website.

## Related collections
[Library of Congress / Chronicling America](https://github.com/mikeyeves/Library-of-Congress-API-Postman) · [FamilySearch](https://github.com/mikeyeves/FamilySearch-API-Postman) · [Trove](https://github.com/mikeyeves/Trove-API-Postman)

*Unofficial. Not affiliated with DPLA.*
