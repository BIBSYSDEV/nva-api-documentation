# nva-api-documentation
API documentation for NVA.

## System documentation

We provide standardized [C4 diagrams](https://c4model.com/) — for those who may be interested — in the `system` directory. To generate the diagrams, use the [C4-Structurizr](https://structurizr.com/dsl) or your favourite tool. At the present time, C4 diagrams are available for the System context only as this is relevant to most users. If a Container context is required, create an issue in this repository.

Please note, at the present time, there is no intention to make Component or Code context diagrams available as it is possible to generate sufficient diagrams from code (SAM-IaC and the code itself).

## API Servers
* Test: [https://api.test.nva.aws.unit.no](https://api.test.nva.aws.unit.no)
* Production: [https://api.nva.unit.no](https://api.nva.unit.no)

## API documentation
* Test: [https://swagger-ui.test.nva.aws.unit.no/#/](https://swagger-ui.test.nva.aws.unit.no/#/)
* Production: [https://swagger-ui.nva.unit.no/#/](https://swagger-ui.nva.unit.no/#/)


## Versioning
We have a few principles when it comes to versioning that all users of the API need to be aware of:
* We will never change or delete existing fields.
* We can add new fields without bumping the version.
* Clients must make sure they can handle "unknown" fields from the server responses.
* If we need to make changes that are not backward compatible, we will introduce a version property, e.g. `application/json; version=2023-05-26` that clients that are aware can ask for.
* Clients sending no `Accept`-header or the generic "application/json" will get the original version.
* If the original version is rarely used in the future, we might officially deprecate it and eventually remove it.
* Generally, we try to adhere to [Postel's Law / The Robustness Principle](https://en.wikipedia.org/wiki/Robustness_principle#:~:text=It%20is%20often%20reworded%20as,an%20early%20specification%20of%20TCP), which we suggest you do too ;)

## Scenarios
* [Authentication](scenarios/authenticating/index.md)
* [Organization search](scenarios/organization.md)
* [Person search](scenarios/person.md)
* [NVA Search Service](https://github.com/BIBSYSDEV/nva-search-api/blob/main/README.md)
   * [Resources (Publication)](https://github.com/BIBSYSDEV/nva-search-api/blob/main/search-commons/src/main/java/no/unit/nva/search/resource/README.md)
   * [Tickets](https://github.com/BIBSYSDEV/nva-search-api/blob/main/search-commons/src/main/java/no/unit/nva/search/ticket/README.md)
   * [Import Candidates](https://github.com/BIBSYSDEV/nva-search-api/blob/main/search-commons/src/main/java/no/unit/nva/search/importcandidate/README.md)
* [Publication search](scenarios/publication.md)
* [File upload](scenarios/file-upload/index.md)
* [Uploading student degree thesis](scenarios/upload-student-thesis/index.md)
