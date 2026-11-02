# htw_seminar3_jupyter

## Wetteranalyse Berlin

### Vorgehen

Die Analyse verwendet tägliche Messwerte der DWD-Station Berlin-Dahlem (FU, Stations-ID 00403) vom 1. Januar 2020 bis zum letzten verfügbaren Messdatum, dem 1. November 2026. Die CSV enthält Tagesminimum, Tagesmaximum und Tagesmitteltemperatur, Niederschlagsmenge sowie Sonnenscheindauer. Fehlende Messwerte bleiben leer.

Nach dem Laden der CSV werden Datenabdeckung und Kennzahlen geprüft. Temperaturverläufe, monatliche Niederschlagssummen und Sonnenscheindauer werden visualisiert. Für den Jahresvergleich wird je Kalendertag die Spannweite zwischen dem wärmsten und kältesten Jahr berechnet; verwendet werden dafür die vollständigen Jahre 2020 bis 2025. Das unvollständige Jahr 2026 bleibt außen vor.

Zusätzlich schätzt ein Random-Forest-Modell die Tagesmitteltemperatur einen Tag voraus. Als Eingaben dienen die Mitteltemperaturen der fünf vorhergehenden Tage und der Kalendertag. Trainiert wird chronologisch mit 2020 bis 2024, getestet mit 2025. Die Testwerte werden außerdem mit einer einfachen Vortagsprognose verglichen.

### Kernergebnisse

- Für 2.481 von 2.497 Tagen liegen Tagesminimum, Tagesmaximum, Tagesmitteltemperatur und Sonnenscheindauer vor; Niederschlagswerte gibt es für 2.482 Tage.
- Die mittlere tägliche Temperaturspannweite zwischen den Jahren beträgt im Winter (Dezember bis Februar) 10,05 °C, im Sommer (Juni bis August) 7,15 °C. Der Winterwert ist damit rund 41 % größer.
- Im Testjahr 2025 erreicht der Random Forest einen mittleren absoluten Fehler (MAE) von 1,67 °C und einen RMSE von 2,12 °C. Die Vortags-Baseline liegt bei 1,76 °C MAE und 2,26 °C RMSE.
- Mit den bis zum 1. November 2026 verfügbaren Daten ergibt das Modell für den 2. November 2026 eine Tagesmitteltemperatur von 8,9 °C.

Die Prognose ist ein einfacher Ein-Tages-Schätzwert ohne Prognoseintervall und berücksichtigt außer den letzten fünf Temperaturen und der Jahreszeit keine weiteren Wetterfaktoren. Die DWD-Werte stammen von einer einzelnen Station und beschreiben daher nicht jede Lage in Berlin.

