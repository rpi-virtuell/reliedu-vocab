# Religionspädagogisches Vokabular (ReLiEdu Vocabulary)

Kontrolliertes, SKOS-Vokabular für die AMB-konforme Erschließung religionspädagogischer Bildungsressourcen.

```
reliedu-vocab/
├── index.ttl                    # 🎯 HAUPTDATEI für SkoHub (vollständig, monolithisch)
├── didactics.ttl                # 13 religionsdidaktische Labels (optional/modular)
├── resourcetype.ttl             # 7 spezifische Ressourcentypen (optional/modular)
├── competency.ttl               # 5 prozessbezogene Kompetenzen (optional/modular)
├── content.ttl                  # 6 Inhaltsbereiche (optional/modular)
├── method.ttl                   # 4 Unterrichtsmethoden (optional/modular)
└── location.ttl                 # 8 Lernorte (optional/modular)
```

## 📚 Struktur

**`index.ttl`** ist die **Hauptdatei** mit dem vollständigen Vokabular in einem ConceptScheme. Sie wird von SkoHub für die Publikation verwendet.

Die **modularen Dateien** (didactics.ttl, resourcetype.ttl, etc.) sind **eigenständige ConceptSchemes** für flexible Nutzung in anderen Kontexten. Sie enthalten dieselben Konzepte wie index.ttl, aber aufgeteilt nach Themenbereich.

### Warum zwei Versionen?

- **SkoHub** benötigt ein vollständiges, monolithisches ConceptScheme pro Datei → `index.ttl`
- **Modulare Nutzung** ermöglicht separate Updates und flexible Integration → einzelne .ttl Dateien

## 📊 Vokabular-Übersicht

Das Vokabular umfasst **6 Themenbereiche** mit insgesamt **47 Konzepten**:

| Bereich | Datei | Beschreibung | Konzepte |
|---------|-------|--------------|----------|
| **Didaktische Zugänge** | `didactics.ttl` | 13 religionsdidaktische Labels | 17 |
| **Ressourcentypen** | `resourcetype.ttl` | Spezifische Materialtypen | 7 |
| **Kompetenzen** | `competency.ttl` | Prozessbezogene Kompetenzen (KMK) | 5 |
| **Inhaltsbereiche** | `content.ttl` | Themenfelder des RU | 6 |
| **Unterrichtsmethoden** | `method.ttl` | Religionspädagogische Methoden | 4 |
| **Lernorte** | `location.ttl` | Außerschulische Lernorte | 8 |

Alle Konzepte sind in der **`index.ttl`** zusammengefasst.

## 🎯 Verwendung

### AMB-Metadaten

Beispiel für die Verwendung in AMB-konformen Metadaten:

```json
{
  "@context": "https://w3id.org/kim/amb/context.jsonld",
  "id": "https://example.org/resource/123",
  "type": ["LearningResource"],
  "name": "Gleichnisse Jesu verstehen",
  "about": [
    {
      "id": "http://w3id.org/openeduhub/vocabs/discipline/520"
    },
    {
      "id": "https://w3id.org/reliedu/didactics/korrelation",
      "prefLabel": {"de": "Korrelationsdidaktik"}
    },
    {
      "id": "https://w3id.org/reliedu/didactics/biblisch",
      "prefLabel": {"de": "Biblische Didaktik"}
    }
  ],
  "teaches": [
    {
      "id": "https://w3id.org/reliedu/competency/deutung",
      "prefLabel": {"de": "Deutungskompetenz"}
    },
    {
      "id": "https://w3id.org/reliedu/content/jesus-christus",
      "prefLabel": {"de": "Jesus Christus"}
    }
  ],
  "learningResourceType": [
    {
      "id": "http://w3id.org/openeduhub/vocabs/new_lrt/36e68792-3a99-4c1d-b1c9-9212d67026ee"
    },
    {
      "id": "https://w3id.org/reliedu/resourcetype/bibeltext",
      "prefLabel": {"de": "Bibeltext"}
    }
  ]
}
```

## 🏗️ Architektur

### Monolithische Hauptdatei (index.ttl)

Die `index.ttl` enthält das **gesamte Vokabular** in einem einzigen ConceptScheme. Dies ist notwendig für:
- ✅ **SkoHub-Publikation** (erfordert vollständige ConceptSchemes)
- ✅ **Einfache Integration** (eine Datei enthält alles)
- ✅ **SKOS-Validierung** (alle Beziehungen sind auflösbar)

