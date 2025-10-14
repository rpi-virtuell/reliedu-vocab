# Religionspädagogisches Vokabular (ReLiEdu Vocabulary)

Kontrolliertes SKOS-Vokabular für die AMB-konforme Erschließung religionspädagogischer Bildungsressourcen.

## 📁 Repository-Struktur

Dieses Repository hat **zwei Branches**:

- **`main`** - Stabiler Branch mit der ursprünglichen `reliedu.ttl` (funktioniert mit SkoHub)
- **`weiterentwicklung`** - Experimenteller Branch mit modularer Struktur (6 separate .ttl Dateien)

## 🎯 Aktueller Zustand (main)

Der `main` Branch enthält:
- `reliedu.ttl` - Vollständiges religionspädagogisches Vokabular (funktionsfähig)
- `colors.ttl` & `colors_with_hierarchy.ttl` - Beispiel-Vokabulare
- SkoHub-kompatible Struktur

## 🚀 SkoHub-Publikation

## 🚀 SkoHub-Publikation

Every time a change is made to a vocabulary a GitHub-workflow-action is triggered to publish the most recent vocabulary to the `gh-pages`-branch, which is used by GitHub pages.
It spins up a Docker container made from [SkoHub Vocabs](https://github.com/hbz/skohub-vocabs).

## 💡 Vokabular-Details

Das **Religionspädagogische Vokabular** umfasst:

- **13 religionsdidaktische Labels** (Subjektorientierung, Korrelation, etc.)
- **5 prozessbezogene Kompetenzen** (nach KMK-Standards)
- **6 Inhaltsbereiche** (Gott, Jesus Christus, Bibel, etc.)
- **Religionspädagogische Ressourcentypen** (Bibeltext, Glaubenszeugnis, etc.)
- **Unterrichtsmethoden** (Bibelgespräch, Bibliolog, etc.)
- **Religiöse Lernorte** (Kirchenraum, Friedhof, etc.)

**Standards-konform:** AMB, OpenEduHub, KIM, SKOS

## 🔧 Setup für eigene Nutzung

If you want to reuse this repo and have your vocabulary automatically pushed und published via GitHub-Pages, follow these steps:

1. Fork this repo. **Uncheck the box to only fork the main branch**.
1. Go to "Actions" tab and if not already activated, activate GitHub Actions.
1. Go to "Settings", navigate to the "Pages" setting and select `gh-pages` as the branch your site is being built from. 
1. Go back to the main page of your repo and click the little gear icon in the top right of the "About" section. Check the box at "Use your GitHub Pages website".
1. Add a commit to the main branch and your vocabulary will be automatically published (sometimes it takes a little to see the changes, remember to do some hard refreshing).

Any issues? Please open up a issue [here](https://github.com/skohub-io/skohub-pages/issues)

## 📄 Lizenz & Autor

- **Lizenz**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **Autor**: Jörg Lohrer
- **Version**: 0.2
- **Namespace**: `https://w3id.org/reliedu/`

## 🌿 Branch-Übersicht

- **`main`** - Stabile Version mit `reliedu.ttl` (empfohlen)
- **`weiterentwicklung`** - Experimentelle modulare Struktur

---

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

