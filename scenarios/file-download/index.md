# File download in the NVA API

Given a publication that refers to a file in <code>associatedArtifacts</code>:

```json
{
  "type": "Publication",
  "identifier": "01907a72374b-6f71bda5-d5c9-43e6-b6de-a9c5161b7e7f",
  "associatedArtifacts": [
    {
      "type": "PublishedFile",
      "identifier": "4e1ea619-93b6-45d8-9dc6-9a55755acfa6",
      ...
    }
  ],
  ...
}
```

If you want to get a link to download the file, you need to use the following endpoints:

```html
GET /publication/{publicationIdentifier}/filelink/{fileIdentifier}
Host: api.test.nva.aws.unit.no
Accept: application/json
Authorization: Bearer {token}
```
where <code>publicationIdentifier</code> would be <code>01907a72374b-6f71bda5-d5c9-43e6-b6de-a9c5161b7e7f</code>, and <code>fileIdentifier</code> would be <code>4e1ea619-93b6-45d8-9dc6-9a55755acfa6</code>.

The response would look something like:
```json
{
    "type": "PresignedUriResponse",
    "fileIdentifier": "4e1ea619-93b6-45d8-9dc6-9a55755acfa6",
    "id": "<AWS S3 presigned URI>",
    "expires": "2024-11-07T09:41:04.843638375Z",
    "alias": "https://api.sandbox.nva.aws.unit.no/publication/file/019305fcf7ee-e5d405a9-604e-4d39-b132-c6b7a362a931"
}
```

You can use the `id` uri to download the file. Note that `expires` indicates when the file links expire. As the AWS S3 presigned uri in `id` might be very long, we also provide an `alias` uri for your convenience.
This is probably also better suited for previewing the file in the browser if you want to do that.