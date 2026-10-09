
# Graduaatsproject — Vesalius.ai

**WYSIWYG-e-maileditor — Proof of Concept**

## Projectbeschrijving

Dit project wordt uitgevoerd binnen het ontwikkelingsteam van [Vesalius.ai](https://vesalius.ai) als onderdeel van het graduaatsproject **Graduaat in het Programmeren** aan HOGENT.

Binnen het Vesalius-platform worden op vaste momenten automatisch e-mails verstuurd, bijvoorbeeld bij afspraakbevestigingen, herinneringen en annulaties. Momenteel is de aanpasbaarheid van deze e-mails beperkt: artsen en organisaties kunnen bepaalde huisstijlelementen configureren, maar hebben onvoldoende controle over de inhoud en opmaak van de meeste e-mailtypes.

Het doel van dit project is een zelfstandige proof of concept (PoC) te ontwikkelen van een visuele e-maileditor waarmee gebruikers de inhoud en opmaak van e-mails kunnen aanpassen, opslaan, vooraf bekijken en als testmail versturen.

## Functionaliteiten

De PoC omvat de volgende functionaliteiten:

- **Visuele e-maileditor**

  - E-mailinhoud aanpassen via een WYSIWYG-editor.
  - Tekstopmaak, titels, lijsten en hyperlinks ondersteunen.
  - Placeholders invoegen voor dynamische gegevens.
  - Opmaak uit externe bronnen, zoals Word, veilig verwerken.
- **E-mailtemplates beheren**

  - Templates opslaan en opnieuw laden per e-mailtype, taal en configuratie.
  - Terugvallen op een standaardtemplate wanneer geen aangepaste versie beschikbaar is.
  - Drie voorbeeld-e-mailtypes ondersteunen: afspraakbevestiging, herinnering en annulatie.
- **Rendering en beveiliging**

  - HTML-inhoud opschonen en onveilige elementen verwijderen.
  - Placeholders veilig vervangen door voorbeeldgegevens.
  - Een vaste e-mailschil toepassen met onder meer logo, kleuren en footer.
  - CSS inline verwerken en een tekstuele versie van de e-mail genereren.
- **Voorbeeldweergave en testverzending**

  - De gerenderde e-mail vooraf bekijken.
  - Testmails versturen naar een lokale testmailserver.
  - De weergave en compatibiliteit controleren in gangbare e-mailclients.

## Scope

Het graduaatsproject richt zich uitsluitend op de ontwikkeling en validatie van een zelfstandige PoC. De focus ligt op één visuele editor, drie voorbeeld-e-mailtypes, templateopslag, veilige rendering, voorbeeldweergave en testverzending.

De e-mailschil blijft binnen de PoC grotendeels vast, zodat de nadruk ligt op het aanpassen van de inhoud en opmaak van de e-mailbody.

De volgende onderdelen vallen buiten de scope:

- Integratie in het bestaande Vesalius-platform.
- Productieverzending en productieplanning van e-mails.
- Keycloak-e-mails.
- Verwerking van echte patiëntgegevens.
- Een volledig configureerbare layout-builder.
- Een volledige vervanging van de bestaande e-mailinfrastructuur.

De PoC moet een onderbouwde basis bieden voor een mogelijke latere integratie, zonder deze integratie zelf te realiseren.

## Technologische stack

| Onderdeel                    | Technologie                              |
| ---------------------------- | ---------------------------------------- |
| Frontend                     | Angular 21 / TypeScript                  |
| Visuele editor               | Quill 2                                  |
| Mock-API                     | Node.js / TypeScript / Express           |
| HTML-opschoning              | `sanitize-html`                        |
| Templates en placeholders    | Handlebars / eigen placeholderverwerking |
| CSS-inlining                 | `juice`                                |
| Tekstuele e-mailversie       | `html-to-text`                         |
| Templateopslag               | Tijdelijke opslagoplossing voor de PoC   |
| Mockgegevens                 | JSON-fixtures / Faker.js                 |
| Testverzending               | Nodemailer / Mailpit                     |
| Containerisatie testomgeving | Docker / Docker Compose                  |
| Geautomatiseerde tests       | Vitest / Playwright                      |
| Versiebeheer                 | Git / Bitbucket                          |
| Projectbeheer                | Jira                                     |
| Ontwikkelomgeving            | Visual Studio Code / WSL2 / Ubuntu       |

De gekozen technologieën ondersteunen een zelfstandige testopstelling die aansluit bij de bestaande frontendtechnologie van Vesalius.ai. De mock-API maakt het mogelijk om de editor en rendering afzonderlijk te ontwikkelen en te testen, zonder afhankelijk te zijn van de productieomgeving.

De definitieve keuze voor de editor en tijdelijke opslag wordt tijdens de ontwikkeling gevalideerd. De opslagtechnologie wordt niet vooraf vastgelegd op basis van de bestaande productiedatabase.

## Architectuur en projectstructuur

De PoC wordt als een afzonderlijke applicatie ontwikkeld en staat los van de bestaande Vesalius-codebase.

De beoogde projectstructuur is:

```text
email-editor-poc/
├── apps/
│   ├── web/                 # Angular-editor, preview en testinterface
│   └── mock-api/             # API, templatebeheer en rendering
├── fixtures/                 # Fictieve gegevens en voorbeeldtemplates
├── docs/
│   ├── proposition.md        # Projectvoorstel
│   ├── decisions.md          # Technische beslissingen
│   ├── test-matrix.md        # Testscenario's en resultaten
│   ├── worklog.md            # Voortgang per sprint
│   └── integration-notes.md  # Voorstel voor latere integratie
├── docker-compose.yml        # Lokale testomgeving met Mailpit
└── README.md
```

De frontend biedt de editor, voorbeeldweergave en testinterface aan. De mock-API verzorgt het opslaan en laden van templates, het verwerken van placeholders, de HTML-rendering en het versturen van testmails.

## Ontwikkeling

De ontwikkeling gebeurt iteratief in wekelijkse sprints, met een afgebakend resultaat per sprint. De voortgang, technische keuzes en eventuele problemen worden bijgehouden en regelmatig besproken met de bedrijfsmentor.

De belangrijkste ontwikkelactiviteiten zijn:

- Opzetten van de ontwikkel- en testomgeving.
- Analyseren van de vereisten en ontwerpen van de oplossing.
- Ontwikkelen van de editor en templateverwerking.
- Implementeren van veilige HTML-rendering en testverzending.
- Valideren van de uitvoer in verschillende e-mailclients.
- Documenteren van de resultaten en formuleren van een integratievoorstel.

## Testen en validatie

De oplossing wordt getest met fictieve gegevens en een combinatie van geautomatiseerde en handmatige controles.

De belangrijkste testscenario's omvatten:

- Aanpassen, opslaan en opnieuw laden van e-mailtemplates.
- Correcte vervanging en veilige verwerking van placeholders.
- Opschonen van HTML en voorkomen van ongewenste scriptuitvoering.
- Correcte verwerking van ontbrekende, ongeldige of speciale invoer.
- Correcte generatie van HTML- en tekstuele e-mailversies.
- Weergave van de drie voorbeeld-e-mailtypes in verschillende talen en configuraties.
- Controle van de e-mails in Gmail, Outlook.com en Apple Mail, waar beschikbaar.
- Controle van de rendering op verschillende schermformaten en van bekende compatibiliteitsproblemen.

De resultaten worden bijgehouden in een testmatrix met eventuele afwijkingen, screenshots en voorgestelde verbeteringen. Automatische tests worden gebruikt om regressies te detecteren en de belangrijkste beveiligings- en renderingvereisten te bewaken.

## AI-gebruik

Generatieve AI maakt geen deel uit van de functionaliteit van de PoC. Het project richt zich op voorspelbare tekstbewerking, templateverwerking en e-mailrendering.

AI kan eventueel als ondersteunend hulpmiddel worden gebruikt tijdens de ontwikkeling, bijvoorbeeld voor het analyseren van foutmeldingen, het vergelijken van technische oplossingsrichtingen en het structureren van documentatie. Voorgestelde oplossingen worden steeds kritisch beoordeeld en getest.

## Privacy en vertrouwelijkheid

Omdat Vesalius.ai actief is binnen een medische context, wordt bij de ontwikkeling rekening gehouden met de vertrouwelijkheid van bedrijfsinformatie en persoonsgegevens.

De PoC gebruikt uitsluitend fictieve patiëntgegevens en voorbeeldtemplates. Er worden geen echte patiëntgegevens, productiecredentials, API-sleutels of andere vertrouwelijke gegevens in de repository opgenomen.

De verwerking van HTML en dynamische placeholders wordt beveiligd tegen onveilige invoer. De uiteindelijke oplossing en het eventuele integratievoorstel houden rekening met de relevante principes van de Algemene Verordening Gegevensbescherming (AVG/GDPR).

## Verwachte opleveringen

Aan het einde van het graduaatsproject worden de volgende resultaten voorzien:

- Een werkende PoC van de visuele e-maileditor.
- Een lokale testomgeving met mock-API en testmailserver.
- Voorbeeldtemplates en reproduceerbare fictieve testgegevens.
- Geautomatiseerde tests en gedocumenteerde testresultaten.
- Een overzicht van de compatibiliteit met gangbare e-mailclients.
- Technische documentatie en een onderbouwd voorstel voor mogelijke integratie in Vesalius.ai.
- Een demonstratie van de gerealiseerde functionaliteiten.

## Auteur

**Sarah Turner Burkitt**
Graduaat in het Programmeren — HOGENT
Academiejaar 2026–2027 1e semester

## Bedrijf

**Vesalius.ai (dochterbedrijf van Endare)**

Het graduaatsproject wordt uitgevoerd in het kader van een professionele stage binnen het ontwikkelingsteam van Vesalius.ai.
