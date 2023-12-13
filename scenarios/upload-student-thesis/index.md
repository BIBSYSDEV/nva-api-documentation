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
The publication context must indicate that this is a degree context:
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
The publication instance must indicate what kind of degree we are dealing with.

### Shared data for degrees

#### Pages
Example:
```json
{
  "type": "MonographPages",
  "introduction": {
    "type": "Range",
    "begin": "10",
    "end": "20"
  },
  "pages": "10-20",
  "illustrated": true
}
```

#### SubmittedDate
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
