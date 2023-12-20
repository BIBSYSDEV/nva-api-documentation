# Upload student degree thesis to NVA

## Upload files
See [file upload](../file-upload/index.md)

## Describing the thesis (entity description)
The metadata about the actually published work is contained within the `entityDescription` field. The important fields are:
* `language`
* `mainTitle`
* `alternativeTitles`
* `mainLanguageAbstract`
* `alternativeAbstracts`
* `contributors`
* `publicationDate`

```json
{
  "entityDescription": {
    "language": "http://lexvo.org/id/iso639-3/eng",
    "mainTitle": "The title of the bachelor thesis",
    "alternativeTitles": {
      "nb": "Tittelen til bachelor oppgaven, på norsk nokmål"
    },
    "mainLanguageAbstract": "The abstract of the bachelor thesis",
    "alternativeAbstracts": {
      "nb": "Sammendraget av bacheloroppgaven, på norsk bokmål"
    }
  }
}
```

The `publicationDate` is the date when the thesis was made officially available. Year is required, month and day is optional.
```json
{
  "entityDescription": {
    "language": "http://lexvo.org/id/iso639-3/eng",
    "mainTitle": "The title of the bachelor thesis",
    "alternativeTitles": {
      "nb": "Tittelen til bachelor oppgaven, på norsk nokmål"
    },
    "mainLanguageAbstract": "The abstract of the bachelor thesis",
    "alternativeAbstracts": {
      "nb": "Sammendraget av bacheloroppgaven, på norsk bokmål"
    },
    "publicationDate": {
      "year": "2023",
      "month": "01",
      "day": "01"
    },
    "npiSubjectHeading": "",
    "tags": [],
    "description": "",
    "metadataSource": ""
  },
  "associatedArtifacts": [],
  "projects": [],
  "subjects": [],
  "additionalIdentifiers": [],
  "fundings": [],
  "rightsHolder": "",
  "status": "PUBLISHED",
  "publicationNotes": []
}
```

### Contributors
The students that actually authored the thesis should be added with role `Creator`, while supervisors should be added with role `Supervisor`.

```json
{
  "entityDescription": {
    "language": "http://lexvo.org/id/iso639-3/eng",
    "mainTitle": "The title of the bachelor thesis",
    "alternativeTitles": {
      "nb": "Tittelen til bachelor oppgaven, på norsk nokmål"
    },
    "mainLanguageAbstract": "The abstract of the bachelor thesis",
    "alternativeAbstracts": {
      "nb": "Sammendraget av bacheloroppgaven, på norsk bokmål"
    },
    "publicationDate": {
      "year": "2023",
      "month": "01",
      "day": "01"
    },
    "contributors": [
      {
        "type": "Contributor",
        "identity": {
          "type": "Identity",
          "name": "Nordmann, Ola"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/185.18.2.0"
          }
        ],
        "role": {
          "type": "Creator"
        }
      },
      {
        "type": "Contributor",
        "identity": {
          "type": "Identity",
          "name": "Svensson, Medel"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/10600000.0.0.0"
          }
        ],
        "role": {
          "type": "Supervisor"
        }
      }
    ]
  }
}
```
See [Adding contributors](../create-publication/contributors.md) for more details on adding contributors.

## Publication context
The publication context must indicate that this is a "Degree" context, the remaining fields are filled according to current practice at the institution. 

**publisher**: Depending on the practice at the insitution, the publisher may be an institution, a faculty or department, otherwise the author.

**series**: If the degree belongs to a series (typically relevant for PhD-level studies).

**seriesNumber**: See _series_.

**isbnList**: Values for ISBN for the electronic, paperback and hardback (and potentially other) editions.

Example with a verified series from the Channel Register delivered by HKDIR:
```json
{
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        "publisher": {},
        "series": {
          "type": "Series",
          "id": "https://api.test.nva.aws.unit.no/publication-channels-v2/series/6DA5EF2B-2DF5-4534-A2E5-E9E58C27324E/2023"
        },
        "seriesNumber": "10",
        "isbnList": ["0-4345-6058-8"],
        "course": {
          "type": "UnconfirmedCourse",
          "code": "MAT100"
        },
        "additionalIdentifiers": [{
          "type": "AdditionalIdentifier",
          "sourceName": "ISBN",
          "value": "0-4345-6058-8"
        }]
      }
    }
  }
}
```

