# Graduaatsproject — Vesalius.ai

Uitbreiding van het Vesalius-platform voor een gerichtere configuratie van automatisch gegenereerde output.

## Projectbeschrijving

Dit project werd uitgevoerd binnen het ontwikkelingsteam van [Vesalius.ai](https://vesalius.ai) als onderdeel van het graduaatsproject **Graduaat in het Programmeren** aan HOGENT.

Het project is gebaseerd op bestaande JIRA-tickets die betrekking hebben op het verfijnen van automatisch gegenereerde output binnen het Vesalius-platform.

De belangrijkste functionaliteiten zijn:

- **Artsgebonden documenttemplates**
  - Een documenttemplate kan aan één of meerdere specifieke artsen worden gekoppeld.
  - Enkel gebruikers met de functie `arts` kunnen geselecteerd worden.
  - Automatische generatie kan hierdoor worden beperkt tot de gekoppelde arts(en).
  - Templates zonder artskoppeling behouden het bestaande gedrag.
  - Manuele generatie blijft beschikbaar voor alle gebruikers.
  - De zichtbaarheid van een template wordt niet gewijzigd.

- **Doelgroep voor Scribe-consultatemplates**
  - Een consultatietemplate kan worden ingesteld voor `patiënt` of `arts`.
  - Patiëntgerichte output is gericht op begrijpelijke mensentaal.
  - Artsgerichte output kan medische terminologie gebruiken.

## Scope

Het graduaatsproject richt zich uitsluitend op de twee bovenstaande functionaliteiten.

Het bredere backlog-item rond een **WYSIWYG-editor voor e-mails** valt buiten de scope van dit project. Ook andere templatecategorieën worden niet automatisch uitgebreid wanneer hun werking afwijkt van de onderzochte document- en Scribe-templates.

## Technologische stack

| Onderdeel | Technologie |
|---|---|
| Backend | PHP / Laravel |
| Frontend | Angular / TypeScript |
| Styling | HTML / SCSS |
| Database | MySQL |
| Authenticatie | Keycloak |
| Caching / tijdelijke gegevens | Redis |
| Containerisatie | Docker |
| Infrastructuur | Kubernetes / Terraform |
| CI/CD | CodeFresh |
| Versiebeheer | Git / Bitbucket |
| Projectbeheer | Jira |
| Ontwikkelomgeving | Visual Studio Code / WSL2 |

De bestaande technologieën van Vesalius.ai worden behouden zodat de nieuwe functionaliteit aansluit bij de bestaande architectuur, ontwikkelstandaarden en infrastructuur.

## Projectstructuur

De functionaliteit wordt geïntegreerd in de bestaande Vesalius.ai-codebase.

De belangrijkste onderdelen zijn:

```text
Frontend
└── Angular / TypeScript
    └── Templateconfiguratie en gebruikersinterface

Backend
└── Laravel / PHP
    └── Businesslogica en API-functionaliteit

Database
└── MySQL
    └── Template- en configuratiegegevens

Authentication
└── Keycloak
    └── Gebruikersidentiteit en toegangscontext
```

De exacte structuur kan verschillen afhankelijk van de bestaande Vesalius.ai-codebase en wordt daarom niet los van de oorspronkelijke applicatiestructuur gereorganiseerd.

## Ontwikkeling

Het project wordt ontwikkeld binnen de bestaande ontwikkelomgeving van Vesalius.ai.

Voor lokale ontwikkeling wordt onder andere gebruikgemaakt van:

- Windows 11
- WSL2 / Ubuntu
- Docker
- Visual Studio Code
- Git
- Bitbucket

Functionele vereisten en voortgang worden opgevolgd via Jira. Wijzigingen worden versiebeheerd met Git.

## Testen

De functionaliteit wordt gevalideerd aan de hand van de acceptatiecriteria uit de betreffende JIRA-tickets.

Belangrijke testscenario's zijn onder andere:

- templates zonder artskoppeling;
- templates met één of meerdere gekoppelde artsen;
- filtering van gebruikers op functie `arts`;
- automatische versus manuele generatie;
- behoud van bestaande functionaliteit;
- patiëntgerichte en artsgerichte Scribe-output.

## AI-gebruik

Tijdens de ontwikkeling kan generatieve AI als ondersteunend hulpmiddel worden gebruikt voor onder andere:

- analyse van foutmeldingen;
- uitleg van bestaande code;
- vergelijking van technische oplossingsrichtingen;
- ondersteuning bij codeontwikkeling;
- structurering en taalcontrole van documentatie.

AI vervangt de eigen analyse of technische besluitvorming niet. Voorgestelde oplossingen worden gecontroleerd, aangepast en getest voordat ze worden gebruikt.

Een volledige verantwoording van het AI-gebruik is opgenomen in het graduaatsprojectrapport.

## Privacy en vertrouwelijkheid

Het project maakt deel uit van een professioneel medisch softwareplatform. Vertrouwelijke bedrijfsinformatie, persoonsgegevens, medische gegevens, wachtwoorden, API-sleutels en andere gevoelige gegevens worden niet publiek beschikbaar gesteld.

De repository kan daarom beperkte of niet-publieke toegang hebben. Raadpleeg de projectdocumentatie en de afspraken met Vesalius.ai voor de toegestane ontwikkel- en testomgeving.

## Auteur

**Sarah Turner**  
Graduaat in het Programmeren — HOGENT  
Academiejaar 2026–2027 (1e semester)

## Bedrijf

**Vesalius.ai**

Het project werd uitgevoerd binnen het developmentteam van Vesalius.ai als onderdeel van een professionele stage en het graduaatsproject.
