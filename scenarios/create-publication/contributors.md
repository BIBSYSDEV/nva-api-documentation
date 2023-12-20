# Contributors

Contributors refer to every person or group of persons that have contributed to something that will be stored and published in NVA.

## Contributors
All publications have one or more contributors. A contributor is a person (or a group of persons) that have contributed somehow. Each contributor has an identity, one or more affiliations and a role
in regard to the publication at hand. In addition, each contributor has a sequence number and a boolean flag indicating if it is a corresponding author.
You should always strive to identify all the contributors. This has the benefit that the contributors would actually be credited for their contribution on their research profile in NVA automatically.

To identify a contributor by `id`, you actually need to search for and find the `id` for the person by searching in the [Person API](https://swagger-ui-internal.nva.unit.no/#/NVA%20Cristin%20Proxy%20API/ListPersons).
An identified contributor is recognized by having `identifier.id` populated with a valid URI.

```json
{
  "type": "Contributor",
  "identity": {
    "type": "Identity",
    "id": "https://api.test.nva.aws.unit.no/cristin/person/538786",
    "name": "Test, Test",
    "orcId": "http://orcid.org/0000-0001-5109-3700",
    "verificationStatus": "Verified|CannotBeEstablished|NotVerified",
    "additionalIdentifiers": [{
      "type": "AdditionalIdentifier",
      "sourceName": "SomeSystem",
      "value": "162534"
    }]
  },
  "affiliations": [{
    "type": "Organization",
    "id": "https://api.test.nva.aws.unit.no/cristin/organization/185.18.2.0"
  }],
  "role": {
    "type": "Creator"
  },
  "sequence": 1,
  "correspondingAuthor": false
}
```

## Affiliations
The affiliations of contributors should always refer to existing organizational units found through the [Organization API](https://swagger-ui-internal.nva.unit.no/#/NVA%20Cristin%20Proxy%20API/ListOrganizations).

```json
[
  {
    "type": "Organization",
    "id": "https://api.test.nva.aws.unit.no/cristin/organization/185.18.2.0"
  }
]
```
## Roles
The valid set of contributor roles are:
* AcademicCoordinator
* Actor
* Advisor
* Architect
* ArchitecturalPlanner
* Artist
* ArtisticDirector
* AudioVisualContributor
* Choreographer
* CollaborationPartner
* Composer
* Conductor
* Consultant
* Conservator
* ContactPerson
* CostumeDesigner
* Creator
* Curator
* CuratorOrganizer
* Dancer
* DataCollector
* DataCurator
* DataManager
* Designer
* Director
* Distributor
* Dramatist
* Dramaturge
* Editor
* EditorialBoardMember
* ExhibitionDesigner
* Funder
* HostingInstitution
* Illustrator
* InteriorArchitect
* InterviewSubject
* Journalist
* LandscapeArchitect
* Librettist
* LightDesigner
* Musician
* MuseumEducator
* Organizer
* RoleOther
* Producer
* Photographer
* ProductionDesigner
* ProgrammeLeader
* ProgrammeParticipant
* ProjectLeader
* ProjectManager
* ProjectMember
* Registrar
* RegistrationAgency
* RegistrationAuthority
* RelatedPerson
* Researcher
* ResearchGroup
* RightsHolder
* Scenographer
* Screenwriter
* Soloist
* SoundDesigner
* Supervisor
* TranslatorAdapter
* VfxSupervisor
* VideoEditor
* WorkPackageLeader
* Writer
