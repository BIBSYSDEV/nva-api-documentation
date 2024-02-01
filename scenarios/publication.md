# Publication

## Data model

```json
{
  "type": "Publication",
  "@context": "",
  "id": "https://api.test.nva.aws.unit.no/publication/018c86914d06-4419e8b0-2329-425d-821e-72b1eb669e0e",
  "identifier": "018c86914d06-4419e8b0-2329-425d-821e-72b1eb669e0e",
  "additionalIdentifiers": [],
  "status": "PUBLISHED",
  "resourceOwner": {
    "owner": "api01@185.90.0.0",
    "ownerAffiliation": "https://api.test.nva.aws.unit.no/cristin/organization/185.90.0.0"
  },
  "publisher": {
    "type": "Organization",
    "id": "https://api.test.nva.aws.unit.no/customer/5a823e16-38a3-4e5b-9436-d42ff514a99d"
  },
  "createdDate": "2023-12-20T09:31:58.598623195Z",
  "modifiedDate": "2023-12-20T09:31:58.598623195Z",
  "entityDescription": {
    "type": "EntityDescription",
    "mainTitle": "Tittel",
    "alternativeTitles": {
      "en": "English title"
    },
    "language": "http://lexvo.org/id/iso639-3/nob",
    "publicationDate": {
      "type": "PublicationDate",
      "year": "2023",
      "month": "08",
      "day": "21"
    },
    "contributors": [],
    "abstract": "Eksempel sammendrag for bachelorgrad-oppgave",
    "alternativeAbstracts": {
      "en": "English abstract"
    },
    "tags": [],
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "<context type>"
      },
      "publicationInstance": {
        "type": "<instance type>"
      }
    }
  },
  "projects": [],
  "fundings": [],
  "subjects": [],
  "associatedArtifacts": [
    {
      "type": "PublishedFile",
      "identifier": "59347ec1-57f8-4ab7-9bff-9a66ac9066af",
      "name": "my-thesis.pdf",
      "mimeType": "application/pdf",
      "license": "http://rightsstatements.org/vocab/InC/1.0/",
      "administrativeAgreement": false,
      "publisherAuthority": true,
      "visibleForNonOwner": true
    }
  ]
}

```
## Search

### By a specific contributor
```http request
GET /search/resources?contributor=https%3A%2F%2Fapi.test.nva.aws.unit.no%2Fcristin%2Fperson%2F538786 HTTP/1.1
Host: api.test.nva.aws.unit.no
Accept: application/json

```

### By title
```http request
GET /search/resources?title=My+very+specific+title HTTP/1.1
Host: api.test.nva.aws.unit.no
Accept: application/json

```

### By category
```http request
GET /search/resources?category=AcademicArticle&category=AcademicMonograph HTTP/1.1
Host: api.test.nva.aws.unit.no
Accept: application/json

```

### Free text
```http request
GET /search/resources?query=Some+specific+phrase HTTP/1.1
Host: api.test.nva.aws.unit.no
Accept: application/json

```

### All available filters
* category
* contributor
* created_before
* created_since
* doi
* funding
* funding_source
* id
* institution
* isbn
* issn
* orcid
* modified_before
* modified_since
* project_code
* published_before
* published_since
* title
* unit
* user
* year_reported

## Fetch by id
```http request
GET /publication/018a50f7ee5c-d8095d71-7c98-4cbe-996f-d9e520a68bdd HTTP/1.1
Host: api.test.nva.aws.unit.no
Content-Type: application/json
Authorization: Bearer ***

```
