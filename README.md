# California Housing: Hauswert-Schätzung und ihre Grenzen

## 1. Überblick
Dieses Projekt untersucht, wie zuverlässig sich Hauswerte kalifornischer Wohngebiete mithilfe von Machine Learning schätzen lassen. Ziel ist es, der Planungsabteilung aufzuzeigen, in welchen Einkommensgruppen und Regionen die Vorhersagen besonders ungenau sind.

Die Fehleranalyse zeigt größere Abweichungen bei hohen Einkommen und gedeckelten Hauswerten sowie regionale Unterschiede. Das Modell eignet sich daher eher für grobe Einschätzungen als für präzise Immobilienbewertungen.

## 2. Team
- Gruppe: 4
- Projektleitung: Aaron
- Projektkollege: Oliver

## 3. Projektstruktur und Datenfluss

- `notebooks/` – Jupyter-Notebooks zur Datenvorbereitung, Analyse, Modellierung und Evaluation.
- `doku/` – Projektdokumentation, Modellentscheidungen und Fehleranalyse.
- `presentation/` – Dokumentation der Abschlusspräsentation.
- - `PROJEKTAUFTRAG.md` – Ausgangssituation, Projektziele, Vorgehensweise und mögliche Weiterentwicklungen.

**Datenfluss:** scikit-learn → CSV/SQLite → Datenanalyse → Aufbereitung → Modellierung → Evaluation.

## 4. Setup
```bash
git clone https://github.com/aaronddecker/california-housing-ml.git
cd california-housing-ml
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## 5. Ausführung

Die Notebooks werden in folgender Reihenfolge vollständig ausgeführt:

1. `00_vorbereitung.ipynb` – California-Housing-Datensatz laden und als CSV und SQLite-Datenbank bereitstellen.
2. `01_data_understanding.ipynb` – Daten untersuchen und Datenqualität analysieren.
3. `02_preparation_modeling.ipynb` – Trainings- und Testdaten aufteilen, Modelle vergleichen und Merkmale transformieren.
4. `03_evaluation_report.ipynb` – Gewähltes Modell auswerten und Fehler nach Einkommen, gedeckelten Zielwerten und Regionen analysieren.

## 6. Daten
- Quelle und Zitation: siehe `doku/DATASET_NOTICE.md`.
- Die Daten werden vom Vorbereitungs-Notebook erzeugt und sind nicht eingecheckt.

## 7. Reproduzierbarkeit
- Fester Seed: 42.
- Notebooks laufen von oben nach unten. Alle Ergebnisse stammen aus dem Code.
- Reproduzierbarkeit geprüft (Gate 9 am 10.11.2026):
  Kernel neu gestartet und alle Notebooks vollständig
  von oben nach unten ausgeführt.


## 8. Verwendete Bibliotheken
- pandas: 3.1.0
- numpy: 2.5.4
- matplotlib: 3.11.2
- scikit-learn: 1.9.1
- joblib: 1.6.0
- IPython: 9.18.0

## 9. Ergebnis

Die Modelle wurden mittels 5-Fold-Cross-Validation auf den Trainingsdaten verglichen. Als Bewertungsmetrik wurde der Mean Absolute Error (MAE) verwendet.

| Modell | CV-MAE | Fehler in USD (ca.) |
|---|---:|---:|
| DummyRegressor (Baseline) | 0,9139 | 91.390 $ |
| LinearRegression (ohne Transformation) | 0,5291 | 52.910 $ |
| DecisionTreeRegressor | 0,4864 | 48.640 $ |
| **LinearRegression (Log-Transformation)** | **0,4836** | **48.360 $** |

Aufgrund des niedrigsten CV-MAE wurde die `LinearRegression` mit Log-Transformation ausgewählt. Der Unterschied zum `DecisionTreeRegressor` fällt allerdings gering aus.

**Fehleranalyse:**
- **Einkommen:** Der MAE steigt von 0,4110 (niedriges Einkommen) auf 0,5589 (hohes Einkommen).
- **Gedeckelte Zielwerte:** Der MAE beträgt 1,3522 gegenüber 0,4513 bei nicht gedeckelten Werten.
- **Regionen:** San Francisco Bay Area (MAE 0,5495), Los Angeles (0,4906) und Central Valley (0,4369).

Alle Fehlerwerte beziehen sich auf Einheiten von 100.000 US-Dollar. Die CV-MAE-Werte stammen aus der Kreuzvalidierung auf den Trainingsdaten, während die Fehleranalyse auf den Testdaten basiert.

Das Modell eignet sich für grobe Schätzungen, jedoch nicht für präzise Immobilienbewertungen.

## 10. Bekannte Einschränkungen

- Hauswerte sind bei `5.00001` (ca. 500.001 $) gedeckelt.
- Die Vorhersagefehler unterscheiden sich je nach Einkommen und Region.
- Die untersuchten Regionen sind vereinfacht definiert und decken nicht ganz Kalifornien ab.
- Das Modell erlaubt keine zuverlässige Bewertung einzelner Immobilien oder kausale Schlussfolgerungen.

## 11. Ausblick
Als nächster Schritt könnten weitere Regressionsmodelle untersucht und die Vorhersagequalität durch eine räumlich getrennte Validierung überprüft werden. Dadurch ließe sich besser beurteilen, wie zuverlässig das Modell auf bisher unbekannte Regionen übertragbar ist.
