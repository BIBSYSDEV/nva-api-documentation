# Person

## Search

### By organization
```http request
GET /cristin/person?organization=20754

Host: api.test.nva.aws.unit.no
Accept: application/json

```
### By name
```http request
GET /cristin/person?name=Testesen
Host: api.test.nva.aws.unit.no
Accept: application/json

```
Example response
```json
{
    "@context": "https://example.org/person-search-context.json",
    "id": "https://api.test.nva.aws.unit.no/cristin/person?name=Testesen&page=1&results=5",
    "size": 5,
    "searchString": "name=Testesen&page=1&results=5",
    "processingTime": 3104,
    "firstRecord": 1,
    "nextResults": null,
    "previousResults": null,
    "hits": [
        {
            "id": "https://api.dev.nva.aws.unit.no/cristin/person/87",
            "type": "Person",
            "identifiers": [
                {
                    "type": "CristinIdentifier",
                    "value": "87"
                }
            ],
            "names": [
                {
                    "type": "FirstName",
                    "value": "Marit"
                },
                {
                    "type": "LastName",
                    "value": "Testesen"
                }
            ],
            "affiliations": [
                {
                    "type": "Affiliation",
                    "organization": "https://api.dev.nva.aws.unit.no/cristin/organization/185.15.5.0",
                    "active": true,
                    "role": {
                        "type": "Role",
                        "labels": {
                            "en": "Senior adviser",
                            "nb": "Seniorrådgiver"
                        }
                    }
                }
            ],
            "verified": true,
            "keywords": [],
            "background": {}
        },
        {
            "id": "https://api.dev.nva.aws.unit.no/cristin/person/515048",
            "type": "Person",
            "identifiers": [
                {
                    "type": "CristinIdentifier",
                    "value": "515048"
                }
            ],
            "names": [
                {
                    "type": "FirstName",
                    "value": "TUST"
                },
                {
                    "type": "LastName",
                    "value": "Testesen"
                }
            ],
            "affiliations": [
                {
                    "type": "Affiliation",
                    "organization": "https://api.dev.nva.aws.unit.no/cristin/organization/224.20.0.0",
                    "active": false,
                    "role": {
                        "type": "Role",
                        "labels": {
                            "en": "Head of department",
                            "nb": "Avdelingsleder"
                        }
                    }
                }
            ],
            "verified": true,
            "keywords": [],
            "background": {}
        },
        {
            "id": "https://api.dev.nva.aws.unit.no/cristin/person/1504353",
            "type": "Person",
            "identifiers": [
                {
                    "type": "CristinIdentifier",
                    "value": "1504353"
                }
            ],
            "names": [
                {
                    "type": "FirstName",
                    "value": "test"
                },
                {
                    "type": "LastName",
                    "value": "testesen"
                }
            ],
            "affiliations": [
                {
                    "type": "Affiliation",
                    "organization": "https://api.dev.nva.aws.unit.no/cristin/organization/186.26.26.0",
                    "active": true,
                    "role": {
                        "type": "Role",
                        "labels": {
                            "en": "Guest",
                            "nb": "Gjest"
                        }
                    }
                }
            ],
            "verified": true,
            "keywords": [],
            "background": {}
        },
        {
            "id": "https://api.dev.nva.aws.unit.no/cristin/person/515114",
            "type": "Person",
            "identifiers": [
                {
                    "type": "CristinIdentifier",
                    "value": "515114"
                }
            ],
            "names": [
                {
                    "type": "FirstName",
                    "value": "TEST"
                },
                {
                    "type": "LastName",
                    "value": "Testesen"
                }
            ],
            "affiliations": [
                {
                    "type": "Affiliation",
                    "organization": "https://api.dev.nva.aws.unit.no/cristin/organization/224.20.0.0",
                    "active": false,
                    "role": {
                        "type": "Role",
                        "labels": {
                            "en": "Head of department",
                            "nb": "Avdelingsleder"
                        }
                    }
                }
            ],
            "verified": true,
            "keywords": [],
            "background": {}
        },
        {
            "id": "https://api.dev.nva.aws.unit.no/cristin/person/1684656",
            "type": "Person",
            "identifiers": [
                {
                    "type": "CristinIdentifier",
                    "value": "1684656"
                }
            ],
            "names": [
                {
                    "type": "FirstName",
                    "value": "Test"
                },
                {
                    "type": "LastName",
                    "value": "Testesen"
                }
            ],
            "affiliations": [
                {
                    "type": "Affiliation",
                    "organization": "https://api.dev.nva.aws.unit.no/cristin/organization/20754.0.0.0",
                    "active": false,
                    "role": {
                        "type": "Role",
                        "labels": {
                            "nb": "Forsker"
                        }
                    }
                }
            ],
            "verified": false,
            "keywords": [],
            "background": {},
            "nvi": {
                "verifiedBy": {
                    "id": "https://api.dev.nva.aws.unit.no/cristin/person/1684650",
                    "firstName": "Mayli",
                    "lastName": "Munkebye",
                    "type": "Person"
                },
                "verifiedAt": {
                    "type": "Organization",
                    "id": "https://api.dev.nva.aws.unit.no/cristin/organization/20754.0.0.0",
                    "labels": {
                        "en": "Sikt - Norwegian Agency for Shared Services in Education and Research",
                        "nb": "Sikt – Kunnskapssektorens tjenesteleverandør"
                    },
                    "partOf": [
                        {
                            "type": "Organization",
                            "id": "https://api.dev.nva.aws.unit.no/cristin/organization/20754.0.0.0",
                            "labels": {
                                "en": "Sikt - Norwegian Agency for Shared Services in Education and Research",
                                "nb": "Sikt – Kunnskapssektorens tjenesteleverandør"
                            },
                            "acronym": "SIKT",
                            "country": "NO"
                        }
                    ]
                },
                "verifiedDate": "2024-01-05T09:10:39Z"
            }
        }
    ],
    "aggregations": {
        "organizationFacet": [
            {
                "key": "185",
                "id": "https://api.dev.nva.aws.unit.no/cristin/person?name=Testesen&organizationFacet=185&page=1&results=5",
                "count": 1,
                "labels": {
                    "en": "University of Oslo",
                    "nb": "Universitetet i Oslo"
                }
            },
            {
                "key": "186",
                "id": "https://api.dev.nva.aws.unit.no/cristin/person?name=Testesen&organizationFacet=186&page=1&results=5",
                "count": 1,
                "labels": {
                    "en": "UiT The Arctic University of Norway",
                    "nb": "UiT Norges arktiske universitet"
                }
            },
            {
                "key": "20754",
                "id": "https://api.dev.nva.aws.unit.no/cristin/person?name=Testesen&organizationFacet=20754&page=1&results=5",
                "count": 1,
                "labels": {
                    "en": "Sikt - Norwegian Agency for Shared Services in Education and Research",
                    "nb": "Sikt – Kunnskapssektorens tjenesteleverandør"
                }
            }
        ],
        "sectorFacet": [
            {
                "key": "UC",
                "id": "https://api.dev.nva.aws.unit.no/cristin/person?name=Testesen&page=1&results=5&sectorFacet=UC",
                "count": 4,
                "labels": {
                    "en": "Universities and colleges",
                    "nb": "Universitet og Høgskoler"
                }
            },
            {
                "key": "INSTITUTE",
                "id": "https://api.dev.nva.aws.unit.no/cristin/person?name=Testesen&page=1&results=5&sectorFacet=INSTITUTE",
                "count": 1,
                "labels": {
                    "en": "Institute Sector",
                    "nb": "Instituttsektoren"
                }
            }
        ]
    }
}
```

