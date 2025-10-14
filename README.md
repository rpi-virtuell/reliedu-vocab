# Religionspädagogisches Vokabular (Rein Modulare Architektur)

Sechs eigenständige SKOS-ConceptSchemes für religionspädagogische Bildungsressourcen - **keine Hauptdatei nötig!**

## 🎯 Modulare ConceptSchemes

Jede TTL-Datei ist ein **vollständiges, eigenständiges ConceptScheme** mit eigenem Namespace:

| Datei | ConceptScheme URI | Beschreibung | AMB-Verwendung |
|-------|------------------|-------------|----------------|
| **didactics.ttl** | `https://w3id.org/reliedu/didactics/` | 13 religionsdidaktische Labels | `about` (zusätzlich zu discipline/520) |
| **resourcetype.ttl** | `https://w3id.org/reliedu/resourcetype/` | 7 religionsspezifische Ressourcentypen | `learningResourceType` (erweitert new_lrt) |
| **competency.ttl** | `https://w3id.org/reliedu/competency/` | 6 religionpädagogische Kompetenzbereiche | `teaches` (erweitert hcrt) |
| **content.ttl** | `https://w3id.org/reliedu/content/` | 8 theologische Inhaltsbereiche | `about` (erweitert discipline) |
| **method.ttl** | `https://w3id.org/reliedu/method/` | 8 religionsspezifische Methoden | `typicalLearningTime`, `conditionsOfAccess` |
| **location.ttl** | `https://w3id.org/reliedu/location/` | 8 religionsspezifische Bildungskontexte | `educationalContext` (erweitert OpenEduHub) |

## 🎯 OpenEduHub educationalContext Erweiterung

