# Projektauftrag – California Housing

## 1. Ausgangssituation

Dieses Machine-Learning-Projekt entstand im Rahmen einer Weiterbildung zum Spezialisten für angewandte KI, Machine Learning und Datenanalyse.

Als Anwendungsszenario dient eine fiktive regionale Planungsabteilung in Kalifornien. Diese möchte anhand historischer Zensusdaten den typischen Hauswert verschiedener Wohngebiete abschätzen, beispielsweise um Gebiete für weiterführende Untersuchungen vorauszuwählen.

Dabei ist nicht nur die durchschnittliche Genauigkeit der Vorhersagen relevant. Die Planungsabteilung möchte auch verstehen, in welchen Einkommensgruppen und Regionen besonders große Schätzfehler auftreten und wann die Vorhersagen nicht als verlässliche Entscheidungsgrundlage geeignet sind.

Das Projekt ist eine methodische Untersuchung auf Basis historischer Daten und stellt keine aktuelle Immobilienbewertung dar.

## 2. Zielsetzung und Fragestellung

Ziel des Projekts war die Entwicklung und Evaluation eines Regressionsmodells, das den Median-Hauswert kalifornischer Zensus-Blockgruppen anhand sozioökonomischer, demografischer und geografischer Merkmale schätzt.

**Zentrale Fragestellung:**

> Wie zuverlässig lassen sich die Median-Hauswerte kalifornischer Wohngebiete anhand historischer Zensusdaten vorhersagen, in welchen Gruppen und Regionen treten besonders große Fehler auf und welche Einsatzgrenzen ergeben sich daraus?

Daraus ergeben sich vier Teilziele:

1. Ein nachvollziehbares Regressionsmodell zur Schätzung des Median-Hauswerts entwickeln.
2. Die Vorhersagequalität anhand geeigneter Kennzahlen mit einer einfachen Baseline vergleichen.
3. Vorhersagefehler nach Einkommensgruppen, gedeckelten Zielwerten und geografischen Regionen untersuchen.
4. Die Ergebnisse verständlich interpretieren und Grenzen einer möglichen Anwendung dokumentieren.

Im Mittelpunkt steht nicht die Maximierung einer einzelnen Modellkennzahl, sondern die nachvollziehbare Bewertung der Modellzuverlässigkeit.

## 3. Datengrundlage

Verwendet wird der öffentlich verfügbare California-Housing-Datensatz aus `scikit-learn`.

| Eigenschaft | Beschreibung |
|---|---|
| Datenquelle | California Housing (`scikit-learn`) |
| Datenstand | US-Zensus von 1990 |
| Umfang | 20.640 Beobachtungen |
| Untersuchungseinheit | Zensus-Blockgruppe |
| Eingangsmerkmale | 8 numerische Merkmale |
| Zielvariable | `MedHouseVal` |
| Zieleinheit | 100.000 US-Dollar |
| Aufgabentyp | Überwachtes Lernen – Regression |

Zu den Eingangsmerkmalen gehören unter anderem das Medianeinkommen, das Gebäudealter, durchschnittliche Zimmer- und Schlafzimmerzahlen, Bevölkerungsdaten sowie geografische Koordinaten.

**Wichtige Einschränkungen:**

- Die Daten beschreiben Wohngebiete und keine einzelnen Immobilien.
- Die Beobachtungen stammen aus dem Jahr 1990 und erlauben keine Aussagen über aktuelle Immobilienpreise.
- Die Zielvariable ist bei ungefähr 500.001 US-Dollar gedeckelt. Besonders hohe Hauswerte können dadurch nicht vollständig abgebildet werden.
- Aus statistischen Zusammenhängen lassen sich keine kausalen Aussagen ableiten.

Weitere Informationen zu den Daten und ihrer Herkunft befinden sich in [`doku/DATASET_NOTICE.md`](doku/DATASET_NOTICE.md) und [`doku/DATA_DICTIONARY.md`](doku/DATA_DICTIONARY.md).

