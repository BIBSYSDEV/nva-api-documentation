# Publication

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
