# w3id.org Integration Documentation

## Overview

The Religious Education Vocabulary (reliedu) is integrated with w3id.org to provide persistent, stable URIs for the vocabulary and all its concepts. This document describes the integration setup and how the redirect system works.

## Persistent URI Structure

All reliedu URIs follow the pattern:
```
https://w3id.org/reliedu/{path}
```

These URIs are **permanent** and will redirect to the actual vocabulary hosted on GitHub Pages.

### Examples:
- `https://w3id.org/reliedu/` → Main vocabulary
- `https://w3id.org/reliedu/didactics/korrelation` → Specific concept
- `https://w3id.org/reliedu/competency/wahrnehmung` → Competency concept
- `https://w3id.org/reliedu/content/bibel` → Content area

## Technical Implementation

### Repository Structure

The w3id.org integration consists of two minimal files in the `reliedu/` directory:

```
w3id.org/reliedu/
├── .htaccess      (6 lines - redirect configuration)
└── README.md      (13 lines - basic information)
```

### .htaccess Configuration

The `.htaccess` file is intentionally minimal, following w3id.org best practices:

```apache
# Religious Education Vocabulary (reliedu)
# Maintainer: Jörg Lohrer (@joerglohrer)
# Documentation: https://github.com/rpi-virtuell/reliedu-vocab

RewriteEngine on
RewriteRule ^(.*)$ https://rpi-virtuell.github.io/reliedu-vocab/$1 [R=302,L]
```

**Key Design Decisions:**

1. **Single Redirect Rule**: All requests are forwarded to GitHub Pages
2. **No AddType Directives**: Not needed for redirect services
3. **No RewriteBase**: Not required for simple redirects
4. **No Explicit Concept Rules**: SkoHub handles content negotiation
5. **R=302 Redirect**: Temporary redirect (can be changed to 303 for semantic web best practice)

### Content Negotiation

Content negotiation is handled automatically by **SkoHub Vocabs** on GitHub Pages:

| Accept Header | Response Format | File Extension |
|--------------|-----------------|----------------|
| `text/html` | HTML documentation | `.html` |
| `text/turtle` | Turtle RDF | `.ttl` |
| `application/ld+json` | JSON-LD | `.jsonld` |
| `application/rdf+xml` | RDF/XML | `.rdf` |

**Example Request Flow:**

1. Client requests: `https://w3id.org/reliedu/didactics/korrelation`
2. w3id.org redirects to: `https://rpi-virtuell.github.io/reliedu-vocab/didactics/korrelation`
3. SkoHub serves appropriate format based on Accept header:
   - Browser → `didactics/korrelation.html`
   - RDF client → `didactics/korrelation.ttl` or `.jsonld` or `.rdf`

## Pull Request Process

### Timeline

