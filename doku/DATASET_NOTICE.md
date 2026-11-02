# Dataset Notice

> Ergänze die Abschnitte mit Platzhaltern `{{…}}` (Tag 7). Die übrigen Angaben sind vorbereitet.

## Datensatz
California Housing: Zensusdaten 1990 je Blockgruppe in Kalifornien (20.640 Zeilen, 8 Merkmale und der Median-Hauswert als Zielwert).

## Quelle
- Bezug: `sklearn.datasets.fetch_california_housing(as_frame=True)` (scikit-learn), geladen durch `notebooks/00_vorbereitung.ipynb`.
- Herkunft laut scikit-learn-Dokumentation: StatLib-Repository (<https://lib.stat.cmu.edu/datasets/houses.zip>), abgeleitet aus dem US-Zensus 1990.
- Originalveröffentlichung: Pace, R. K. & Barry, R. (1997).

## Abrufdatum
{{Datum, an dem das Vorbereitungs-Notebook zum ersten Mal erfolgreich lief (JJJJ-MM-TT).}}

## Nutzung im Kurs
- Die Daten werden über scikit-learn bezogen und im Kurs zu Übungszwecken genutzt.
- Die Datendateien entstehen lokal beim Ausführen des Vorbereitungs-Notebooks und werden nicht eingecheckt (`.gitignore`).

## Zitation / Attribution
Pace, R. K. & Barry, R. (1997). Sparse Spatial Autoregressions. *Statistics and Probability Letters*, 33, 291–297. Bezogen über scikit-learn (<https://scikit-learn.org/stable/datasets/real_world.html#california-housing-dataset>).

## Veränderungen durch die Projektgruppe
- Ablage als `data/raw/california_housing.csv` und SQLite-Tabelle `blockgruppen`, keine inhaltliche Änderung.
- {{Weitere Änderungen, zum Beispiel abgeleitete Merkmale, Filter oder entfernte Zeilen.}}

## Datenschutz / personenbezogene Daten
Die Daten sind über Blockgruppen zusammengefasst und enthalten keine Angaben zu einzelnen Personen oder Haushalten. Der Datenstand ist 1990.
