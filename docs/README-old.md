# Religionspädagogisches Vokabular (Modulare Architektur)

Kontrolliertes Vokabular für religionspädagogische Bildungsressourcen mit modularer SKOS-Struktur.

## 🎯 Überblick

Dieses Vokabular erweitert die offiziellen Standards (AMB, OpenEduHub, KIM) um religionsdidaktische Spezifika und ermöglicht präzise Metadatenauszeichnung für religionspädagogische Materialien.

### Modulare Struktur

Das Vokabular ist in 6 separate ConceptSchemes aufgeteilt:

| Datei | Beschreibung | AMB-Verwendung |
|-------|-------------|----------------|
| **didactics.ttl** | 13 religionsdidaktische Labels | `about` (zusätzlich zu discipline/520) |
| **resourcetype.ttl** | 7 religionsspezifische Ressourcentypen | `learningResourceType` (erweitert new_lrt) |
| **competency.ttl** | 6 religionspädagogische Kompetenzbereiche | `teaches` (erweitert hcrt) |
| **content.ttl** | 8 theologische Inhaltsbereiche | `about` (erweitert discipline) |
| **method.ttl** | 8 religionsspezifische Methoden | `typicalLearningTime`, `conditionsOfAccess` |
| **location.ttl** | 8 religionsspezifische Bildungskontexte | `educationalContext` (erweitert OpenEduHub) |

## 🎯 Erweiterte OpenEduHub Integration

Die `location.ttl` erweitert das OpenEduHub educationalContext-Vokabular um religionsspezifische Bildungskontexte:

### Bestehende OpenEduHub-Werte
- `grundschule`
- `sekundarstufe_1`
- `sekundarstufe_2`
- `erwachsenenbildung`
- `hochschule`

### Neue religionsspezifische Erweiterungen
- `reliedu-location:konfirmandenarbeit` ↔ `sekundarstufe_1`
- `reliedu-location:firmvorbereitung` ↔ `sekundarstufe_1` 
- `reliedu-location:erwachsenenbildung_gemeinde` ↔ `erwachsenenbildung`
- `reliedu-location:gottesdienst`
- `reliedu-location:seelsorge`
- `reliedu-location:pilgerweg`
- `reliedu-location:kloster`
- `reliedu-location:bibelkreis` ↔ `erwachsenenbildung`

## 🔗 Standards & Compliance

- **AMB** (Allgemeines Metadatenprofil für Bildungsressourcen) v20231019
- **OpenEduHub** Vokabulare (28 Vokabulare) - erweitert um religionsspezifische Kontexte
- **KIM** educationalLevel + HCRT
- **SKOS** (Simple Knowledge Organization System)

## 📋 AMB-Nutzungsbeispiel

```json
{
  "@context": "https://w3id.org/kim/amb/context.jsonld",
  "name": "Gleichnisse verstehen - Vom verlorenen Schaf",
  "description": "Interaktive Lerneinheit zur Deutung biblischer Gleichnisse",
  "about": [
    "http://w3id.org/openeduhub/vocabs/discipline/520",
    "https://w3id.org/reliedu/didactics/subjektorientierung",
    "https://w3id.org/reliedu/content/bibeldidaktik"
  ],
  "learningResourceType": [
    "http://w3id.org/openeduhub/vocabs/new_lrt/d8c3ef03-2e34-4331-a375-a1bb5827ed7d",
    "https://w3id.org/reliedu/resourcetype/glaubenskurs"
  ],
  "educationalContext": [
    "http://w3id.org/openeduhub/vocabs/educationalContext/sekundarstufe_1",
    "https://w3id.org/reliedu/location/konfirmandenarbeit"
  ],
  "teaches": [
    "https://w3id.org/kim/hcrt/e2c4de45-d326-4e1b-a8c1-b8d5f1234567",
    "https://w3id.org/reliedu/competency/hermeneutische_kompetenz"
  ]
}
```

## 📝 Verfügbare Konzepte

### Religionsdidaktische Labels (didactics.ttl)
1. Subjektorientierung
2. Korrelationsdidaktik  
3. Elementarisierung
4. Symboldidaktik
5. Bibliodrama
6. Performative Religionsdidaktik
7. Konfigurative Religionsdidaktik
8. Mystagogische Didaktik
9. Interkulturelle Religionsdidaktik
10. Gendersensible Religionsdidaktik
11. Inklusive Religionsdidaktik
12. Mediale Religionsdidaktik
13. Digitale Religionsdidaktik

### Religionsspezifische Ressourcentypen (resourcetype.ttl)
1. Gottesdienstbaustein
2. Andacht
3. Liturgisches Material
4. Glaubenskurs
5. Exerzitium
6. Seelsorgehilfe
7. Gemeindepraxis

### Religionpädagogische Kompetenzen (competency.ttl)
1. Religiöse Sprachfähigkeit
2. Hermeneutische Kompetenz
3. Existentielle Kompetenz
4. Ethische Urteilsfähigkeit
5. Dialogfähigkeit
6. Spirituelle Kompetenz

### Religionspädagogische Inhaltsbereiche (content.ttl)
1. Gotteslehre
2. Christologie
3. Theologische Anthropologie
4. Religiöse Ethik
5. Ekklesiologie
6. Eschatologie
7. Weltreligionen und Konfessionen
8. Bibeldidaktik

### Religionspädagogische Methoden (method.ttl)
1. Meditation
2. Gebet als Methode
3. Bibliolog
4. Kirchenpädagogik
5. Stilleübung
6. Religiöses Rollenspiel
7. Religiöse Kunstpädagogik
8. Religiöse Musikpädagogik

### Religionsspezifische Lernorte (location.ttl)
1. Konfirmandenarbeit
2. Firmvorbereitung
3. Erwachsenenbildung in der Gemeinde
4. Gottesdienst als Lernort
5. Seelsorge
6. Pilgerweg
7. Kloster als Lernort
8. Bibelkreis

## 📁 Dateien

- **reliedu.ttl** - Hauptvokabular mit Verweisen auf Subvokabulare
- **index.ttl** - Übersichtsindex für SkoHub
- **didactics.ttl** - Religionsdidaktische Ansätze
- **resourcetype.ttl** - Religionsspezifische Ressourcentypen
- **competency.ttl** - Religionpädagogische Kompetenzen
- **content.ttl** - Theologische Inhaltsbereiche
- **method.ttl** - Religionsspezifische Methoden
- **location.ttl** - Religionsspezifische Bildungskontexte
- **config.yaml** - SkoHub-Konfiguration

## 🚀 Nutzung

Die modulare Struktur ermöglicht:
- **Flexible Integration**: Einzelne ConceptSchemes können unabhängig verwendet werden
- **Einfache Wartung**: Updates betreffen nur spezifische Teilbereiche
- **AMB-Konformität**: Vollständig kompatibel mit dem Allgemeinen Metadatenprofil
- **OpenEduHub-Erweiterung**: Nahtlose Integration mit bestehenden Vokabularen

## 🚀 SkoHub-Publikation

Every time a change is made to a vocabulary a GitHub-workflow-action is triggered to publish the most recent vocabulary to the `gh-pages`-branch, which is used by GitHub pages.
It spins up a Docker container made from [SkoHub Vocabs](https://github.com/hbz/skohub-vocabs).

## 📄 Lizenz

CC BY-SA 4.0 - Jörg Lohrer, Religionspädagogisches Institut