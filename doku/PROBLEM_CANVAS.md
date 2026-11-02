# Problem Canvas

> Gate 1. Kurz und prüfbar halten, Stichpunkte genügen. Ersetze jeden Platzhalter `{{…}}` durch deinen Text.

## Ziel
Ein Regressionsmodell soll den Median-Hauswert einer Blockgruppe schätzen.

## Fachliche Fragestellung
Wie gut ist die Schätzung im Durchschnitt, in welchen Gruppen und Regionen ist sie unzuverlässig, und welche Aussagen dürfen daraus nicht abgeleitet werden?

## Nutzen / Stakeholder
Die fiktive Regionalverwaltung kann dadurch grob den typischen Hauswert einer Blockgruppe abschätzen. Außerdem erkennen Sie welche Einschätzungen nicht von der Vorhersage übernommen werden sollen, da erkannt wird welche Blockgruppen unzuverlässig vorhergesagt werden.

## Annahmen
- Der Datensatz enthält rund 20.640 Zeilen. Jede Zeile beschreibt eine Blockgruppe in Kalifornien.
- Die Zielspalte `MedHouseVal` gibt den Median-Hauswert in Einheiten von 100.000 US-Dollar an.
- Alle anderen 8 vorhandenen Merkmale wie Einkommen, Gebäudealter und Bevölkerungsdaten werden für die Vorhersage verwendet.
- Die Daten werden als Grundlage für die Schätzung betrachtet.

## Grenzen / Nicht-Ziele
- Es wird sich auf die Blockgruppen aus dem Staat Californien beschränkt. Alle anderen Staaten werden in den Vorhersagen nicht berücksichtigt.
- Es kann keine hundertprozentige Gewährleistung garantiert werden.

## Erfolgskriterium
{{Woran erkennst du am Ende ein gelungenes Ergebnis? Es muss prüfbar sein und darf nicht „bester Score“ lauten.}}
Das Modell ist messbar besser als die Baseline. Wo es unzuverlässig ist, belegen wir mit Zahlen und übersetzen es in Einsatzgrenzen, mit denen die Planungsabteilung arbeiten kann.