## Fetch by id
```http request
GET /cristin/person/87
Host: api.test.nva.aws.unit.no
Accept: application/json

```
Example response
```json
{
  "id": "https://api.dev.nva.aws.unit.no/cristin/person/87",
  "type": "Person",
  "identifiers": [
    {
      "type": "CristinIdentifier",
      "value": "87"
    }
  ],
  "names": [
    {
      "type": "FirstName",
      "value": "Marit"
    },
    {
      "type": "LastName",
      "value": "Testesen"
    }
  ],
  "affiliations": [
    {
      "type": "Affiliation",
      "organization": "https://api.dev.nva.aws.unit.no/cristin/organization/185.15.5.0",
      "active": true,
      "role": {
        "type": "Role",
        "labels": {
          "en": "Senior adviser",
          "nb": "Seniorrådgiver"
        }
      }
    }
  ],
  "verified": true,
  "keywords": [],
  "background": {}
}
```
## Promoted publications

```http request
GET /person-preferences/https%3A%2F%2Fapi.test.nva.aws.unit.no%2Fcristin%2Fperson%2F538786
Host: api.test.nva.aws.unit.no
Accept: application/json

```
Response:
```json
{
  "personId" : "https://api.test.nva.aws.unit.no/cristin/person/538786",
  "promotedPublications" : [ "https://api.test.nva.aws.unit.no/publication/018d221cf005-d3a8979d-04d8-4239-9788-673e0fa287c3" ]
}
```
