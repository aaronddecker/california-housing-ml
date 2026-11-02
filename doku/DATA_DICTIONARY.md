# Data Dictionary

> Gate 2. Eine Zeile je Spalte. Trage Datentyp, Bedeutung, Einheit, Wertebereich (aus den Daten) und Rolle ein.
> Was du nicht sicher weißt, markierst du mit „?“ und klärst es. Ersetze jeden Platzhalter `{{…}}` durch deinen Text.

| Spalte | Datentyp | Bedeutung | Einheit | Wertebereich | Rolle (Merkmal / Ziel) |
| --- | --- | --- | --- | --- | --- |
| `MedInc` | float | Median-Einkommen der Haushalte | 10.000 US-Dollar pro Jahr | 0.4999 - 15.00 | Merkmal |
| `HouseAge` | float | Mittleres Alter der Häuser | Jahre | 1.0 - 52.0 | Merkmal | 
| `AveRooms` | float | Durchschnittliche Zimmerzahl pro Haushalt | Anzahl | 0.846 - 141.909 | Merkmal |
| `AveBedrms` | float | Durchschnittliche Schlafzimmerzahl pro Haushalt | Anzahl | 0.333 - 34.067 | Merkmal |
| `Population` | float | Einwohnerzahl der Blockgruppe | Personenzahl | 3.0 - 35682.0 | Merkmal |
| `AveOccup` | float | Durchschnittliche Haushaltsgröße | Personen pro Haushalt | 0.692 - 1243.333 | Merkmal |
| `Latitude` | float | Breitengrad | Grad | 32.54 - 41.95 | Merkmal |
| `Longitude` | float | Längengrad | Grad | -124.35 - -114.31 | Merkmal |
| `MedHouseVal` | float | Median-Hauswert der Blockgruppe | 100.000 US-Dollar | 0.150 - 5.000 | Ziel |


## Zielvariable
`MedHouseVal` ist das Ziel. Sie beschreibt den Median-Hauswert der Blockgruppe in der Einheit 100.000 US-Dollar.

## Hinweise
(Ausarbeitung: siehe 01_data_understanding.ipynb)
- `MedInc`: Scheint auf 15.0001 gedeckelt zu sein.
- `HouseAge`: Scheint auf 52.0 gedeckelt zu sein.
- `MedHouseVal`: Scheint auf 5.00001 gedeckelt zu sein.
- `Longitude` und `Latitude` stehen im Verhältnis und beschreiben die geografische Lage. Deswegen, kann z.B. die gleiche `Latitude` auch mehrfach vorkommen.
