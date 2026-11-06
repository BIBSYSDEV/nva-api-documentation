# Migrating from Cristin API v2 to the NVA API

> **Disclaimer:** The `/cristin` prefix in the NVA API paths will be removed at some point. For example, `https://api.nva.unit.no/cristin/person/{identifier}` will become `https://api.nva.unit.no/person/{identifier}`.

Cristin API v2 (`https://api.cristin.no/v2`) is being deprecated. This guide shows how to move from the Cristin API v2 endpoints that remain supported to the corresponding endpoints in the NVA API.

* NVA API: [https://api.nva.unit.no](https://api.nva.unit.no)
* NVA API documentation: [https://swagger-ui.nva.unit.no/#/](https://swagger-ui.nva.unit.no/#/)

| Cristin API v2 | NVA API |
|---|---|
| `GET /biobanks` | Not supported |
| `GET /biobanks/materials` | Not supported |
| [`GET /biobanks/{identifier}`](#get-biobanksidentifier) | `GET /cristin/biobank/{identifier}` |
| [`GET /biobanks/{identifier}/projects`](#get-biobanksidentifierprojects) | `GET /cristin/project?biobank={identifier}` |
| [`GET /countries`](#get-countries) | `GET /cristin/country` |
| `GET /fundings` | Not supported |
| [`GET /fundings/sources`](#get-fundingssources) | `GET /cristin/funding-sources` |
| `GET /fundings/{identifier}` | Not supported |
| [`GET /fundings/{identifier}/projects`](#get-fundingsidentifierprojects) | `GET /cristin/project?funding={funding-source-code:identifier}` |
| [`GET /fundings/{identifier}/results`](#get-fundingsidentifierresults) | `GET /search/resources?funding={funding-source-code:identifier}`, `GET /search/resources?funding_identifier={identifier}` |
| [`GET /institutions`](#get-institutions) | `GET /cristin/organization` |
| [`GET /institutions/{identifier}`](#get-institutionsidentifier) | `GET /cristin/organization/{identifier}` |
| [`GET /keywords`](#get-keywords) | `GET /cristin/keyword` |
| [`GET /keywords/{identifier}`](#get-keywordsidentifier) | `GET /cristin/keyword/{identifier}` |
| [`GET /persons`](#get-persons) | `GET /cristin/person` |
| [`GET /persons/affiliations/positions`](#get-personsaffiliationspositions) | `GET /cristin/position` |
| [`GET /persons/facets`](#get-personsfacets) | `GET /cristin/person` (aggregations version) |
| [`GET /persons/orcid`](#get-personsorcid) | `GET /cristin/person/orcid` |
| [`GET /persons/{identifier}`](#get-personsidentifier) | `GET /cristin/person/{identifier}` |
| [`GET /persons/{identifier}/picture`](#get-personsidentifierpicture) | `GET /cristin/person/{identifier}/picture` |
| [`GET /persons/{identifier}/results`](#get-personsidentifierresults) | `GET /search/resources?contributor={identifier}` |
| `GET /persons/{identifier}/users` | Not supported |
| [`GET /projects`](#get-projects) | `GET /cristin/project` |
| [`GET /projects/categories`](#get-projectscategories) | `GET /cristin/category/project` |
| [`GET /projects/facets`](#get-projectsfacets) | `GET /cristin/project` (aggregations version) |
| `GET /projects/participants/roles` | Not supported |
| [`GET /projects/{identifier}`](#get-projectsidentifier) | `GET /cristin/project/{identifier}` |
| `GET /projects/{identifier}/biobanks` | Not supported |
| `GET /projects/{identifier}/datasets` | Not supported |
| [`GET /results`](#get-results) | `GET /search/resources` |
| `GET /results/categories` | Not supported |
| [`GET /results/{identifier}`](#get-resultsidentifier) | `GET /publication/{identifier}` |
| [`GET /results/{identifier}/chapters`](#get-resultsidentifierchapters) | `GET /search/resources?id_not={identifier}&query={identifier}` |
| `GET /results/{identifier}/contributors` | Not supported |
| [`GET /units`](#get-units) | `GET /cristin/organization` |
| [`GET /units/{identifier}`](#get-unitsidentifier) | `GET /cristin/organization/{identifier}` |
| [`GET /units/{identifier}/results`](#get-unitsidentifierresults) | `GET /search/resources?unit={identifier}` |

---

## Biobanks

### `GET /biobanks/{identifier}`

Fetch a single biobank.

**NVA API:** `GET /cristin/biobank/{identifier}`

**Example**

```
GET https://api.nva.unit.no/cristin/biobank/1234
```

### `GET /biobanks/{identifier}/projects`

List the projects related to a biobank.

**NVA API:** There is no direct equivalent. Search for projects with the biobank identifier instead: `GET /cristin/project?biobank={identifier}`

**Example**

```
GET https://api.nva.unit.no/cristin/project?biobank=1234
```

---

## Countries

### `GET /countries`

List countries.

**NVA API:** `GET /cristin/country`

**Example**

```
GET https://api.nva.unit.no/cristin/country
```

---

## Fundings

### `GET /fundings/sources`

List funding sources.

**NVA API:** `GET /cristin/funding-sources`

**Example**

```
GET https://api.nva.unit.no/cristin/funding-sources
```

### `GET /fundings/{identifier}/projects`

List the projects connected to a funding.

**NVA API:** There is no direct equivalent. Search for projects with the funding source code and identifier instead: `GET /cristin/project?funding={funding-source-code:identifier}`

> **Note:** The NVA API endpoint is case sensitive.

**Example**

```
GET https://api.nva.unit.no/cristin/project?funding=NFR:1234
```

### `GET /fundings/{identifier}/results`

List the results (publications) connected to a funding.

**NVA API:** There is no direct equivalent. Search for resources instead, either with the funding source code and identifier, `GET /search/resources?funding={funding-source-code:identifier}`, or with the funding identifier, `GET /search/resources?funding_identifier={identifier}`.

> **Note:** The NVA API endpoint is case sensitive.

**Example**

```
GET https://api.nva.unit.no/search/resources?funding=NFR:1234
```

```
GET https://api.nva.unit.no/search/resources?funding_identifier=1234
```

---

## Institutions

### `GET /institutions`

Search for institutions.

**NVA API:** `GET /cristin/organization`

**Example**

```
GET https://api.nva.unit.no/cristin/organization
```

```
GET https://api.nva.unit.no/cristin/organization?query=universitet
```

### `GET /institutions/{identifier}`

Fetch a single institution.

**NVA API:** `GET /cristin/organization/{identifier}`

**Example**

```
GET https://api.nva.unit.no/cristin/organization/20754.0.0.0
```

---

## Keywords

### `GET /keywords`

Search for keywords.

**NVA API:** `GET /cristin/keyword`

**Example**

```
GET https://api.nva.unit.no/cristin/keyword
```

```
GET https://api.nva.unit.no/cristin/keyword?query=biology
```

### `GET /keywords/{identifier}`

Fetch a single keyword.

**NVA API:** `GET /cristin/keyword/{identifier}`

**Example**

```
GET https://api.nva.unit.no/cristin/keyword/1234
```

---

## Persons

### `GET /persons`

Search for persons.

**NVA API:** `GET /cristin/person`

**Example**

```
GET https://api.nva.unit.no/cristin/person
```

```
GET https://api.nva.unit.no/cristin/person?name=Ola%20Nordmann
```

```
GET https://api.nva.unit.no/cristin/person?organization=194
```

```
GET https://api.nva.unit.no/cristin/person?organization=Norges teknisk-naturvitenskapelige universitet
```

### `GET /persons/affiliations/positions`

List position codes.

**NVA API:** `GET /cristin/position`

**Example**

```
GET https://api.nva.unit.no/cristin/position
```

### `GET /persons/facets`

Search for persons with facets.

**NVA API:** `GET /cristin/person` with `Accept: application/json; version=2023-11-03-aggregations`

**Example**

```
GET https://api.nva.unit.no/cristin/person
Accept: application/json; version=2023-11-03-aggregations
```

### `GET /persons/orcid`

List persons with an ORCID.

**NVA API:** `GET /cristin/person/orcid`

**Example**

```
GET https://api.nva.unit.no/cristin/person/orcid
```

### `GET /persons/{identifier}`

Fetch a single person by Cristin person identifier.

**NVA API:** `GET /cristin/person/{identifier}`, where `{identifier}` is either the Cristin person identifier or the ORCID.

**Example**

```
GET https://api.nva.unit.no/cristin/person/1234
```

```
GET https://api.nva.unit.no/cristin/person/0000-1111-2222-3333
```

### `GET /persons/{identifier}/picture`

Fetch a person's picture.

**NVA API:** `GET /cristin/person/{identifier}/picture`

**Example**

```
GET https://api.nva.unit.no/cristin/person/1234/picture
```

### `GET /persons/{identifier}/results`

List a person's results (publications).

**NVA API:** There is no direct equivalent. Search for resources with the person identifier as contributor instead: `GET /search/resources?contributor={identifier}`

**Example**

```
GET https://api.nva.unit.no/search/resources?contributor=1234
```

---

## Projects

### `GET /projects`

Search for projects.

**NVA API:** `GET /cristin/project`

**Example**

```
GET https://api.nva.unit.no/cristin/project
```

```
GET https://api.nva.unit.no/cristin/project?query=Lorem%20ipsum
```

```
GET https://api.nva.unit.no/cristin/project?title=Lorem%20ipsum
```

```
GET https://api.nva.unit.no/cristin/project?organization=https://api.dev.nva.aws.unit.no/cristin/organization/194.0.0.0
```

```
GET https://api.nva.unit.no/cristin/project?unit=194.0.0.0
```

```
GET https://api.nva.unit.no/cristin/project?biobank=1234
```

```
GET https://api.nva.unit.no/cristin/project?project_manager=Kari%20Nordmann
```

```
GET https://api.nva.unit.no/cristin/project?project_manager=1234
```

```
GET https://api.nva.unit.no/cristin/project?participant=Ola%20Nordmann
```

```
GET https://api.nva.unit.no/cristin/project?participant=1234
```

```
GET https://api.nva.unit.no/cristin/project?approval_reference_id={reference-id}
```

```
GET https://api.nva.unit.no/cristin/project?approved_by=REK
```

```
GET https://api.nva.unit.no/cristin/project?creator=1234
```

```
GET https://api.nva.unit.no/cristin/project?modified_since=2026-01-01
```

```
GET https://api.nva.unit.no/cristin/project?keyword=wind%20energy
```

```
GET https://api.nva.unit.no/cristin/project?status=active
```

```
GET https://api.nva.unit.no/cristin/project?funding_source=NFR
```

```
GET https://api.nva.unit.no/cristin/project?funding=NFR:1234
```

### `GET /projects/categories`

List project categories.

**NVA API:** `GET /cristin/category/project`

**Example**

```
GET https://api.nva.unit.no/cristin/category/project
```

### `GET /projects/facets`

Search for projects with facets.

**NVA API:** `GET /cristin/project` with `Accept: application/json; version=2023-11-03-aggregations`

**Example**

```
GET https://api.nva.unit.no/cristin/project
Accept: application/json; version=2023-11-03-aggregations
```

### `GET /projects/{identifier}`

Fetch a single project.

**NVA API:** `GET /cristin/project/{identifier}`

**Example**

```
GET https://api.nva.unit.no/cristin/project/1234
```

---

## Results

### `GET /results`

Search for results (publications).

**NVA API:** `GET /search/resources` with query parameters. See the [NVA Search Service documentation for resources](https://github.com/BIBSYSDEV/nva-search-api/blob/main/search-commons/src/main/java/no/unit/nva/search/resource/README.md) for the available parameters.

The response format is chosen with the `Accept` header. The default, `application/json`, is very verbose, so consider one of the other formats:

| `Accept` header | Response |
|---|---|
| `application/json` | Full response (default, very verbose) |
| `application/json; version=2024-12-01` | Simplified response |
| `text/x-bibtex` | BibTeX |
| `text/csv` | CSV |
| `application/ld+json; profile="https://schema.org"` | JSON-LD using the schema.org vocabulary |

**Example**

```
GET https://api.nva.unit.no/search/resources
```

```
GET https://api.nva.unit.no/search/resources?query=Lorem%20ipsum
```

```
GET https://api.nva.unit.no/search/resources?doi=10.1000/123456
```

```
GET https://api.nva.unit.no/search/resources?title=Lorem%20ipsum
```

```
GET https://api.nva.unit.no/search/resources?contributor=1234
```

```
GET https://api.nva.unit.no/search/resources?issn=1234-4321
```

```
GET https://api.nva.unit.no/search/resources?unit=194.0.0.0
```

```
GET https://api.nva.unit.no/search/resources?unit=194.0.0.0&exclude_subunits=true
```

```
GET https://api.nva.unit.no/search/resources?category=AcademicArticle
```

```
GET https://api.nva.unit.no/search/resources?published_since=2026-01-01
```

```
GET https://api.nva.unit.no/search/resources?published_before=2026-01-01
```

```
GET https://api.nva.unit.no/search/resources?created_since=2026-01-01
```

```
GET https://api.nva.unit.no/search/resources?created_before=2026-01-01
```

```
GET https://api.nva.unit.no/search/resources?modified_since=2026-01-01
```

```
GET https://api.nva.unit.no/search/resources?modified_before=2026-01-01
```

```
GET https://api.nva.unit.no/search/resources?scientific_report_period_since=2025
```

```
GET https://api.nva.unit.no/search/resources?scientific_report_period_before=2025
```

```
GET https://api.nva.unit.no/search/resources?funding=NFR:1234
```

```
GET https://api.nva.unit.no/search/resources?funding_identifier=1234
```

```
GET https://api.nva.unit.no/search/resources?funding_source=NFR
```

### `GET /results/{identifier}`

Fetch a single result (publication).

**NVA API:** `GET /publication/{identifier}`

**Example**

```
GET https://api.nva.unit.no/publication/1234
```

### `GET /results/{identifier}/chapters`

List the chapters of a book result.

**NVA API:** There is no direct equivalent. Search for resources that refer to the book, excluding the book itself, instead: `GET /search/resources?id_not={identifier}&query={identifier}`

**Example**

```
GET https://api.nva.unit.no/search/resources?id_not=1234&query=1234
```

---

## Units

### `GET /units`

Search for units.

**NVA API:** `GET /cristin/organization`

**Example**

```
GET https://api.nva.unit.no/cristin/organization
```

```
GET https://api.nva.unit.no/cristin/organization?query=universitet
```

### `GET /units/{identifier}`

Fetch a single unit.

**NVA API:** `GET /cristin/organization/{identifier}`

**Example**

```
GET https://api.nva.unit.no/cristin/organization/20754.1.2.3
```

### `GET /units/{identifier}/results`

List a unit's results (publications).

**NVA API:** There is no direct equivalent. Search for resources with the unit identifier instead: `GET /search/resources?unit={identifier}`

**Example**

```
GET https://api.nva.unit.no/search/resources?unit=20754.1.2.3&exclude_subunits=true
```
