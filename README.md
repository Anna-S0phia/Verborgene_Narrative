# Verborgene Narrative
Repository for my Master Thesis "Verborgene Narrative? Klappeffekte spätmittelalterlicher Flügelaltäre in Forschungsdiskurs und Ausstellungspraxis"
(engl: "Hidden narratives? Folding effects of late medieval winged altars in research discourse and exhibitions")

Datenerhebung erfolgt mit folgendem Query-Inhalt: Das gesuchte Subjekt gehört zur Kategorie oder einer Unterkategorie von wd:Q1278452 = "Polyptychon" zusätzlich gefiltert über p:P571 = "Entstehungszeit" größer gleich 1400 und kleiner 1526 auf https://query.wikidata.org/. Link zum Query: https://w.wiki/EVzL:

SELECT DISTINCT ?item ?itemLabel WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],mul,en". }
  {
    SELECT DISTINCT ?item WHERE {
      ?item p:P31 ?statement0.
      ?statement0 (ps:P31/(wdt:P279*)) wd:Q1278452.
      {
        ?item p:P571 ?statement_1.
        ?statement_1 psv:P571 ?statementValue_1.
        ?statementValue_1 wikibase:timePrecision ?precision_1.
        hint:Prior hint:rangeSafe "true"^^xsd:boolean.
        FILTER(?precision_1 >= 9 )
        ?statementValue_1 wikibase:timeValue ?P571_1.
        hint:Prior hint:rangeSafe "true"^^xsd:boolean.
        FILTER(?P571_1 >= "+1400-00-00T00:00:00Z"^^xsd:dateTime)
        FILTER(EXISTS { ?statement_1 prov:wasDerivedFrom ?reference. })
      }
      ?item p:P571 ?statement_2.
      ?statement_2 psv:P571 ?statementValue_2.
      ?statementValue_2 wikibase:timePrecision ?precision_2.
      hint:Prior hint:rangeSafe "true"^^xsd:boolean.
      FILTER(?precision_2 >= 9 )
      ?statementValue_2 wikibase:timeValue ?P571_2.
      hint:Prior hint:rangeSafe "true"^^xsd:boolean.
      FILTER(?P571_2 < "+1526-00-00T00:00:00Z"^^xsd:dateTime)
    }
  }
}
