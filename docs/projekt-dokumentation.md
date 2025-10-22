# Erstellung eines modularen, AMB-konformen SKOS-Vokabulars für religionspädagogische Bildungsressourcen mit w3id-Permalink und SkoHub-Publikation.

## Übersicht

**w3id-Antrag genehmigt**: 21. Oktober 2025  
**Permalink**: https://w3id.org/reliedu → https://rpi-virtuell.github.io/reliedu-vocab/

---

## Aufgabenstellung

### 1. Anforderungen

- **Modulares SKOS-Vokabular** für religionspädagogische Materialien erstellen
- **AMB-Konformität** sicherstellen (Allgemeines Metadatenprofil für Bildungsressourcen)
- **Integration mit bestehenden Standards**:
  - OpenEduHub Vokabulare (28 Vokabulare)
  - KIM educationalLevel + HCRT
  - SKOS (Simple Knowledge Organization System)
- **w3id.org Permalink** beantragen und einrichten
- **SkoHub-Publikation** über GitHub Pages automatisieren

### 2. Fachliche Anforderungen - MÜSSEN NOCH ÜBERARBEITET WERDEN (zum Test KI-generiert)

Abdeckung der religionspädagogischen Kernbereiche:
- Religionsdidaktische Ansätze und Labels
- Religionsspezifische Ressourcentypen
- Religionspädagogische Kompetenzen
- Theologische Inhaltsbereiche
- Religionsspezifische Lehr-/Lernmethoden
- Religionsspezifische Bildungskontexte (Erweiterung von OpenEduHub educationalContext)

---

## Umsetzung

### Phase 1: Konzeption und Strukturierung in ConceptSchemes

**Entscheidung für modulare Architektur:**
- Statt einer monolithischen Datei → 6 (bzw. noch mehr) eigenständige ConceptSchemes
- Jedes ConceptScheme mit eigenem Namespace und URI
- Keine zentrale "Hauptdatei" nötig - rein modularer Aufbau

**Vorteile der modularen Struktur:**
- ✅ Maximale Flexibilität - jedes Vokabular unabhängig nutzbar
- ✅ Einfache Wartung - Updates nur in spezifischen Bereichen
- ✅ Klare Separation - jeder Bereich hat eigenen Namespace
- ✅ Bessere Performance - kleinere, fokussierte Dateien
- ✅ Team-freundlich - parallele Arbeit an verschiedenen Bereichen

### Phase 2: Erstellung der ConceptSchemes
- [X] KI-basierte ConceptSchemes mit Fantasienamen blanko erstellen
- [ ] Alle ConceptSchemes überarbeiten

**AMB-Verwendung**: `educationalContext` (ERWEITERT OpenEduHub educationalContext)

**Besonderheit**:  Integration mit OpenEduHub durch `skos:broadMatch`-Mappings zu bestehenden Bildungsstufen.

### Phase 3: w3id.org Permalink-Antrag

**Beantragter Permalink**: `https://w3id.org/reliedu`  
**Ziel-URL**: `https://rpi-virtuell.github.io/reliedu-vocab/`

**Pull Request an w3id.org Repository**:
- [X] Antrag auf neuen Permalink für religionspädagogisches Vokabular
- [ ] Redirect-Konfiguration für alle ConceptSchemes
- [X] Content Negotiation für verschiedene RDF-Formate

**Status**: ✅ Genehmigt (Oktober 2025)


### Phase 4: SkoHub-Publikation

**Repository**: https://github.com/rpi-virtuell/reliedu-vocab  
**GitHub Pages**: https://rpi-virtuell.github.io/reliedu-vocab/

**Automatisierung**:
- GitHub Actions Workflow für automatische Publikation
- Docker-Container mit SkoHub Vocabs
- Automatisches Deployment bei jedem Push auf `main`


---

## Technische Details

### (Vorläufige) Repository-Struktur

```
reliedu-vocab/
├── didactics.ttl          # 13 religionsdidaktische Labels
├── resourcetype.ttl       # 7 religionsspezifische Ressourcentypen
├── competency.ttl         # 6 religionspädagogische Kompetenzen
├── content.ttl            # 8 theologische Inhaltsbereiche
├── method.ttl             # 8 religionsspezifische Methoden
├── location.ttl           # 8 religionsspezifische Bildungskontexte
├── config.yaml            # SkoHub-Konfiguration
├── README.md              # Projektdokumentation
└── .github/
    └── workflows/
        └── main.yml       # GitHub Actions für automatische Publikation
```

### SKOS-Metadaten

