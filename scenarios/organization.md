# Organization

## Search
```http request
GET /cristin/organization?query=Universitet HTTP/1.1
Host: api.test.nva.aws.unit.no
Authorization: Bearer ***
```
Example response
```json
{
    "@context": "https://bibsysdev.github.io/src/organization-context.json",
    "id": "https://api.test.nva.aws.unit.no/cristin/organization?depth=top&query=Universitet&page=1&results=5",
    "size": 6442,
    "searchString": "depth=top&query=Universitet&page=1&results=5",
    "processingTime": 1262,
    "firstRecord": 1,
    "nextResults": "https://api.test.nva.aws.unit.no/cristin/organization?depth=top&query=Universitet&page=2&results=5",
    "previousResults": null,
    "hits": [
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/11120006.0.0.0",
            "labels": {
                "en": "Universiteti 'Marin Barleti'",
                "nb": "Universiteti 'Marin Barleti'"
            },
            "acronym": "UMB",
            "country": "AL"
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/13600013.0.0.0",
            "labels": {
                "en": "Aleksandro Stulginskio universitetas",
                "nb": "Aleksandro Stulginskio universitetas"
            },
            "acronym": "L_UU",
            "country": "LT"
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/13620015.0.0.0",
            "labels": {
                "en": "Vilniaus Pedagoginis Universitetas",
                "nb": "Vilniaus Pedagoginis Universitetas"
            },
            "acronym": "VDU",
            "country": "LT"
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/16100001.0.0.0",
            "labels": {
                "en": "Universiteti i Prishtinës \"Hasan Prishtina\"",
                "nb": "Universiteti i Prishtinës \"Hasan Prishtina\"",
                "nn": "Universiteti i Prishtinës \"Hasan Prishtina\""
            },
            "acronym": "UNIPR",
            "country": "XK"
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/11120009.0.0.0",
            "labels": {
                "en": "University \"Aldent\"",
                "nb": "Universiteti \"Aldent\"",
                "nn": "Universiteti \"Aldent\""
            },
            "acronym": "UA",
            "country": "AL"
        }
    ]
}
```
## Fetch by id
```http request
GET /cristin/organization/20754.0.0.0 HTTP/1.1
Host: api.test.nva.aws.unit.no
Content-Type: application/json; version=2023-05-26
Authorization: Bearer ***

```
Example response
```json
{
    "@context": "https://bibsysdev.github.io/src/organization-context.json",
    "type": "Organization",
    "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.0.0.0",
    "labels": {
        "en": "Sikt - Norwegian Agency for Shared Services in Education and Research",
        "nb": "Sikt – Kunnskapssektorens tjenesteleverandør"
    },
    "acronym": "SIKT",
    "country": "NO",
    "hasPart": [
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.4.0.0",
            "labels": {
                "en": "The Organisational Development Department",
                "nb": "Avdeling for organisasjonsutvikling",
                "nn": "Avdeling for organisasjonsutvikling"
            }
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.3.0.0",
            "labels": {
                "en": "The Organisational Development Department",
                "nb": "Divisjon data og infrastruktur",
                "nn": "Divisjon for data og infrastruktur"
            }
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.5.0.0",
            "labels": {
                "en": "The Corporate Governance Department",
                "nb": "Avdeling for virksomhetsstyring",
                "nn": "Avdeling for verksemdstyring"
            }
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.1.0.0",
            "labels": {
                "en": "The Education and Administration Division",
                "nb": "Divisjon utdanning og administrasjon",
                "nn": "Divisjon for utdanning og administrasjon"
            }
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.2.0.0",
            "labels": {
                "en": "The Research and Education Resources Division",
                "nb": "Divisjon forsknings- og kunnskapsressurser",
                "nn": "Divisjon for forskings- og kunnskapsressursar"
            }
        },
        {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/20754.6.0.0",
            "labels": {
                "en": "The Customer and Communication Department",
                "nb": "Avdeling for kunde og kommunikasjon",
                "nn": "Avdeling for kunde og kommunikasjon"
            }
        }
    ]
}
```

## Persons affiliated with an organization
The endpoint supports paging by using the following query parameters:
* page, the page number; starts at page 1
* results, number of results per page; defaults to 5


```http request
GET /cristin/organization/20754.0.0.0/persons HTTP/1.1
Host: api.test.nva.aws.unit.no
Authorization: Bearer ***

```
Example response
```json
{
  "id": "https://api.nva.unit.no/cristin/organization/260.0.0.0/persons?page=1&results=5",
  "size": 155,
  "searchString": "page=1&results=5",
  "processingTime": 991,
  "firstRecord": 1,
  "nextResults": "https://api.nva.unit.no/cristin/organization/260.0.0.0/persons?page=2&results=5",
  "previousResults": null,
  "hits": [
    {
      "id": "https://api.nva.unit.no/cristin/person/dddddd",
      ...
    },
    ...
  ]
}
```

Note: if you further want to look up results where persons hare contributed, check [this](./publication.md#by-a-specific-contributor).