## 4. Projektumfang und Vorgehensweise

Das Projekt orientiert sich an den grundlegenden Phasen eines Machine-Learning-Projekts und lehnt sich methodisch an CRISP-DM an.

### 4.1 Problemverständnis

Zunächst wurden die fachliche Fragestellung, die vorgesehenen Einsatzmöglichkeiten und die Erfolgskriterien definiert.

Dabei wurde festgelegt, dass das Modell eine einfache Vergleichsschätzung übertreffen und seine Zuverlässigkeit anhand einer differenzierten Fehleranalyse beurteilt werden soll.

Die fachlichen Anforderungen sind im [`Problem Canvas`](doku/PROBLEM_CANVAS.md) dokumentiert.

### 4.2 Datenverständnis und explorative Datenanalyse

Der Datensatz wurde hinsichtlich seiner Struktur, Merkmale, Werteverteilungen und Datenqualität untersucht.

Zu den Untersuchungsschwerpunkten gehörten:

- Bedeutung und Wertebereiche der einzelnen Merkmale
- Fehlende Werte, Duplikate und auffällige Beobachtungen
- Verteilung der Zielvariable
- Zusammenhang zwischen Medianeinkommen und Hauswerten
- Geografische Verteilung der Wohngebiete
- Ausreißer und gedeckelte Zielwerte

Auffälligkeiten wurden dokumentiert und hinsichtlich ihrer möglichen Auswirkungen auf die Modellierung bewertet.

### 4.3 Datenaufbereitung

Die Daten wurden in Trainings- und Testdaten aufgeteilt:

- 80 % Trainingsdaten
- 20 % Testdaten
- Reproduzierbare Aufteilung mit `random_state=42`

Die Testdaten wurden für die abschließende Bewertung zurückgehalten.

Für die Modellauswahl wurde eine fünffache Kreuzvalidierung auf den Trainingsdaten verwendet.

Zusätzlich wurden verschiedene Möglichkeiten zur Behandlung auffälliger Merkmale und gedeckelter Zielwerte untersucht.

### 4.4 Modellierung und Modellvergleich

Als einfache Vergleichsschätzung wurde ein `DummyRegressor` verwendet, der den Mittelwert der Trainingszielwerte vorhersagt.

Darüber hinaus wurden folgende Modelle untersucht:

- `LinearRegression` mit unveränderten Eingangsmerkmalen
- `DecisionTreeRegressor` mit begrenzter Baumtiefe
- `LinearRegression` mit logarithmisch transformierten Merkmalen

Die Modellqualität wurde insbesondere anhand des mittleren absoluten Fehlers (MAE) bewertet. Ergänzend wurden RMSE und R² berücksichtigt.

Die Auswahl des finalen Modells erfolgte anhand der Kreuzvalidierung und einer nachvollziehbaren Abwägung der Ergebnisse.

### 4.5 Fehleranalyse und Interpretation

Neben der durchschnittlichen Modellqualität wurde untersucht, unter welchen Bedingungen besonders große Vorhersagefehler auftreten.

Die Analyse umfasste:

- Vorhersagefehler in verschiedenen Einkommensgruppen
- Fehler bei gedeckelten und nicht gedeckelten Zielwerten
- Regionale Unterschiede zwischen ausgewählten Gebieten Kaliforniens
- Richtung und Größe der Residuen
- Auswirkungen der Datenbeschränkungen auf die Interpretation

Auf dieser Grundlage wurden die bekannten Schwächen und Einsatzgrenzen des Modells beschrieben.

## 5. Erfolgskriterien

Das Projekt wurde anhand folgender Kriterien beurteilt:

