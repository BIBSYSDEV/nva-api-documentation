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
          "name": "Studentesen, Student"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.sandbox.nva.aws.unit.no/cristin/organization/185.18.2.0"
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
          "name": "Medel-Svensson"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.sandbox.nva.aws.unit.no/cristin/organization/10600000.0.0.0"
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
          "id": "https://api.sandbox.nva.aws.unit.no/publication-channels-v2/series/6DA5EF2B-2DF5-4534-A2E5-E9E58C27324E/2023"
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
Host: api.sandbox.nva.aws.unit.no
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
          "name": "Studentesen, Student"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.sandbox.nva.aws.unit.no/cristin/organization/185.18.2.0"
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
          "name": "Medel-Svensson"
        },
        "affiliations": [
          {
            "type": "Organization",
            "id": "https://api.sandbox.nva.aws.unit.no/cristin/organization/10600000.0.0.0"
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
          "id": "https://api.sandbox.nva.aws.unit.no/publication-channels-v2/publisher/47A9D5D-EF68-4FDE-BD56-05733CD830FC/2023"
        },
        "series": {
          "type": "Series",
          "id": "https://api.sandbox.nva.aws.unit.no/publication-channels-v2/series/6DA5EF2B-2DF5-4534-A2E5-E9E58C27324E/2023"
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