Example with an unconfirmed series:
```json
{
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        "publisher": {},
        "series": {
          "type": "UnconfirmedSeries",
          "title": "My unconfirmed series",
          "issn": "1144-875X",
          "onlineIssn": "2307-7301"
        },
        "seriesNumber": "10",
        "isbnList": ["0-4345-6058-8"],
        "course": {
          "type": "UnconfirmedCourse",
          "code": "MAT100"
        },
        "additionalIdentifiers": [{
          "type": "AdditionalIdentifier",
          "sourceName": "ISBN",
          "value": "0-4345-6058-8"
        }]
      }
    }
  }
}
```

## Publication instance
The publication instance must indicate the degree type, e.g. *DegreeBachelor*, *DegreeMaster*, *DegreePhd* or *DegreeLicentiate*.

### Shared data for degrees

#### Pages
Since all degrees are monographs, the page-type is "MonographPages".

**introduction**: (the preface) is not included in the total number of pages, and is often indicated by use of Roman numerals.
**pages**: The number of body text pages, prefer integers such as "311" rather than the traditional e.g. "311 p." or "311 pp.".
**illustrated**: If the text contains illustrations, photographs or figures.

Example:
```json
{
  "type": "MonographPages",
  "introduction": {
    "type": "Range",
    "begin": "i",
    "end": "xxiv"
  },
  "pages": "311",
  "illustrated": true
}
```

#### SubmittedDate

The submitted date may be a year, a year-and-month or a year-month-day.

While the data may be presented as non-Gregorian dates, e.g. 5784 Tevet 1, prefer Gregorian representations of dates.

Example:
```json
{
  "type": "PublicationDate",
  "year": "2023",
  "month": "01",
  "day": "31"
}
```

### Bachelor degree thesis
```json
{
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree"
      },
      "publicationInstance": {
        "type": "DegreeBachelor",
        "pages": {
          "type": "MonographPages",
          "introduction": {
            "type": "Range",
            "begin": "i",
            "end": "vi"
          },
          "pages": "157",
          "illustrated": true
        },
        "submittedDate": {
          "type": "PublicationDate",
          "year": "2023",
          "month": "01",
          "day": "31"
        }
      }
    }
  }
}
```
### Master degree thesis
```json
{
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree"
      },
      "publicationInstance": {
        "type": "DegreeMaster",
        "pages": {
          "type": "MonographPages",
          "introduction": {
            "type": "Range",
            "begin": "i",
            "end": "vi"
          },
          "pages": "157",
          "illustrated": true
        },
        "submittedDate": {
          "type": "PublicationDate",
          "year": "2023",
          "month": "01",
          "day": "31"
        }
      }
    }
  }
}
```
### PhD degree thesis
```json
{
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree"
      },
      "publicationInstance": {
        "type": "DegreePhd",
        "pages": {
          "type": "MonographPages",
          "introduction": {
            "type": "Range",
            "begin": "i",
            "end": "vi"
          },
          "pages": "157",
          "illustrated": true
        },
        "submittedDate": {
          "type": "PublicationDate",
          "year": "2023",
          "month": "01",
          "day": "31"
        }
      }
    }
  }
}
```
### Licentiate degree thesis
```json
{
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree"
      },
      "publicationInstance": {
        "type": "DegreeLicentiate",
        "pages": {
          "type": "MonographPages",
          "introduction": {
            "type": "Range",
            "begin": "i",
            "end": "vi"
          },
          "pages": "157",
          "illustrated": true
        },
        "submittedDate": {
          "type": "PublicationDate",
          "year": "2023",
          "month": "01",
          "day": "31"
        }
      }
    }
  }
}
```

## Associated artifacts and licences

### An administrative agreement
```json
{
  "type": "UnpublishableFile",
  "identifier": "8dd58b7e-5a90-4cde-853b-adc3a4681abf",
  "name":"thesis.pdf",
  "mimeType": "application/pdf",
  "size":"12356665",
  "license": "http://rightsstatements.org/vocab/InC/1.0/",
  "administrativeAgreement": true,
  "embargoDate": "2023-01-01T00:00:00Z",
  "rightsRetentionStrategy": {
    "type": "NullRightsRetentionStrategy"
  }
}
```