Jedes ConceptScheme enthält:
- `dct:title` (de/en)
- `dct:description` (de/en) mit ausführlicher Dokumentation
- `dct:creator` "Jörg Lohrer"
- `dct:created` / `dct:modified` (Datumsangaben)
- `dct:license` CC BY-SA 4.0
- `dct:publisher` "Religionspädagogisches Institut"
- `schema:version` Versionsnummer
- `vann:preferredNamespacePrefix` und `vann:preferredNamespaceUri`
- `skos:hasTopConcept` mit allen Top-Level-Konzepten

### AMB-Nutzungsbeispiel


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

---

## Ergebnisse

### Quantitative Erfolge

- ✅ **6 ConceptSchemes** erfolgreich erstellt
- ✅ **50 Konzepte** insgesamt definiert
  - 13 religionsdidaktische Labels
  - 7 Ressourcentypen
  - 6 Kompetenzen
  - 8 Inhaltsbereiche
  - 8 Methoden
  - 8 Lernorte
- ✅ **w3id.org Permalink** erfolgreich beantragt und genehmigt
- ✅ **SkoHub-Publikation** automatisiert und funktionsfähig

### Qualitative Erfolge

1. **Modulare Architektur**
   - Keine zentrale Hauptdatei nötig
   - Jedes ConceptScheme eigenständig nutzbar
   - Einfache Wartung und Erweiterung

2. **OpenEduHub-Integration**
   - Erweiterung des educationalContext-Vokabulars
   - SKOS-Mappings mit `broadMatch` zu bestehenden Bildungsstufen
   - Neue Kontexte: Konfirmandenarbeit, Firmvorbereitung

3. **AMB-Konformität**
   - Vollständig kompatibel mit Allgemeinem Metadatenprofil
   - Integration mit OpenEduHub, KIM und SKOS-Standards
   - Produktionsreife Metadatenauszeichnung

4. **Nachhaltige Infrastruktur**
   - Stabiler w3id-Permalink
   - Automatisierte Publikation via GitHub Actions
   - Open Source unter CC BY-SA 4.0 Lizenz

---

## Lessons Learned

### Technische Erkenntnisse

1. **Modulare Struktur ist überlegen**: Die Entscheidung gegen eine monolithische Datei und für eigenständige ConceptSchemes hat sich bewährt.

2. **SkoHub verarbeitet automatisch**: Keine Index-Datei nötig - SkoHub findet und verarbeitet alle .ttl-Dateien automatisch.

3. **SKOS-Mappings sind essentiell**: Die `broadMatch`-Mappings zu OpenEduHub ermöglichen perfekte Integration.

4. **w3id.org ist unkompliziert**: Der Antragsprozess für Permalinks ist gut dokumentiert und funktioniert zuverlässig.

### Fachliche Erkenntnisse

1. **Religionspädagogik braucht eigene Kontexte**: Standard-Bildungsstufen decken Konfirmandenarbeit/Firmvorbereitung nicht ab.

2. **13 didaktische Labels sind noch nicht ausreichend**: Die erfundenen religionsdidaktischen Ansätze sind noch zu überprüfen.

3. **AMB-Konformität ermöglicht Interoperabilität**: Integration mit allgemeinen Bildungsressourcen-Repositorien wird möglich.

---

## Ausblick

### Kurzfristig

- [ ] Nutzerfeedback einholen
- [ ] Dokumentation erweitern
- [ ] Beispiel-Metadaten für verschiedene Materialtypen erstellen

### Mittelfristig

- [ ] Weitere religionspädagogische Konzepte ergänzen
- [ ] Multilingual erweitern (aktuell: de/en)
- [ ] Mappings zu weiteren Vokabularen hinzufügen

### Langfristig

- [ ] Community-Prozess für Erweiterungen etablieren
- [ ] Integration in religionspädagogische Material-Repositorien
- [ ] Übernahme in offizielle AMB-Erweiterungen prüfen

---

## Referenzen

- **Repository**: https://github.com/rpi-virtuell/reliedu-vocab
- **w3id-Permalink**: https://w3id.org/reliedu
- **SkoHub-Publikation**: https://rpi-virtuell.github.io/reliedu-vocab/
- **AMB-Spezifikation**: https://w3id.org/kim/amb/
- **OpenEduHub Vokabulare**: https://vocabs.openeduhub.de/
- **SKOS-Standard**: https://www.w3.org/2004/02/skos/

---

## Autor & Lizenz

**Autor**: Jörg Lohrer, Comenius-Institut  
**Lizenz**: CC BY-SA 4.0  
**Version**: 1.0  
**Datum**: 14. Oktober 2025
