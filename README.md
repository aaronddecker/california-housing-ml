# California Housing: Hauswert-Schätzung und ihre Grenzen

> **Vorlage.** Das ist das README deines Projekts. Es ist die Startseite für alle, die dein Projekt nicht kennen: Worum geht
> es, wie startet man es, was ist herausgekommen? Du füllst es im Lauf des Projekts mit deiner Gruppe aus. Ersetze jeden Platzhalter
> in doppelten geschweiften Klammern `{{…}}` durch deinen Text und lösche diesen Kasten am Ende.

## 1. Überblick
Dieses Projekt untersucht, wie zuverlässig sich Hauswerte kalifornischer Wohngebiete mithilfe von Machine Learning schätzen lassen. Ziel ist es, der Planungsabteilung aufzuzeigen, in welchen Einkommensgruppen und Regionen die Vorhersagen besonders ungenau sind.

Die Fehleranalyse zeigt größere Abweichungen bei hohen Einkommen und gedeckelten Hauswerten sowie regionale Unterschiede. Das Modell eignet sich daher eher für grobe Einschätzungen als für präzise Immobilienbewertungen.

## 2. Team
- Gruppe: 4
- Projektleitung: Aaron

## 3. Projektstruktur und Datenfluss
- Notebooks: `notebooks/01_data_understanding`, `02_preparation_modeling`, `03_evaluation_report`.
- Datenfluss: Laden (scikit-learn, CSV, SQLite) → Aufbereitung → Modellierung → Evaluation.

## 4. Setup
```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## 5. Ausführung
Die Notebooks werden in folgender Reihenfolge vollständig ausgeführt:

- `01_data_understanding.ipynb` – Daten laden, untersuchen und für die weiteren Schritte vorbereiten.
- `02_preparation_modeling.ipynb` – Trainings- und Testdaten aufteilen, Modelle vergleichen und Merkmale transformieren.
- `03_evaluation_report.ipynb` – Gewähltes Modell auswerten und Fehler nach Einkommen, gedeckelten Zielwerten und Regionen analysieren.

## 6. Daten
- Quelle und Zitation: siehe `doku/DATASET_NOTICE.md`.
- Die Daten werden vom Vorbereitungs-Notebook erzeugt und sind nicht eingecheckt.

## 7. Reproduzierbarkeit
- Fester Seed: 42.
- Notebooks laufen von oben nach unten. Alle Ergebnisse stammen aus dem Code.
- Selbstcheck (Gate 9): ☐ Kernel neu gestartet ☐ alle Notebooks von oben nach unten gelaufen — Datum: 10.11.2026

## 8. Tests
{{Nur bei S4: Wie ruft man den Smoke-Test auf, und was prüft er?}}

## 9. Verwendete Bibliotheken
- pandas: 3.1.0
- numpy: 2.5.4
- matplotlib: 3.11.2
- scikit-learn: 1.9.1
- joblib: 1.6.0
- IPython: 9.18.0

## 10. Ergebnis

Die `LinearRegression` mit Log-Transformation wurde aufgrund des niedrigsten CV-MAE von 0,4836 ausgewählt. Die Baseline (`DummyRegressor`) erreichte 0,9139, die ursprüngliche `LinearRegression` 0,5291 und der `DecisionTreeRegressor` 0,4864.

**Fehleranalyse:**
- **Einkommen:** Der MAE steigt von 0,4110 (niedriges Einkommen) auf 0,5589 (hohes Einkommen).
- **Gedeckelte Zielwerte:** Der MAE beträgt 1,3522 gegenüber 0,4513 bei nicht gedeckelten Werten.
- **Regionen:** San Francisco Bay Area (MAE 0,5495), Los Angeles (0,4906) und Central Valley (0,4369).

Alle Fehlerwerte beziehen sich auf Einheiten von 100.000 US-Dollar. Das Modell eignet sich für grobe Schätzungen, jedoch nicht für präzise Immobilienbewertungen.

## 11. Bekannte Einschränkungen

- Hauswerte sind bei `5.00001` (ca. 500.001 $) gedeckelt.
- Die Vorhersagefehler unterscheiden sich je nach Einkommen und Region.
- Die untersuchten Regionen sind vereinfacht definiert und decken nicht ganz Kalifornien ab.
- Das Modell erlaubt keine zuverlässige Bewertung einzelner Immobilien oder kausale Schlussfolgerungen.

## 12. Eigene Ideen der Gruppe
- {{Idee, Nutzen für die Planungsabteilung, umgesetzt ja oder nein.}}