Die `location.ttl` erweitert das [OpenEduHub educationalContext](https://vocabs.openeduhub.de/w3id.org/openeduhub/vocabs/educationalContext/index.json) um religionsspezifische Bildungskontexte:

### Bestehende OpenEduHub-Werte
- `grundschule`, `sekundarstufe_1`, `sekundarstufe_2`, `erwachsenenbildung`, `hochschule`

### Neue religionsspezifische Erweiterungen
- `reliedu-location:konfirmandenarbeit` ↔ `sekundarstufe_1`
- `reliedu-location:firmvorbereitung` ↔ `sekundarstufe_1` 
- `reliedu-location:erwachsenenbildung_gemeinde` ↔ `erwachsenenbildung`
- `reliedu-location:gottesdienst`, `reliedu-location:seelsorge`, `reliedu-location:pilgerweg`
- `reliedu-location:kloster`, `reliedu-location:bibelkreis` ↔ `erwachsenenbildung`

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

### 🎓 Religionsdidaktische Labels (didactics.ttl)
1. **Subjektorientierung** - Fokus auf Lebenswelten der Lernenden
2. **Korrelationsdidaktik** - Verknüpfung von Erfahrung und Tradition
3. **Elementarisierung** - Reduktion auf elementare Strukturen
4. **Symboldidaktik** - Symbole als Brücke zur Transzendenz
5. **Bibliodrama** - Erfahrungsorientierte Bibelauslegung
6. **Performative Religionsdidaktik** - Verkörpertes religiöses Lernen
7. **Konfigurative Religionsdidaktik** - Ästhetische Darstellung
8. **Mystagogische Didaktik** - Einführung in religiöse Geheimnisse
9. **Interkulturelle Religionsdidaktik** - Lernen zwischen Traditionen
10. **Gendersensible Religionsdidaktik** - Geschlechterreflexion
11. **Inklusive Religionsdidaktik** - Gemeinsames Lernen trotz Unterschieden
12. **Mediale Religionsdidaktik** - Integration verschiedener Medien
13. **Digitale Religionsdidaktik** - Online-Lernumgebungen

### 📚 Religionsspezifische Ressourcentypen (resourcetype.ttl)
1. **Gottesdienstbaustein** - Teilkomponente liturgischer Feiern
2. **Andacht** - Kurze religiöse Feier
3. **Liturgisches Material** - Sakramente und kirchliche Handlungen
4. **Glaubenskurs** - Strukturierte Glaubensvermittlung
5. **Exerzitium** - Anleitung für geistliche Übungen
6. **Seelsorgehilfe** - Unterstützung für pastorale Gespräche
7. **Gemeindepraxis** - Anleitung für Gemeindearbeit

### 🧠 Religionspädagogische Kompetenzen (competency.ttl)
1. **Religiöse Sprachfähigkeit** - Angemessene Verwendung religiöser Sprache
2. **Hermeneutische Kompetenz** - Sachgemäße Textinterpretation
3. **Existentielle Kompetenz** - Reflexion der eigenen Lebenserfahrungen
4. **Ethische Urteilsfähigkeit** - Begründete ethische Bewertung
5. **Dialogfähigkeit** - Respektvoller Austausch über Weltanschauungen
6. **Spirituelle Kompetenz** - Gestaltung spiritueller Erfahrungen

### 📖 Religionspädagogische Inhaltsbereiche (content.ttl)
1. **Gotteslehre** - Reflexion über Gott und Gotteserfahrungen
2. **Christologie** - Lehre von Person und Werk Jesu Christi
3. **Theologische Anthropologie** - Lehre vom Menschen aus theologischer Sicht
4. **Religiöse Ethik** - Moraltheologische Reflexion
5. **Ekklesiologie** - Lehre von der Kirche
6. **Eschatologie** - Lehre von den letzten Dingen
7. **Weltreligionen und Konfessionen** - Vergleichende Religionswissenschaft
8. **Bibeldidaktik** - Didaktische Erschließung biblischer Texte

### 🎭 Religionspädagogische Methoden (method.ttl)
1. **Meditation** - Spirituelle Sammlung als Lernmethode
2. **Gebet als Methode** - Gebetsformen im Lernprozess
3. **Bibliolog** - Interaktive Bibelauslegung durch Rolleneinfühlung
4. **Kirchenpädagogik** - Ganzheitliche Erschließung des Kirchenraums
5. **Stilleübung** - Einübung in Achtsamkeit und Kontemplation
6. **Religiöses Rollenspiel** - Szenische Darstellung religiöser Inhalte
7. **Religiöse Kunstpädagogik** - Künstlerisch-kreative Gestaltung
8. **Religiöse Musikpädagogik** - Religiöse Bildung durch Musik

### 🏛️ Religionsspezifische Lernorte (location.ttl)
1. **Konfirmandenarbeit** - Evangelische Jugendarbeit (13-15 Jahre)
2. **Firmvorbereitung** - Katholische Jugendarbeit (14-16 Jahre)
3. **Erwachsenenbildung in der Gemeinde** - Religiöse Bildung für Erwachsene
4. **Gottesdienst als Lernort** - Liturgische Feier als Bildungskontext
5. **Seelsorge** - Geistliche Begleitung und Beratung
6. **Pilgerweg** - Spirituelle Wanderung als religiöse Bildung
7. **Kloster als Lernort** - Monastische Gemeinschaft als Bildungsort
8. **Bibelkreis** - Gruppenbezogene Bibelarbeit

## 🚀 Vorteile der modularen Architektur

- ✅ **Maximale Flexibilität** - Jedes ConceptScheme unabhängig nutzbar
- ✅ **Einfache Wartung** - Updates nur in spezifischen Bereichen
- ✅ **Klare Separation** - Jeder Bereich hat eigenen Namespace
- ✅ **Bessere Performance** - Kleinere, fokussierte Dateien
- ✅ **Team-freundlich** - Parallelarbeit an verschiedenen Bereichen möglich
- ✅ **AMB-konform** - Vollständig kompatibel mit Metadatenprofil
- ✅ **SkoHub-ready** - Automatische Verarbeitung aller .ttl-Dateien

## 🚀 SkoHub-Publikation

SkoHub verarbeitet automatisch alle TTL-Dateien im Repository und erstellt für jedes ConceptScheme eine eigene Navigationsseite:

- `https://domain.de/didactics/` - Religionsdidaktische Labels
- `https://domain.de/resourcetype/` - Religionsspezifische Ressourcentypen
- `https://domain.de/competency/` - Religionspädagogische Kompetenzen
- `https://domain.de/content/` - Religionspädagogische Inhaltsbereiche
- `https://domain.de/method/` - Religionspädagogische Methoden
- `https://domain.de/location/` - Religionsspezifische Lernorte

Jeder GitHub-Push triggert automatisch die Publikation über GitHub Actions.

## 📄 Lizenz & Autor

- **Lizenz**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **Autor**: Jörg Lohrer, Religionspädagogisches Institut
- **Version**: 1.0 (Modulare Architektur)
- **Erstellt**: 14. Oktober 2025