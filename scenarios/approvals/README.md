# Approvals API

This is a thin service that reconciles the diverse spectrum of Approvals in use in Norwegian research.

The REST API allows the creation, management and dereferencing of Approval records. A record has a minimal, deliberate scope: it asserts that an approval exists, gives it a persistent identifier, and lists the names by which it is known.

## The identity model

Each concept has one role:

- **The IRI** (`https://api.nva.unit.no/approval/{uuid}`) is the identifier of the record. The UUID is its local part, not a separate identifier.
- **The Handle** is the persistent identifier for the approval, intended for citation and cross-system reference (i.e. use this as your identifier when referring to an Approval). It is expected to remain resolvable indefinitely.
- **The named identifiers** (e.g. `REK 2024/123`) are the reconciliation keys — the names by which the approval is already known to issuing bodies and source systems. Each name–value pair is unique across all Approvals, so there is exactly one record per real-world identifier.
- **The source** is the URI supplied at registration, pointing toward the system the registration was derived from. It is recorded as provenance, and is expected — but not guaranteed — to lead to further information about the approval. It carries no liveness guarantee: source systems change, and the source URI is not updated when they do.

The durable content of a record is the Handle and the named identifiers. The details of the approval itself — who granted it, when, and for what — remain with the issuing body and are not held by this service.

## What value does the Approvals API add?

Different source systems use different identifiers and different data structures, and most do not provide stable, addressable representations of individual approvals. Registering an Approval gives it a persistent, citable identifier, and a single place where its known identifiers resolve:

- By Handle: `GET /approval/?handle=https%3A%2F%2Fhdl.handle.net%2F11250.1%2F12345`
- By named identifier: `GET /approval/?name=REK&value=2024%2F123`

Because each name–value pair is unique (registration of an identifier already in use is rejected with `409 Conflict`), any system holding such an identifier can dereference the corresponding Approval without prior coordination.

## Using the API

Creation and update are asynchronous: `POST` and `PUT` return `202 Accepted` with a `Location` header pointing to the Approval and a `Retry-After` header indicating when to fetch it.

After creation, the identifier list can be updated. The `source` is fixed at creation — it records where the registration came from, which does not change — and there is no delete operation. Write operations require authentication; read operations are open.

## Data format and content

The data the API uses is [JSON-LD](https://www.w3.org/TR/json-ld11/), which allows strong semantics, and the decoupling of structure from semantics. Responses are available as both `application/json` and `application/ld+json` via content negotiation.

The [Approvals API @context](https://api.nva.unit.no/approval/context) maps the JSON keys used by the API to terms in the [Approvals ontology](https://api.nva.unit.no/approval/ontology) (namespace `https://nva.unit.no/approval#`), so the data can be interpreted directly as [RDF](https://www.w3.org/RDF/). This means that Approvals data from diverse sources can be aligned using RDF semantics, and data producers and consumers can align their own data with the Approvals API.

### How to align

You have a system that holds approvals, and you want them to be identifiable across systems:

- Create an Approval via the API, including the identifiers your system (and others) use for it
- Add the Handle to your data as the persistent identifier for the approval
- State that your data describes an https://nva.unit.no/approval#Approval (or a rdfs:subClassOf https://nva.unit.no/approval#Approval in your own ontology)

This allows a minimal alignment, and subclassing other properties from the Approvals ontology will allow further data alignment (via rdfs:subPropertyOf, or direct use of the properties in the Approvals ontology — directly, or via JSON-LD aliasing).