### A published file
```json
{
  "type": "PublishedFile",
  "identifier": "8dd58b7e-5a90-4cde-853b-adc3a4681abf",
  "name":"thesis.pdf",
  "mimeType": "application/pdf",
  "size":"12356665",
  "license": "http://rightsstatements.org/vocab/InC/1.0/",
  "administrativeAgreement": false,
  "embargoDate": "2023-01-01T00:00:00Z",
  "rightsRetentionStrategy": {
    "type": "NullRightsRetentionStrategy"
  },
  "publishedDate": "2022-12-01T00:00:00Z"
}
```

### Supported licences
* https://creativecommons.org/licenses/by/4.0
* https://creativecommons.org/licenses/by-nc/4.0
* https://creativecommons.org/licenses/by-nc-nd/4.0
* https://creativecommons.org/licenses/by-nc-sa/4.0
* https://creativecommons.org/licenses/by-sa/4.0
* https://creativecommons.org/licenses/by-nd/4.0
* https://creativecommons.org/publicdomain/zero/1.0
* http://rightsstatements.org/vocab/InC/1.0/

# Create the NVA record for the thesis
```http request
POST /publication HTTP/1.1
Host: api.test.nva.aws.unit.no
Content-Type: application/json
Authorization: Bearer ***

{
  "type": "Publication",
  "status": "PUBLISHED",
  "entityDescription": {
    "type": "EntityDescription",
    "mainTitle": "Eksempel på bacheloroppgave",
    "alternativeTitles": {
      "en": "Sample bachelor thesis"
    },
    "language": "http://lexvo.org/id/iso639-3/nob",
    "date": {
      "type": "PublicationDate",
      "year": "2023",
      "month": "08",
      "day": "21"
    },
    "contributors": [
      {
        "type": "Contributor",
        "identity": {
          "type": "Identity",
          "name": "Nordmann, Ola"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/185.18.2.0"
          }
        ],
        "role": {
          "type": "Creator"
        }
      },
      {
        "type": "Contributor",
        "identity": {
          "type": "Identity",
          "name": "Svensson, Medel"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.test.nva.aws.unit.no/cristin/organization/10600000.0.0.0"
          }
        ],
        "role": {
          "type": "Supervisor"
        }
      }
    ],
    "alternativeAbstracts": {
      "en": "Abstract for sample bachelor degree thesis."
    },
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        "publisher": {
          "type": "Publisher",
          "id": "https://api.test.nva.aws.unit.no/publication-channels-v2/publisher/47A9D5D-EF68-4FDE-BD56-05733CD830FC/2023"
        },
        "series": {
          "type": "Series",
          "id": "https://api.test.nva.aws.unit.no/publication-channels-v2/series/6DA5EF2B-2DF5-4534-A2E5-E9E58C27324E/2023"
        },
        "seriesNumber": "10",
        "isbnList": ["0-4345-6058-8"],
        "course": {
          "type": "UnconfirmedCourse",
          "code": "MAT100"
        }
      },
      "publicationInstance": {
        "type": "DegreeBachelor",
        "submittedDate": {
          "type": "PublicationDate",
          "year": "2023",
          "month": "02",
          "day": "01"
        }
      }
    },
    "abstract": "Eksempel sammendrag for bachelorgrad-oppgave"
  },
  "additionalIdentifiers": [
    {
      "type": "AdditionalIdentifier",
      "source": "inspera",
      "value": "no.usn:wiseflow:6602739:50548407"
    }
  ],
  "associatedArtifacts": [
    {
      "type": "PublishedFile",
      "identifier": "49665499-8d8f-4b3c-9eef-28f7f0474715",
      "name": "dev.nva:02.attachment 01.pdf",
      "mimeType": "application/pdf",
      "license": "http://rightsstatements.org/vocab/InC/1.0/"
    },
    {
      "type": "PublishedFile",
      "identifier": "852575ec-2776-4fc5-8255-6e2a1416ff6e",
      "name": "dev.nva:02.attachment 02.pdf",
      "mimeType": "application/pdf",
      "license": "http://rightsstatements.org/vocab/InC/1.0/"
    },
    {
      "type": "PublishedFile",
      "identifier": "73afb9ec-5f0e-45e7-bf12-716e57690d61",
      "name": "dev.nva:02.attachment 03.pdf",
      "mimeType": "application/pdf",
      "license": "http://rightsstatements.org/vocab/InC/1.0/"
    },
    {
      "type": "PublishedFile",
      "identifier": "831baeba-67bc-4ef9-92ff-7a8252701677",
      "name": "nva_dev:test_file02.pdf",
      "mimeType": "application/pdf",
      "license": "http://rightsstatements.org/vocab/InC/1.0/"
    }
  ]
}
```

