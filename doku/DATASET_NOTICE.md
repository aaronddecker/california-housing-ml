# Dataset Notice

## Datensatz
California Housing: Zensusdaten 1990 je Blockgruppe in Kalifornien (20.640 Zeilen, 8 Merkmale und der Median-Hauswert als Zielwert).

## Quelle
- Bezug: `sklearn.datasets.fetch_california_housing(as_frame=True)` (scikit-learn), geladen durch `notebooks/00_vorbereitung.ipynb`.
- Herkunft laut scikit-learn-Dokumentation: StatLib-Repository (<https://lib.stat.cmu.edu/datasets/houses.zip>), abgeleitet aus dem US-Zensus 1990.
- Originalveröffentlichung: Pace, R. K. & Barry, R. (1997).

## Abrufdatum
2026-11-02

## Nutzung im Kurs
- Die Daten werden über scikit-learn bezogen und im Kurs zu Übungszwecken genutzt.
- Die Datendateien entstehen lokal beim Ausführen des Vorbereitungs-Notebooks und werden nicht eingecheckt (`.gitignore`).

## Zitation / Attribution
Pace, R. K. & Barry, R. (1997). Sparse Spatial Autoregressions. *Statistics and Probability Letters*, 33, 291–297. Bezogen über scikit-learn (<https://scikit-learn.org/stable/datasets/real_world.html#california-housing-dataset>).

## Veränderungen durch die Projektgruppe
- Ablage als `data/raw/california_housing.csv` und in der SQLite-Tabelle `blockgruppen`, ohne inhaltliche Veränderung der Rohdaten.
- Aufteilung in 80 % Trainingsdaten und 20 % Testdaten (`random_state=42`).
- Log-Transformation der Merkmale `AveRooms`, `AveBedrms`, `Population` und `AveOccup` für die ausgewählte Modellvariante.
- Keine Ausreißer oder gedeckelten Zielwerte entfernt.
- Für die Fehleranalyse wurden Residuen, Einkommensgruppen und geografische Regionen abgeleitet.

## Datenschutz / personenbezogene Daten
Der Datensatz enthält aggregierte statistische Angaben auf Ebene kalifornischer Zensus-Blockgruppen. Es sind keine direkten personenbezogenen Identifikatoren oder individuellen Haushaltsdatensätze enthalten. Die zugrunde liegenden Zensusdaten stammen aus dem Jahr 1990.
