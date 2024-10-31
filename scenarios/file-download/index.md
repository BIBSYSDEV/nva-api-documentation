# File download in the NVA API

:warning: Note: we are currently working on some changes to files and file download that will not be backwards compatible.

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
GET /download/public/{publicationIdentifier}/files/{fileIdentifier}
Host: api.test.nva.aws.unit.no
Accept: application/json
Authorization: Bearer {token}
```
where <code>publicationIdentifier</code> would be <code>01907a72374b-6f71bda5-d5c9-43e6-b6de-a9c5161b7e7f</code>, and <code>fileIdentifier</code> would be <code>4e1ea619-93b6-45d8-9dc6-9a55755acfa6</code>.

The response would look something like:
```json
{
  "id": "<AWS S3 presigned url",
  "shortenedVersion": "<shorter url to use for generating preview in tools that do not support long urls>",
  "expires": "2024-10-10T10:13:00.000Z"
}
```

You can use one of the urls in the response to actually download the file.