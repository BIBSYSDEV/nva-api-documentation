# Upload student degree thesis to NVA

## Upload files
See [file upload](../file-upload/index.md)

## Common data
```json
{
  "entityDescription": {
    "mainTitle": "The title of the bachelor degree thesis",
    "alternativeTitles": {
      "nb": "Tittelen til bachelor grad oppgaven"
    },
    "language": "en",
    "publicationDate": {
      "year": "2023",
      "month": "01",
      "day": "01"
    },
    "contributors": [{
      
    }],
    "mainLanguageAbstract": "",
    "alternativeAbstracts": {
      
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

## Publication context
The publication context must indicate that this is a "Degree" context, the remaining fields are filled according to current practice at the institution. 

**publisher**: Depending on the practice at the insitution, the publisher may be an institution, a faculty or department, otherwise the author.

**series**: If the degree belongs to a series (typically relevant for PhD-level studies).

**seriesNumber**: See _series_.

**isbnList**: Values for ISBN for the electronic, paperback and hardback (and potentially other) editions.

Example:
```json
{
  ...
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        "publisher": {},
        "series": {},
        "seriesNumber": "",
        "isbnList": []
      }
    },
    ...
  }
  ...
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
  ...
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        ...
      },
      "publicationInstance": {
        "type": "DegreeBachelor",
        "pages": {},
        "submittedDate": {}
      },
      ...
    }
  }
  ...
}
```
### Master degree thesis
```json
{
  ...
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        ...
      },
      "publicationInstance": {
        "type": "DegreeMaster",
        "pages": {},
        "submittedDate": {}
      }
    }
  }
  ...
}
```
### PhD degree thesis
```json
{
  ...
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        ...
      },
      "publicationInstance": {
        "type": "DegreePhd",
        "pages": {},
        "submittedDate": {}
      }
    }
  }
  ...
}
```
### Licentiate degree thesis
```json
{
  ...
  "entityDescription": {
    "reference": {
      "type": "Reference",
      "publicationContext": {
        "type": "Degree",
        ...
      },
      "publicationInstance": {
        "type": "DegreeLicentiate",
        "pages": {},
        "submittedDate": {}
      }
    }
  }
  ...
}
```
