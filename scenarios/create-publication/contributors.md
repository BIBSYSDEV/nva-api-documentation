# Contributors

Contributors refer to every person or group of persons that have contributed to something that will be stored and published in NVA.

## Contributors
You should always strive to identify all the contributors. This has the benefit that the contributors would actually be credited for their contribution on their research profile in NVA automatically.

To identify a contributor, you actually need to search for and find the `id` for the person by searching in the [Person API](https://swagger-ui-internal.nva.unit.no/#/NVA%20Cristin%20Proxy%20API/ListPersons). An identified contributor is recognized by having `identifier.id` populated with a valid URI.

```json
{
  "type": "Contributor",
  "identity": {
    "type": "Identity",
    "id": "https://api.sandbox.nva.aws.unit.no/cristin/person/538786",
    "name": "Test, Test",
    "nameType": "Organizational|Personal",
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
    "id": "https://api.sandbox.nva.aws.unit.no/cristin/organization/185.18.2.0",
    "labels": {
      "en": "My silly organization label"
    }
  }],
  "role": {
    "type": "Creator"
  },
  "sequence": 1,
  "correspondingAuthor": false
}
```

## Affiliations

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
