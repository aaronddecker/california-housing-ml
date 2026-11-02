# California Housing: Hauswert-Schätzung und ihre Grenzen

> **Vorlage.** Das ist das README deines Projekts. Es ist die Startseite für alle, die dein Projekt nicht kennen: Worum geht
> es, wie startet man es, was ist herausgekommen? Du füllst es im Lauf des Projekts mit deiner Gruppe aus. Ersetze jeden Platzhalter
> in doppelten geschweiften Klammern `{{…}}` durch deinen Text und lösche diesen Kasten am Ende.

## 1. Überblick
{{Was macht das Projekt, für wen, und welche Frage beantwortet es? Am Ende ergänzt du eine Kurzfassung des Ergebnisses in zwei bis drei Sätzen.}}

## 2. Team
- Gruppe: {{Namen}}
- Projektleitung: {{Name}}

## 3. Projektstruktur und Datenfluss
- Notebooks: `notebooks/01_data_understanding`, `02_preparation_modeling`, `03_evaluation_report`.
- Datenfluss: Laden (scikit-learn, CSV, SQLite) → Aufbereitung → Modellierung → Evaluation.
- {{Falls du Code nach `src/` ausgelagert hast (K4): welche Funktionen in welcher Datei liegen.}}

## 4. Setup
```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## 5. Ausführung
{{In welcher Reihenfolge führt man die Notebooks aus? Das Vorbereitungs-Notebook kommt zuerst.}}

## 6. Daten
- Quelle und Zitation: siehe `doku/DATASET_NOTICE.md`.
- Die Daten werden vom Vorbereitungs-Notebook erzeugt und sind nicht eingecheckt.

## 7. Reproduzierbarkeit
- Fester Seed: {{Seed}}.
- Notebooks laufen von oben nach unten. Alle Ergebnisse stammen aus dem Code.
- Selbstcheck (Gate 9): ☐ Kernel neu gestartet ☐ alle Notebooks von oben nach unten gelaufen — Datum: {{Datum}}

## 8. Tests
{{Nur bei S4: Wie ruft man den Smoke-Test auf, und was prüft er?}}

## 9. Verwendete Bibliotheken
{{Die wichtigsten Pakete aus `requirements.txt` mit Version.}}

## 10. Ergebnis
{{Am Ende ausfüllen: Kennzahlen von Baseline und Modell, Fehlerbild nach Einkommen und Region, Einsatzgrenzen.}}

## 11. Bekannte Einschränkungen
- {{Was das Modell nicht kann oder wo die Daten Grenzen haben.}}

## 12. Eigene Ideen der Gruppe
- {{Idee, Nutzen für die Planungsabteilung, umgesetzt ja oder nein.}}