| Kriterium | Erwartetes Ergebnis |
|---|---|
| Modellqualität | Das ausgewählte Modell erreicht einen geringeren MAE als die Baseline. |
| Nachvollziehbarkeit | Datenaufbereitung, Modellierung und Evaluation sind dokumentiert und reproduzierbar. |
| Fehleranalyse | Unterschiede zwischen Einkommensgruppen, gedeckelten Zielwerten und Regionen werden quantitativ untersucht. |
| Interpretation | Ergebnisse werden fachlich verständlich erklärt und mit konkreten Kennzahlen belegt. |
| Einsatzgrenzen | Bekannte Schwächen und ungeeignete Anwendungsszenarien werden ausdrücklich benannt. |

Die erreichten Kennzahlen und die daraus abgeleiteten Schlussfolgerungen sind in der [`README.md`](README.md) und der [`Model Card`](doku/MODEL_CARD.md) dokumentiert.

## 6. Technische Rahmenbedingungen

**Projektart:** Gruppenprojekt im Rahmen einer Weiterbildung

**Teamgröße:** Zwei Personen

**Verwendete Technologien:**

- Python 3
- Jupyter Notebook
- pandas und NumPy
- Matplotlib
- scikit-learn
- SQLite
- Git und GitHub

Die einzelnen Analyseschritte wurden in Jupyter-Notebooks umgesetzt. Die Ergebnisse und wesentlichen Entscheidungen sind in ergänzenden Markdown-Dateien dokumentiert.

## 7. Umgesetzte Erweiterungen

Über die grundlegende Regressionsanalyse hinaus wurden zusätzliche Ansätze untersucht.

### 7.1 Vergleich mehrerer Modellverfahren

Neben der Baseline und einer linearen Regression wurde ein `DecisionTreeRegressor` mit begrenzter Baumtiefe trainiert.

Die Modelle wurden anhand einer fünffachen Kreuzvalidierung miteinander verglichen.

Dadurch ließ sich untersuchen, ob ein nichtlineares Modell gegenüber einer linearen Regression Vorteile bietet.

### 7.2 Feature Engineering

Die Merkmale `AveRooms`, `AveBedrms`, `Population` und `AveOccup` zeigten stark rechtsschiefe Verteilungen.

Deshalb wurde eine logarithmische Transformation dieser Merkmale untersucht.

Die Transformation verbesserte den Kreuzvalidierungs-MAE der linearen Regression von 0,5291 auf 0,4836.

Das Ergebnis verdeutlicht, dass eine gezielte Merkmalsaufbereitung die Modellqualität verbessern kann, ohne zwangsläufig ein komplexeres Modell einzusetzen.

### 7.3 Model Card

Für das finale Modell wurde eine eigenständige Model Card erstellt.

Sie dokumentiert:

- Zweck und vorgesehenen Einsatzbereich
- Datengrundlage und Modellverfahren
- Evaluationskennzahlen
- Bekannte Schwächen
- Einsatzgrenzen und ungeeignete Anwendungen

Die vollständige Dokumentation befindet sich in [`doku/MODEL_CARD.md`](doku/MODEL_CARD.md).

## 8. Mögliche Weiterentwicklung

Die folgenden Ansätze bieten Möglichkeiten, die Untersuchung weiter zu vertiefen und das Projekt technisch auszubauen.

Sie sind als potenzielle Erweiterungen zu verstehen und nicht als bereits vollständig umgesetzte Funktionen.

### 8.1 Vergleich modellspezifischer Fehlerprofile

Die Vorhersagefehler unterschiedlicher Modelle könnten systematisch für dieselben Einkommensgruppen und Regionen gegenübergestellt werden.

Damit ließe sich untersuchen, ob ein Modell zwar insgesamt ähnlich gut abschneidet, in bestimmten Teilgruppen jedoch deutlich zuverlässiger ist.

### 8.2 Modellbereitstellung und automatisierte Tests

Das trainierte Modell könnte mithilfe von `joblib` gespeichert und anschließend unabhängig vom Trainingsprozess geladen werden.

Ein automatisierter Smoke-Test könnte prüfen, ob:

- Das Modell erfolgreich geladen werden kann.
- Die erwarteten Eingangsmerkmale verarbeitet werden.
- Vorhersagen erzeugt werden.
- Die ausgegebenen Werte plausibel sind.

