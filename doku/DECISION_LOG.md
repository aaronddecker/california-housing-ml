# Decision Log

> Laufend pflegen, nicht erst am Ende. Halte Entscheidungen, verworfene Alternativen und die Begründung fest.
> Gute Kandidaten: Umgang mit gedeckelten Zielwerten, Umgang mit Ausreißern, Merkmalsauswahl, Transformationen, Split-Strategie, Modellwahl, Metrik, Regionen für die Fehleranalyse.

| Datum | Entscheidung | Alternativen | Begründung (mit Zahl oder Beleg) | Wer |
|---|---|---|---|---|
| 03.11.2026 | Gedeckelte Werte werden zunächst behalten und später getrennt ausgewertet. | Entfernen aller Ausreißer oder pauschales Begrenzen extremer Werte. | Die auffälligen Werte sind nicht automatisch fehlerhaft und können reale Besonderheiten der Wohngebiete darstellen. | Projektteam |
| 05.11.2026 | Zunächst `DecisionTreeRegressor` mit `max_depth=6` als bevorzugtes zweites Modell gewählt. | `DummyRegressor`, `LinearRegression` | Niedrigster MAE bei 5-facher Cross-Validation auf Rohmerkmalen: 0,4864 gegenüber 0,5291 bei LinearRegression. | Projektteam |
| 05.11.2026 | Log-Transformation von `AveRooms`, `AveBedrms`, `Population` und `AveOccup`. | Rohmerkmale unverändert verwenden. | Starke Rechtsschiefe der vier Merkmale (5,28 bis 88,05). Die Log-Transformation reduziert die Schiefe und verbessert den CV-MAE der LinearRegression von 0,5291 auf 0,4836. | Projektteam |
| 05.11.2026 | `LinearRegression` mit Log-Merkmalen für die Schlussbewertung ausgewählt. | DummyRegressor und DecisionTreeRegressor, jeweils mit Roh- und Log-Merkmalen. | Niedrigster CV-MAE: 0,4836 (Std. 0,0077). Der DecisionTree erreicht mit Rohmerkmalen 0,4864. Der geringe Unterschied zeigt keine eindeutige Überlegenheit. | Projektteam |