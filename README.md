# codelijst-ruimtelijkeplannen

## Samenvatting
TODO: korte beschrijving van de codelijst ruimtelijkeplannen, zoals die binnen het kader van het OSLO thema omgeving is opgesteld, en tools om deze lijst te beheren en om te zetten naar webformaten.

## TODO

Dit project is opgezet als skelet op basis van codelijst-luchtzuiveringssysteem. Nog te doen:

- [ ] Samenvatting hierboven invullen.
- [ ] In `src/source/config.yml` de `TODO`-waarden onder `metadata.dataset` invullen: `description` en `provenance.label`; `title` nakijken.
- [ ] In `src/source/config.yml` nagaan of `theme` (eurovoc, gemet, ...) en `spatial` passen voor deze codelijst.
- [ ] In `src/source/codelijst-source.csv` de definitie van het conceptschema `conceptscheme:ruimtelijkeplannen` invullen en het concept `voorbeeld` vervangen door de eigenlijke concepten; daarna `npm run create_skos` om de bestanden in `src/main/resources/be/vlaanderen/omgeving/data/id/conceptscheme/ruimtelijkeplannen/` opnieuw te genereren.
- [ ] Extra CSV-kolommen die nodig zijn toevoegen aan `src/source/context.json` (en zo nodig aan de frames in `src/utils/variables.js`).
- [ ] De SHACL-shapes in `src/main/resources/be/vlaanderen/omgeving/data/id/ontology/ruimtelijkeplannen-ap-constraints/ruimtelijkeplannen-ap-constraints.ttl` afstemmen op de codelijst (verplichte velden, kardinaliteiten, eventuele extra eigenschappen).
- [ ] Nakijken of de `LICENSE` (GPL v3) de juiste licentie is.

## Structuur

| Pad | Inhoud |
|-----|--------|
| `src/source/codelijst-source.csv` | bron van de codelijst (1 rij per conceptschema, collectie of concept) |
| `src/source/config.yml` | configuratie: namespaces, prefixen, DCAT-metadata van dataset en distributies |
| `src/source/context.json` | JSON-LD context die de CSV-kolommen op RDF-termen afbeeldt |
| `src/main/resources/be/vlaanderen/omgeving/data/id/ontology/ruimtelijkeplannen-ap-constraints/` | SHACL-shapes waartegen de codelijst gevalideerd wordt |
| `src/main/resources/be/vlaanderen/omgeving/data/id/conceptscheme/ruimtelijkeplannen/` | gegenereerde codelijst (ttl, nt, jsonld, json, csv, parquet, xlsx) |

## Gebruik

### Voeg een definitie van een nieuw concept toe aan $PROJECT_HOME/src/source/codelijst-source.csv

### Voer het transformatiescript uit:
```
cd $PROJECT_HOME
npm run create_skos
```

### Run een maven build (testen worden uitgevoerd en metadata aangemaakt)
```
cd $PROJECT_HOME
mvn clean install
```

## Dependencies

**_nodejs_**

### Installeer libraries in package.json
```
cd $PROJECT_HOME
npm install
```
