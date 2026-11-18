# AI Assistance Log
Dieses Dokument beschreibt den Einsatz von KI-Werkzeugen während der Projektarbeit sowie die eigenständige Überprüfung und Bewertung der unterstützend erzeugten Inhalte.

## Genutzte KI-Werkzeuge
- ChatGPT (OpenAI, GPT-6)

## Einsatzzweck
- Wir haben ChatGPT genutzt, um Python-Funktionen besser zu verstehen, Codeideen zu besprechen und Fragen zur Cross-Validation, Modellbewertung und Fehleranalyse zu klären. Außerdem haben wir uns bei der Formulierung unserer Ergebnisse und der Dokumentation unterstützen lassen.

## Beispielprompts (3 bis 5)
1. „Was macht agg bei pandas und wofür brauche ich lambda?“
2. „Was genau sind Residuen und was bedeutet es, wenn sie positiv oder negativ sind?“
3. „Wie kann ich untersuchen, ob das Modell in bestimmten Regionen größere Fehler macht?“

## Prüfmethoden
- Wir haben den besprochenen Code in unseren Notebooks ausgeführt und die Ergebnisse überprüft. Bei der Modellwahl haben wir die berechneten MAE-Werte aus der Cross-Validation verglichen. Auch die Interpretationen haben wir anhand unserer Tabellen und Diagramme kontrolliert.

## Verworfene oder korrigierte Vorschläge
- Einige vorgeschlagene Interpretationen waren uns zu ausführlich. Deshalb haben wir sie gekürzt und auf Aussagen beschränkt, die sich mit unseren Ergebnissen belegen lassen. Die Modellwahl haben wir anhand unserer eigenen Berechnungen getroffen und dabei auch den geringen Unterschied zwischen LinearRegression (CV-MAE 0,4836) und DecisionTreeRegressor (CV-MAE 0,4864) berücksichtigt.

## Datenschutz und Quellen
- Wir haben hauptsächlich Python-Code, berechnete Kennzahlen und Analyseergebnisse aus dem California-Housing-Datensatz eingegeben. Personenbezogene Daten waren dafür nicht notwendig. Die Herkunft des Datensatzes haben wir anhand der scikit-learn-Dokumentation und der ursprünglichen Veröffentlichung von Pace und Barry (1997) in unserer `DATASET_NOTICE.md` dokumentiert. ChatGPT haben wir nicht als Quelle verwendet.