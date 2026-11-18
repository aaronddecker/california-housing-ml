# Model Card

## Zweck

Das Modell wurde im Rahmen einer Machine-Learning-Projektsimulation entwickelt. Es schätzt den Median-Hauswert kalifornischer Zensus-Blockgruppen anhand sozioökonomischer, demografischer und geografischer Merkmale.

Die fiktive Planungsabteilung einer Regionalverwaltung soll damit Wohngebiete grob einschätzen können. Zusätzlich zeigt die Fehleranalyse, in welchen Gruppen und Regionen die Schätzungen besonders unzuverlässig sind.

Das Modell ist nicht für die Bewertung einzelner Immobilien vorgesehen.

## Daten

- **Datensatz:** California Housing (scikit-learn)
- **Datenstand:** US-Zensus von 1990
- **Umfang:** 20.640 Blockgruppen
- **Eingangsmerkmale:** 8 numerische Merkmale
- **Zielvariable:** `MedHouseVal` – Median-Hauswert in Einheiten von 100.000 US-Dollar
- **Trainingsdaten:** 16.512 Beobachtungen (80 %)
- **Testdaten:** 4.128 Beobachtungen (20 %)
- **Aufteilung:** Zufälliger Train-Test-Split mit `random_state=42`

Die Eingangsmerkmale umfassen Einkommen, Gebäudealter, durchschnittliche Zimmer- und Schlafzimmerzahlen, Bevölkerung, durchschnittliche Haushaltsbelegung sowie geografische Koordinaten.

## Modell und Kennzahlen

Als finales Modell wurde eine `LinearRegression` mit Log-Transformation ausgewählter Merkmale verwendet.

Die Merkmale `AveRooms`, `AveBedrms`, `Population` und `AveOccup` wurden aufgrund ihrer starken Rechtsschiefe logarithmisch transformiert.

### Modellvergleich

Die Modelle wurden anhand einer 5-Fold-Cross-Validation auf den Trainingsdaten verglichen.

| Modell | CV-MAE | Fehler in USD (ca.) |
|---|---:|---:|
| DummyRegressor (Baseline) | 0,9139 | 91.390 $ |
| LinearRegression (Rohmerkmale) | 0,5291 | 52.910 $ |
| DecisionTreeRegressor (`max_depth=6`) | 0,4864 | 48.640 $ |
| **LinearRegression (Log-Transformation)** | **0,4836** | **48.360 $** |

Die LinearRegression mit Log-Transformation erreichte den niedrigsten CV-MAE. Der Unterschied zum DecisionTreeRegressor ist allerdings gering und belegt keine eindeutige Überlegenheit.

Die Werte dieser Tabelle stammen aus der Kreuzvalidierung auf den Trainingsdaten und sind keine abschließenden Testkennzahlen.

## Einsatzgrenzen

Die Fehleranalyse auf den Testdaten zeigt deutliche Unterschiede zwischen verschiedenen Gruppen.

| Auswertungsgruppe | MAE | Fehler in USD (ca.) |
|---|---:|---:|
| Niedrige Einkommensgruppe | 0,4110 | 41.100 $ |
| Hohe Einkommensgruppe | 0,5589 | 55.890 $ |
| Gedeckelte Zielwerte | 1,3522 | 135.220 $ |
| Nicht gedeckelte Zielwerte | 0,4513 | 45.130 $ |
| San Francisco Bay Area | 0,5495 | 54.950 $ |
| Los Angeles | 0,4906 | 49.060 $ |
| Central Valley | 0,4369 | 43.690 $ |

Die Ergebnisse zeigen, dass die Schätzungen insbesondere bei hohen Hauswerten und in bestimmten Regionen größere Fehler aufweisen.

Das Modell kann für grobe statistische Einschätzungen verwendet werden. Für Entscheidungen, die eine hohe Genauigkeit erfordern, ist es nicht ausreichend zuverlässig.

## Bekannte Schwächen

- **Historischer Datenstand:** Die Daten stammen aus dem Jahr 1990 und bilden keine aktuellen Immobilienpreise ab.
- **Gedeckelte Zielvariable:** Hauswerte oberhalb von etwa 500.001 US-Dollar können durch die Zielvariable nicht vollständig abgebildet werden.
- **Unterschiedliche Fehler nach Einkommen:** In höheren Einkommensgruppen treten größere absolute Vorhersagefehler auf.
- **Regionale Unterschiede:** Die Modellqualität variiert zwischen den untersuchten Regionen.
- **Vereinfachte Regionsdefinition:** Die regionalen Auswertungen basieren auf Koordinatenbereichen und decken nicht ganz Kalifornien ab.
- **Keine Einzelimmobilienbewertung:** Das Modell schätzt Median-Hauswerte von Blockgruppen und keine Preise einzelner Häuser.
- **Keine Kausalität:** Aus den Vorhersagen lassen sich keine ursächlichen Zusammenhänge ableiten.