### Modulare Einzeldateien

Die modularen Dateien bieten:
- 📦 **Thematische Trennung** (leichtere Navigation)
- 🔄 **Flexible Updates** (einzelne Bereiche aktualisieren)
- 🎯 **Selektive Nutzung** (nur benötigte Teile einbinden)

**Empfehlung:** Für die meisten Anwendungsfälle ist die `index.ttl` ausreichend.

### SKOS Mappings

Alle Konzepte nutzen SKOS Mapping Properties zur Integration mit Standards:
- **`exactMatch`**: Identische Bedeutung (z.B. mit OpenEduHub)
- **`broadMatch`**: Übergeordneter Begriff 
- **`relatedMatch`**: Verwandtes Konzept
- **`related`**: Interne Verknüpfungen

## 📖 Standards-Konformität

- ✅ **AMB** (Allgemeines Metadatenprofil für Bildungsressourcen)
- ✅ **SKOS** (Simple Knowledge Organization System)
- ✅ **OpenEduHub Vocabularies** (28 Vokabulare)
- ✅ **KIM educationalLevel + HCRT**
- ✅ **KMK-Bildungsstandards** für Religionsunterricht

## 🚀 Publikation mit SkoHub

Every time a change is made to a vocabulary a GitHub-workflow-action is triggered to publish the most recent vocabulary to the `gh-pages`-branch, which is used by GitHub pages.
It spins up a Docker container made from [SkoHub Vocabs](https://github.com/hbz/skohub-vocabs).

## 📝 Lizenz & Autor

- **Lizenz**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **Autor**: Jörg Lohrer
- **Publisher**: Religionspädagogisches Institut
- **Version**: 0.3
- **Letzte Änderung**: 2025-10-14

## 🤝 Beitragen

Issues und Pull Requests sind willkommen! Bitte beachte:
- Jedes Vokabular sollte ein eigenständiges ConceptScheme bleiben
- SKOS-Best-Practices befolgen
- AMB-Konformität sicherstellen

---

## Setup für eigene Nutzung

If you want to reuse this repo and have your vocabulary automatically pushed und published via GitHub-Pages, follow these steps:

1. Fork this repo. **Uncheck the box to only fork the main branch**.
1. Go to "Actions" tab and if not already activated, activate GitHub Actions.
1. Go to "Settings", navigate to the "Pages" setting and select `gh-pages` as the branch your site is being built from. 
1. Go back to the main page of your repo and click the little gear icon in the top right of the "About" section. Check the box at "Use your GitHub Pages website".
1. Add a commit to the main branch and your vocabulary will be automatically published (sometimes it takes a little to see the changes, remember to do some hard refreshing).

Any issues? Please open up a issue [here](https://github.com/skohub-io/skohub-pages/issues)

## Custom Domain

If you want to host your vocabularies under your GitHub pages domain (so no W3 perma-id or purl.org redirect), you have to provide that domain in the [`config.yaml`](./config.yaml).

Example:

Your GitHub Pages domain is: `https://skohub-io.github.io/skohub-pages/`
Then provide `https://skohub-io.github.io/skohub-pages/` as `custom_domain` in your `config.yaml`.

The base of your concept scheme could then be something like: `https://skohub-io.github.io/skohub-pages/colours/`

Notice that this will apply to all your hosted vocabularies.

## Troubleshooting

### There is no `gh-pages` branch to select for GitHub Pages

You probably only forked the main branch.
You have two options:

- Delete the repo and fork it again, but make sure to uncheck the box to only fork the main branch
- Make sure the GitHub Action is activated ➡️ Go to "Actions" tab and activate it. After that commit changes to a vocabulary in the main branch. This should trigger the build and create a `gh-pages` branch.

### I push changes, but they seem to have no effect. My vocabulary stays the same

Maybe your GitHub Action is not activated yet.
Go to the "Actions" tab and activate GitHub Actions for your repository.

### During the build I get an error saying `The requested URL returned error: 403`

You maybe need to update permissions like described here: https://github.com/peaceiris/actions-gh-pages/issues/744
Go to `Settings` > `Actions` > `General` > `Workflow permissions` and toggle the Read and write permissions.

## CHANGELOG

09.02.2021:

- In an earlier version, there was the .env variable `PATH_PREFIX` set to point to the repository the vocabulary is hosted at. To align with rest of code, this was changed to `BASEURL`.
- The docker image now also support i18n

