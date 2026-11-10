# AI Assistance Log

> Laufend pflegen. Erlaubt ist KI als Arbeitsunterstützung: Recherche, Code erklären, Fehlersuche, Entwürfe.
> Nicht erlaubt: KI schreibt das Projekt ungeprüft, entscheidet Modellwahl oder Interpretation ohne deinen Nachweis, oder du gibst sensible Daten ein.
> Eine KI-Antwort ist keine Quelle. Ersetze jeden Platzhalter `{{…}}` durch deinen Text.

## Genutzte KI-Werkzeuge
Welche Werkzeuge hast du verwendet? Nenne Name und, wenn bekannt, die Version.
- ChatGPT (OpenAI, GPT-6)

## Einsatzzweck
Wofür hast du KI eingesetzt, zum Beispiel zum Erklären einer Fehlermeldung oder für einen ersten Code-Entwurf?
- Wir haben ChatGPT genutzt, um Python-Funktionen besser zu verstehen, Codeideen zu besprechen und Fragen zur Cross-Validation, Modellbewertung und Fehleranalyse zu klären. Außerdem haben wir uns bei der Formulierung unserer Ergebnisse und der Dokumentation unterstützen lassen.

## Beispielprompts (3 bis 5)
Schreib einige deiner Anfragen wörtlich ab, damit man sieht, wie du gefragt hast.
1. „Was macht agg bei pandas und wofür brauche ich lambda?“
2. „Was genau sind Residuen und was bedeutet es, wenn sie positiv oder negativ sind?“
3. „Wie kann ich untersuchen, ob das Modell in bestimmten Regionen größere Fehler macht?“

## Prüfmethoden
Wie hast du kontrolliert, ob die Antwort stimmt, zum Beispiel durch eigene Nachrechnung, Vergleich mit dem Kursmaterial, einen Test oder die Dokumentation?
- Wir haben den besprochenen Code in unseren Notebooks ausgeführt und die Ergebnisse überprüft. Bei der Modellwahl haben wir die berechneten MAE-Werte aus der Cross-Validation verglichen. Auch die Interpretationen haben wir anhand unserer Tabellen und Diagramme kontrolliert.

## Verworfene oder korrigierte Vorschläge
Welche Vorschläge hast du nicht übernommen oder geändert, und warum?
- Einige vorgeschlagene Interpretationen waren uns zu ausführlich. Deshalb haben wir sie gekürzt und auf Aussagen beschränkt, die sich mit unseren Ergebnissen belegen lassen. Die Modellwahl haben wir anhand unserer eigenen Berechnungen getroffen und dabei auch den geringen Unterschied zwischen LinearRegression (CV-MAE 0,4836) und DecisionTreeRegressor (CV-MAE 0,4864) berücksichtigt.

## Datenschutz und Quellen
Welche Daten hast du in das Werkzeug eingegeben? Wie hast du Aussagen zum Datensatz (Herkunft, Einheiten) belegt?
- Wir haben hauptsächlich Python-Code, berechnete Kennzahlen und Analyseergebnisse aus dem California-Housing-Datensatz eingegeben. Personenbezogene Daten waren dafür nicht notwendig. Die Herkunft des Datensatzes haben wir anhand der scikit-learn-Dokumentation und der ursprünglichen Veröffentlichung von Pace und Barry (1997) in unserer `DATASET_NOTICE.md` dokumentiert. ChatGPT haben wir nicht als Quelle verwendet.