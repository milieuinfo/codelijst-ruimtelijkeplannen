# codelijst-ruimtelijkeplannen

## Samenvatting
Codelijsten in verband met ruimtelijke plannen, zoals die binnen het kader van het OSLO thema omgeving zijn opgesteld, en tools om deze lijsten te beheren en om te zetten naar webformaten.

Alle codelijsten worden samen gepubliceerd als één dataset (`codelijst-ruimtelijkeplannen`); elk conceptschema is een `void:rootResource` van die dataset.

## Codelijsten

| Conceptschema | Bron | Concept-namespace |
|---------------|------|-------------------|
| `https://data.omgeving.vlaanderen.be/id/conceptscheme/ruimtelijkeplannen` | `src/source/codelijst-source.csv` | `https://data.omgeving.vlaanderen.be/id/concept/ruimtelijkeplannen/` (prefix `concept`, ook `@base`) |
| `https://data.omgeving.vlaanderen.be/id/conceptscheme/ruimtelijkeplannen/procedurekenmerken` | `src/source/codelijst-procedurekenmerken-source.csv` | `https://data.omgeving.vlaanderen.be/id/concept/ruimtelijkeplannen/procedurekenmerken/` (prefix `procedurekenmerken`) |

## TODO

Nog te doen:

- [ ] In `src/source/config.yml` de `TODO`-waarden onder `metadata.dataset` invullen: `description` en `provenance.label`.
- [ ] In `src/source/config.yml` nagaan of `theme` (eurovoc, gemet, ...) en `spatial` passen voor deze codelijsten.
- [ ] In `src/source/codelijst-source.csv` de definitie van het conceptschema `conceptscheme:ruimtelijkeplannen` invullen en het concept `voorbeeld` vervangen door de eigenlijke concepten.
- [ ] In `src/source/codelijst-procedurekenmerken-source.csv` de definitie van `recht-van-voorkoop` invullen.
- [ ] Extra CSV-kolommen die nodig zijn toevoegen aan `src/source/context.json` (en zo nodig aan de frames in `src/utils/variables.js`).
- [ ] De SHACL-shapes in `src/main/resources/be/vlaanderen/omgeving/data/id/ontology/ruimtelijkeplannen-ap-constraints/ruimtelijkeplannen-ap-constraints.ttl` afstemmen op de codelijsten (verplichte velden, kardinaliteiten, eventuele extra eigenschappen).
- [ ] Nakijken of de `LICENSE` (GPL v3) de juiste licentie is.

## Structuur

| Pad | Inhoud |
|-----|--------|
| `src/source/codelijst-source.csv` | bron van de codelijst ruimtelijkeplannen (1 rij per conceptschema, collectie of concept) |
| `src/source/codelijst-procedurekenmerken-source.csv` | bron van de codelijst procedurekenmerken |
| `src/source/config.yml` | configuratie: bron-CSV's, namespaces, prefixen, DCAT-metadata van dataset en distributies |
| `src/source/context.json` | JSON-LD context die de CSV-kolommen op RDF-termen afbeeldt |
| `src/main/resources/be/vlaanderen/omgeving/data/id/ontology/ruimtelijkeplannen-ap-constraints/` | SHACL-shapes waartegen de codelijsten gevalideerd worden |
| `src/main/resources/be/vlaanderen/omgeving/data/id/conceptscheme/ruimtelijkeplannen/` | gegenereerde codelijsten, alle conceptschema's samen (ttl, nt, jsonld, json, csv, parquet, xlsx) |

## Gebruik

### Voeg een definitie van een nieuw concept toe aan de bron-CSV van de betreffende codelijst in $PROJECT_HOME/src/source/

### Een nieuwe codelijst toevoegen
1. Maak een nieuwe bron-CSV in `src/source/` met dezelfde kolommen als de bestaande.
2. Voeg de bestandsnaam toe aan de lijst `source.codelijst_csv` in `src/source/config.yml`.
3. Voeg onder `skos.prefixes` in `src/source/config.yml` een prefix toe voor de concepten, bv. `https://data.omgeving.vlaanderen.be/id/concept/ruimtelijkeplannen/<naam>/`, en gebruik die prefix in de `_id`-kolom.
4. Gebruik als `_id` van het conceptschema `conceptscheme_ruimtelijkeplannen:<naam>`.

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