Dies wäre ein erster Schritt in Richtung einer wiederverwendbaren Modellbereitstellung.

### 8.3 Vorhersagen innerhalb einer Fehlertoleranz

Ergänzend zum durchschnittlichen absoluten Fehler könnte untersucht werden, welcher Anteil der Vorhersagen höchstens 50.000 US-Dollar vom tatsächlichen Median-Hauswert abweicht.

Diese Kennzahl könnte sowohl für den gesamten Testdatensatz als auch getrennt nach Regionen berechnet werden.

Sie wäre insbesondere für fachliche Anwender leichter interpretierbar als abstrakte Modellkennzahlen.

### 8.4 Räumlich getrennte Validierung

Die bisherige zufällige Aufteilung könnte um eine geografisch getrennte Validierung ergänzt werden.

Dazu würde ein bestimmtes Gebiet vollständig von den Trainingsdaten ausgeschlossen und anschließend als unabhängige Testregion verwendet.

So ließe sich untersuchen, wie gut das Modell auf geografisch unbekannte Gebiete übertragbar ist.

### 8.5 Weitere Machine-Learning-Verfahren

Ein weiterer möglicher Ansatz wäre der Vergleich mit zusätzlichen Regressionsverfahren, beispielsweise einem `RandomForestRegressor`.

Dabei könnten insbesondere die Vorhersagequalität, Modellkomplexität und Unterschiede in den regionalen Fehlerprofilen untersucht werden.

### 8.6 Modularisierung des Python-Codes

Wiederverwendbare Funktionen für Datenaufbereitung, Feature Engineering, Modelltraining und Evaluation könnten aus den Notebooks in eigenständige Python-Module ausgelagert werden.

Dadurch ließen sich Code-Duplikate reduzieren und die Wartbarkeit sowie Wiederverwendbarkeit verbessern.

## 9. Ergebnisse und Projektdokumentation

Das Projekt liefert einen nachvollziehbaren Vergleich verschiedener Regressionsansätze und eine differenzierte Analyse der Vorhersagezuverlässigkeit.

Als finales Modell wurde eine lineare Regression mit logarithmisch transformierten Merkmalen ausgewählt. Sie erreichte im Modellvergleich den niedrigsten durchschnittlichen Kreuzvalidierungs-MAE.

Die Fehleranalyse zeigt jedoch, dass die Vorhersagequalität zwischen Einkommensgruppen, gedeckelten Zielwerten und geografischen Regionen deutlich variiert.

Die Ergebnisse verdeutlichen damit eine zentrale Erkenntnis des Projekts:

**Eine gute durchschnittliche Modellkennzahl allein reicht nicht aus, um die Zuverlässigkeit eines Machine-Learning-Modells für einen konkreten Anwendungsfall zu beurteilen.**

Die vollständige technische Umsetzung und Auswertung befinden sich in den Jupyter-Notebooks dieses Repositories.

Weitere Dokumentation:

- [`README.md`](README.md) – Projektüberblick, Ergebnisse und Ausführung
- [`doku/PROBLEM_CANVAS.md`](doku/PROBLEM_CANVAS.md) – Fachliche Fragestellung und Erfolgskriterien
- [`doku/DATA_DICTIONARY.md`](doku/DATA_DICTIONARY.md) – Beschreibung der Datenmerkmale
- [`doku/DECISION_LOG.md`](doku/DECISION_LOG.md) – Technische Entscheidungen und Begründungen
- [`doku/MODEL_CARD.md`](doku/MODEL_CARD.md) – Modellbewertung und Einsatzgrenzen
- [`doku/AI_ASSISTANCE_LOG.md`](doku/AI_ASSISTANCE_LOG.md) – Dokumentation der KI-Unterstützung

---

*Dieses Projekt wurde zu Lern- und Demonstrationszwecken durchgeführt. Die Ergebnisse sind nicht für die Bewertung einzelner Immobilien oder die Bestimmung aktueller Marktpreise vorgesehen.*