- **Initial PR**: [#5381](https://github.com/perma-id/w3id.org/pull/5381)
- **Reviewer**: @davidlehn (w3id.org maintainer)
- **Status**: Revised based on feedback

### Reviewer Feedback & Resolution

#### Issue 1: AddType Directives
**Feedback:** "These are used for local files, and not needed in a redirect service like this."

**Resolution:** ✅ Removed all `AddType` directives

#### Issue 2: RewriteBase
**Feedback:** "This won't be used for redirects."

**Resolution:** ✅ Removed `RewriteBase` directive

#### Issue 3: Catch-all Rule Order
**Feedback:** "Rules are processed in order. I think this will catch everything before the rules below."

**Resolution:** ✅ Removed all explicit concept rules, simplified to single catch-all redirect

#### Issue 4: Verbose README
**Feedback:** "This readme is too verbose. Please host your documentation on your own site."

**Resolution:** ✅ Reduced README from 268 to 13 lines, moved all docs to external repo

#### Issue 5: GitHub Username
**Feedback:** "Please add your github username to the maintainer line."

**Resolution:** ✅ Added @joerglohrer to both `.htaccess` and README

### Final Simplification

**Before:**
- `.htaccess`: 133 lines with explicit rules for every concept
- `README.md`: 268 lines with full documentation

**After:**
- `.htaccess`: 6 lines with single redirect rule
- `README.md`: 13 lines with minimal info and external links

**Changes:** -393 lines total, +10 lines essential content

## Testing the Integration

Once the PR is merged, you can test the integration:

### Command Line Testing

```bash
# Test HTML content negotiation
curl -L -H "Accept: text/html" https://w3id.org/reliedu/

# Test Turtle content negotiation
curl -L -H "Accept: text/turtle" https://w3id.org/reliedu/

# Test JSON-LD content negotiation
curl -L -H "Accept: application/ld+json" https://w3id.org/reliedu/

# Test specific concept
curl -L -H "Accept: text/turtle" https://w3id.org/reliedu/didactics/korrelation
```

### Browser Testing

Simply visit in your browser:
- https://w3id.org/reliedu/
- https://w3id.org/reliedu/didactics/korrelation
- https://w3id.org/reliedu/competency/wahrnehmung

The browser will automatically receive HTML and display the SkoHub-generated interface.

## Benefits of w3id.org Integration

1. **Persistent URIs**: URIs remain stable even if GitHub Pages URL changes
2. **Professional**: Shorter, cleaner URIs for citations and references
3. **Standard Compliance**: Follows Linked Data best practices
4. **Content Negotiation**: Automatic format selection based on client needs
5. **Maintenance**: SkoHub handles all content generation and negotiation

## Usage in Metadata

### JSON-LD Example (AMB-compliant)

```json
{
  "@context": [
    "https://w3id.org/kim/amb/context.jsonld",
    {
      "reliedu": "https://w3id.org/reliedu/"
    }
  ],
  "id": "https://example.org/my-resource",
  "type": "LearningResource",
  "name": "Gleichnisse Jesu verstehen",
  "about": [
    "https://w3id.org/reliedu/didactics/subjektorientierung",
    "https://w3id.org/reliedu/didactics/biblisch"
  ],
  "teaches": [
    {
      "id": "https://w3id.org/reliedu/competency/deutung"
    }
  ]
}
```

### SPARQL Example

```sparql
PREFIX reliedu: <https://w3id.org/reliedu/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?concept ?label ?definition
WHERE {
  ?concept skos:inScheme reliedu: .
  ?concept skos:prefLabel ?label .
  FILTER(lang(?label) = "de")
  OPTIONAL { ?concept skos:definition ?definition }
}
```

## Maintenance

### Updating the Vocabulary

To update the vocabulary content:

1. **Edit** vocabulary in the reliedu-vocab repository
2. **Commit & Push** changes to trigger GitHub Actions
3. **SkoHub** automatically rebuilds and publishes to GitHub Pages
4. **w3id.org** redirects work automatically (no changes needed)

### Changing Target URL

If you need to change where w3id.org redirects to:

1. Fork the [perma-id/w3id.org](https://github.com/perma-id/w3id.org) repository
2. Edit `reliedu/.htaccess` with new target URL
3. Submit Pull Request with explanation
4. Wait for maintainer approval

## References

- **w3id.org Repository**: https://github.com/perma-id/w3id.org
- **Pull Request**: https://github.com/perma-id/w3id.org/pull/5381
- **OpenEduHub Template**: https://github.com/perma-id/w3id.org/tree/master/openeduhub
- **SkoHub Vocabs**: https://github.com/skohub-io/skohub-vocabs
- **Vocabulary Repository**: https://github.com/rpi-virtuell/reliedu-vocab
- **Vocabulary Website**: https://rpi-virtuell.github.io/reliedu-vocab/

## Contact

- **Maintainer**: Jörg Lohrer (@joerglohrer)
- **GitHub**: https://github.com/rpi-virtuell
- **Issues**: https://github.com/rpi-virtuell/reliedu-vocab/issues

---

*Last updated: October 21, 2025*