The response will then be something like this:
```json
{
    "type": "Publication",
    "identifier": "018c86914d06-4419e8b0-2329-425d-821e-72b1eb669e0e",
    "status": "PUBLISHED",
    "resourceOwner": {
        "owner": "api01@185.90.0.0",
        "ownerAffiliation": "https://api.test.nva.aws.unit.no/cristin/organization/185.90.0.0"
    },
    "publisher": {
        "type": "Organization",
        "id": "https://api.test.nva.aws.unit.no/customer/5a823e16-38a3-4e5b-9436-d42ff514a99d",
        "labels": {}
    },
    "createdDate": "2023-12-20T09:31:58.598623195Z",
    "modifiedDate": "2023-12-20T09:31:58.598623195Z",
    "entityDescription": {
        "type": "EntityDescription",
        "mainTitle": "Eksempel på bacheloroppgave",
        "alternativeTitles": {
            "en": "Sample bachelor thesis"
        },
        "language": "http://lexvo.org/id/iso639-3/nob",
        "publicationDate": {
            "type": "PublicationDate",
            "year": "2023",
            "month": "08",
            "day": "21"
        },
        "contributors": [
            {
                "type": "Contributor",
                "identity": {
                    "type": "Identity",
                    "name": "Nordmann, Ola",
                    "additionalIdentifiers": []
                },
                "affiliations": [
                    {
                        "type": "Organization",
                        "id": "https://api.test.nva.aws.unit.no/cristin/organization/185.18.2.0",
                        "labels": {}
                    }
                ],
                "role": {
                    "type": "Creator"
                },
                "sequence": 1,
                "correspondingAuthor": false
            },
            {
                "type": "Contributor",
                "identity": {
                    "type": "Identity",
                    "name": "Svensson, Medel",
                    "additionalIdentifiers": []
                },
                "affiliations": [
                    {
                        "type": "Organization",
                        "id": "https://api.test.nva.aws.unit.no/cristin/organization/10600000.0.0.0",
                        "labels": {}
                    }
                ],
                "role": {
                    "type": "Supervisor"
                },
                "sequence": 2,
                "correspondingAuthor": false
            }
        ],
        "alternativeAbstracts": {
            "en": "Abstract for sample bachelor degree thesis."
        },
        "tags": [],
        "reference": {
            "type": "Reference",
            "publicationContext": {
                "type": "Degree",
                "series": {
                    "type": "Series",
                    "id": "https://api.test.nva.aws.unit.no/publication-channels-v2/series/6DA5EF2B-2DF5-4534-A2E5-E9E58C27324E/2023"
                },
                "seriesNumber": "10",
                "publisher": {
                    "type": "Publisher",
                    "id": "https://api.test.nva.aws.unit.no/publication-channels-v2/publisher/47A9D5D-EF68-4FDE-BD56-05733CD830FC/2023",
                    "valid": true
                },
                "isbnList": [
                    "9780434560585"
                ],
                "course": {
                    "type": "UnconfirmedCourse",
                    "code": "MAT100"
                },
                "additionalIdentifiers": [
                    {
                        "type": "AdditionalIdentifier",
                        "sourceName": "ISBN",
                        "value": "0-4345-6058-8"
                    }
                ]
            },
            "publicationInstance": {
                "type": "DegreeBachelor",
                "submittedDate": {
                    "type": "PublicationDate",
                    "year": "2023",
                    "month": "02",
                    "day": "01"
                }
            }
        },
        "abstract": "Eksempel sammendrag for bachelorgrad-oppgave"
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
            "publisherAuthority": false,
            "rightsRetentionStrategy": {
                "type": "NullRightsRetentionStrategy",
                "followsPolicy": true
            },
            "visibleForNonOwner": true
        }
    ],
    "additionalIdentifiers": [
        {
            "type": "AdditionalIdentifier",
            "sourceName": "inspera",
            "value": "no.usn:wiseflow:6602739:50548407"
        }
    ],
    "@context": {
        "@vocab": "https://nva.sikt.no/ontology/publication#",
        "xsd": "http://www.w3.org/2001/XMLSchema#",
        "id": "@id",
        "type": "@type",
        "affiliations": {
            "@id": "affiliation",
            "@container": "@set"
        },
        "activeFrom": {
            "@type": "xsd:dateTime"
        },
        "activeTo": {
            "@type": "xsd:dateTime"
        },
        "associatedArtifacts": {
            "@id": "associatedArtifact",
            "@container": "@set"
        },
        "additionalIdentifiers": {
            "@id": "additionalIdentifier",
            "@container": "@set"
        },
        "publicationNotes": {
            "@id": "publicationNote",
            "@container": "@set"
        },
        "alternativeTitles": {
            "@id": "alternativeTitle",
            "@container": "@language"
        },
        "approvals": {
            "@id": "approval",
            "@container": "@set"
        },
        "approvalStatus": {
            "@type": "@vocab",
            "@context": {
                "@vocab": "https://nva.sikt.no/ontology/publication#"
            }
        },
        "approvedBy": {
            "@type": "@vocab",
            "@context": {
                "@vocab": "https://nva.sikt.no/ontology/approvals-body#"
            }
        },
        "architectureOutput": {
            "@id": "architectureOutput",
            "@container": "@set"
        },
        "compliesWith": {
            "@id": "compliesWith",
            "@container": "@set"
        },
        "concertProgramme": {
            "@id": "concertProgramme",
            "@container": "@set"
        },
        "contributors": {
            "@id": "contributor",
            "@container": "@set"
        },
        "createdDate": {
            "@type": "xsd:dateTime"
        },
        "date": {
            "@type": "xsd:dateTime"
        },
        "doi": {
            "@type": "@id"
        },
        "duplicateOf": {
            "@type": "@id"
        },
        "embargoDate": {
            "@type": "xsd:dateTime"
        },
        "from": {
            "@type": "xsd:dateTime"
        },
        "handle": {
            "@type": "@id"
        },
        "indexedDate": {
            "@type": "xsd:dateTime"
        },
        "isbnList": {
            "@id": "isbn",
            "@container": "@set"
        },
        "labels": {
            "@id": "label",
            "@container": "@language"
        },
        "language": {
            "@type": "@id"
        },
        "link": {
            "@type": "@id"
        },
        "manifestations": {
            "@id": "manifestation",
            "@container": "@set"
        },
        "metadataSource": {
            "@type": "@id"
        },
        "modifiedDate": {
            "@type": "xsd:dateTime"
        },
        "musicalWorks": {
            "@id": "musicalWork",
            "@container": "@set"
        },
        "ownerAffiliation": {
            "@type": "@id"
        },
        "outputs": {
            "@id": "output",
            "@container": "@set"
        },
        "publishedDate": {
            "@type": "xsd:dateTime"
        },
        "nameType": {
            "@type": "@vocab",
            "@context": {
                "@vocab": "https://nva.sikt.no/ontology/publication#"
            }
        },
        "projects": {
            "@id": "project",
            "@container": "@set"
        },
        "fundings": {
            "@id": "funding",
            "@container": "@set"
        },
        "related": {
            "@id": "related",
            "@container": "@set"
        },
        "referencedBy": {
            "@id": "referencedBy",
            "@container": "@set"
        },
        "role": {
            "@type": "@vocab",
            "@context": {
                "@vocab": "https://nva.sikt.no/ontology/publication#"
            }
        },
        "source": {
            "@type": "@id"
        },
        "status": {
            "@type": "@vocab",
            "@context": {
                "@vocab": "https://nva.sikt.no/ontology/publication#"
            }
        },
        "subjects": {
            "@id": "subject",
            "@type": "@id",
            "@container": "@set"
        },
        "tags": {
            "@id": "tag",
            "@container": "@set"
        },
        "to": {
            "@type": "xsd:dateTime"
        },
        "trackList": {
            "@id": "trackList",
            "@container": "@set"
        },
        "venues": {
            "@id": "venue",
            "@container": "@set"
        }
    },
    "id": "https://api.test.nva.aws.unit.no/publication/018c86914d06-4419e8b0-2329-425d-821e-72b1eb669e0e"
}
```