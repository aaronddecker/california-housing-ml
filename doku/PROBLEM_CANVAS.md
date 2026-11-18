# Problem Canvas

## Ziel
Ein Regressionsmodell soll den Median-Hauswert einer Blockgruppe schätzen.

## Fachliche Fragestellung
Wie gut ist die Schätzung im Durchschnitt, in welchen Gruppen und Regionen ist sie unzuverlässig, und welche Aussagen dürfen daraus nicht abgeleitet werden?

## Nutzen / Stakeholder
Die fiktive Regionalverwaltung kann mithilfe des Modells den typischen Hauswert einzelner Blockgruppen grob einschätzen. Durch die zusätzliche Fehleranalyse wird deutlich, in welchen Einkommensgruppen und Regionen die Vorhersagen besonders unzuverlässig sind. So kann die Planungsabteilung erkennen, wann Schätzwerte nur eingeschränkt als Entscheidungsgrundlage geeignet sind.

## Annahmen
- Der Datensatz enthält rund 20.640 Zeilen. Jede Zeile beschreibt eine Blockgruppe in Kalifornien.
- Die Zielspalte `MedHouseVal` gibt den Median-Hauswert in Einheiten von 100.000 US-Dollar an.
- Alle anderen 8 vorhandenen Merkmale wie Einkommen, Gebäudealter und Bevölkerungsdaten werden für die Vorhersage verwendet.
- - Die historischen Zensusdaten aus dem Jahr 1990 werden als Grundlage für eine methodische Untersuchung verwendet und bilden keine aktuellen Immobilienpreise ab.

## Grenzen / Nicht-Ziele
- Die Untersuchung beschränkt sich auf kalifornische Zensus-Blockgruppen.
- Der Datensatz basiert auf Zensusdaten aus dem Jahr 1990 und erlaubt keine Aussagen über aktuelle Immobilienpreise.
- Das Modell schätzt Median-Hauswerte von Blockgruppen, nicht die Preise einzelner Immobilien.
- Die Zielwerte sind bei etwa 500.001 US-Dollar gedeckelt, wodurch besonders hohe Hauswerte nur eingeschränkt abgebildet werden.
- Das Modell dient einer groben Einschätzung und ersetzt keine professionelle Immobilienbewertung.
- Aus den Modellvorhersagen lassen sich keine kausalen Zusammenhänge ableiten.

## Erfolgskriterium
Das Modell erreicht bei der 5-Fold-Cross-Validation einen niedrigeren MAE als die Baseline (`DummyRegressor`). Zusätzlich werden die Vorhersagefehler nach Einkommensgruppen, gedeckelten Zielwerten und Regionen untersucht und anhand konkreter Kennzahlen dokumentiert. Daraus werden nachvollziehbare Einsatzgrenzen für die fiktive Planungsabteilung abgeleitet.