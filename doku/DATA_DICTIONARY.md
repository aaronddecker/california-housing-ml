# Data Dictionary

| Spalte | Datentyp | Bedeutung | Einheit | Wertebereich | Rolle (Merkmal / Ziel) |
| --- | --- | --- | --- | --- | --- |
| `MedInc` | float64 | Median-Einkommen der Haushalte | 10.000 US-Dollar | 0.4999 - 15.00 | Merkmal |
| `HouseAge` | float64 | Mittleres Alter der Häuser | Jahre | 1.0 - 52.0 | Merkmal | 
| `AveRooms` | float64 | Durchschnittliche Zimmerzahl pro Haushalt | Anzahl | 0.846 - 141.909 | Merkmal |
| `AveBedrms` | float64 | Durchschnittliche Schlafzimmerzahl pro Haushalt | Anzahl | 0.333 - 34.067 | Merkmal |
| `Population` | float64 | Einwohnerzahl der Blockgruppe | Personenzahl | 3.0 - 35682.0 | Merkmal |
| `AveOccup` | float64 | Durchschnittliche Haushaltsgröße | Personen pro Haushalt | 0.692 - 1243.333 | Merkmal |
| `Latitude` | float64 | Breitengrad | Grad | 32.54 - 41.95 | Merkmal |
| `Longitude` | float64 | Längengrad | Grad | -124.35 - -114.31 | Merkmal |
| `MedHouseVal` | float64 | Median-Hauswert der Blockgruppe | 100.000 US-Dollar | 0.14999 – 5.00001 | Ziel |


## Zielvariable
`MedHouseVal` ist das Ziel. Sie beschreibt den Median-Hauswert der Blockgruppe in der Einheit 100.000 US-Dollar.

## Hinweise
Die Datenanalyse ist in `notebooks/01_data_understanding.ipynb` dokumentiert.

- `MedInc`: Der Wertebereich ist nach oben begrenzt (maximal 15.0001).
- `HouseAge`: Das Gebäudealter ist bei 52 Jahren gedeckelt.
- `MedHouseVal`: Der Zielwert ist bei 5.00001 (entspricht etwa 500.001 US-Dollar) gedeckelt.
- `Latitude` und `Longitude`: Die Koordinaten beschreiben die geografische Lage der Blockgruppen. Einzelne Koordinatenwerte können mehrfach vorkommen, da erst ihre Kombination eine geografische Position beschreibt.
