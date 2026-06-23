# Programm zur Auswertung der Temperatur und PUE

 

*Dieses Programm ist Bestandteil der wissenschaftlichen Arbeit:*

„Reduktion der Power Usage Effectiveness ($\text{PUE}$) zur Erfüllung des Energieeffizienzgesetzes (EnEfG): Potenzial der direkten freien Kühlung im erweiterten ASHRAE-Bereich für Nürnberger Rechenzentren“

 

## Beschreibung

Mithilfe des Programms können xlsx-Dateien des Deutschen Wetterdienstes (DWD) nach ihrer Temperatur und ihrer PUE analysiert und ausgewertet werden.

Der $\text{PUE}$ wird dabei nach folgender Formel berechnet:

$$\widetilde{\text{PUE}} = \text{PUE} + \frac{\chi_{\text{Kühlung}}}{\chi_{\text{IT-Geräte}}} \cdot \left(\frac{\text{t}_{\text{freie Kühlung}} \cdot \epsilon + \text{t}_{\text{mech. Kühlung}}}{\text{t}_{\text{ganzes Jahr}}} – 1 \right)$$

Die Berechnung ist eine Vereinfachung für die Bestimmung des $\text{PUE}$ bei Umstellung von mechanischer Kühlung zu direkter freier Kühlung.
Die Auswertung soll bei der Analyse unterstützen, wie effektiv der Standort geeignet ist den $\text{PUE}$ zu senken.


## Installation

Eine Installation ist nicht erforderlich, wenn Excel bereits vorhanden ist. Es genügt, wenn die xlsm-Datei heruntergeladen wird und die Ausführung von Makros möglich ist.

Damit das Programm die Datengrundlage (die Wetterdaten für den zu untersuchenden Standort) einlesen kann, muss sich die Datei im selben Verzeichnis wie das Programm befinden.

 

## Beispiel

Beim Öffnen sind bereits die Werte für den Standort Nürnberg Flughafen eingelesen.

Die Testdatei steht ebenfalls auf Github („Taupunkte Nürnberg Flughafen ab 1999.xlsx“) zur Verfügung.

 

## Anwendung

1. Wählen Sie auf dem Tabellenblatt "Programm" über das Dropdown-Menü die zu untersuchende Wetterdatei (.xlsx) als Datengrundlage aus.

2. Der Auswertungszeitraum wird automatisch vorbelegt, kann jedoch manuell angepasst werden.

     > *Achtung:* Aktuell findet noch keine automatisierte Prüfung statt, ob der gewählte Zeitraum vollständig in den Wetterdaten vorhanden ist. Bitte wählen Sie daher nur Zeiträume aus, die nachweislich komplett in der Datengrundlage enthalten sind!

3. Nach dem Klick auf den Button "Auswerten" werden die Tabellenblätter "Auswertung_Zeit" und "Auswertung_PUE" auf Basis der neuen Datengrundlage und des ausgewählten Zeitraums aktualisiert.
 

## Auswertung

**Tabellenblatt "Auswertung_Zeit“**

* **Das erste Diagramm** zeigt den prozentualen Verlauf der Stunden (Y-Achse) über dem ausgewählten Zeitraum (X-Achse). *(Für Nürnberg Flughafen: deutliche Schwankungen sind sichtbar und tendenzielle Steigerung der Werte)*

*  **Das zweite Diagramm** zeigt den prozentualen Verlauf der Stunden (Y-Achse) im Verhältnis zur Temperatur (X-Achse). *(Für Nürnberg Flughafen: starker Abfall der Werte bei steigender Temperatur. Die Fehlerbalken werden bei steigender Temperatur immer geringer)*

* **Erste Tabelle:** Zeigt die prozentuale Entwicklung der Stunden auf Jahre und Temperatur. Sie bildet die Grundlage für die Diagramme. Der Durchschnitt und die Standardabweichung wurden je Temperaturschritt berechnet.

*  **Zweite Tabelle:** Zeigt die Stundenanzahl, welche die jeweilige Temperatur im Jahr überschreitet. Es wird je Temperaturschritt ein Mittelwert und die Standardabweichung berechnet.

*  **Dritte Tabelle:** Zeigt die Stundenanzahl, welche die jeweilige Temperatur im Jahr unterschreitet. Es wird je Temperaturschritt ein Mittelwert und die Standardabweichung berechnet.

(Tabelle 2 und Tabelle 3 können zu einem einfachen Abgleich dienen, ob das Programm auch die richtige Stundenzahl in Summe ermittelt hat. Sie bilden die Grundlage für Tabelle 1.)

 

**Tabellenblatt "Auswertung_PUE“**

Die Formel, welche zur Auswertung benutzt wird, ist nochmal angegeben.

Eine Herleitung befindet sich im Paper.

Zusätzlich zu den Wetterdaten können noch weitere Einstellungen vorgenommen werden:

$\text{PUE}$., $\epsilon$, $\Delta \epsilon$, $\chi_{\text{IT-Geräte}}$ und $\chi_{\text{Kühlung}}$. Bei Änderungen der Werte erfolgt eine automatische Aktualisierung der Tabelle und des Diagramms.

 

> *Anmerkung*: Die Werte 𝜀 und ∆𝜀 wurden entsprechend der Literatur gewählt. $\chi_{\text{IT-Geräte}}$ richtet sich nach dem ausgewählten $\text{PUE}$. D.h. es gilt $\chi_{\text{IT-Geräte}} = \frac{1}{\text{PUE}}$.

> Normalerweise müssen deshalb nur die $\text{PUE}$ und $\chi_{\text{Kühlung}}$. angepasst werden.

 

**Das Diagramm** zeigt in Orange den $\text{PUE}$ von mechanischen Kältemaschinen. Der Wert ist konstant, da eine Ceteris-paribus-Annahme getroffen wurde. Die zwei blauen und die graue Funktion sind die Verläufe der $\text{PUE}$.  bei direkter freier Kühlung mit $\epsilon$ (dunkelblau), $\epsilon + \Delta \epsilon$ (Grau) und $\epsilon - \Delta \epsilon$ (hellblau).
  *(Für Nürnberg Flughafen: Alle drei Funktionen unterschreiten den kritischen PUE von 1,2, der bei Neubauten gilt.)*

**Die Tabelle** zeigt in der zweiten und dritten Spalte die Durchschnitte der Stunden über und unter der Zieltemperatur (entsprechend dem Tabellenblatt „Auswertung_Zeit“. $\lambda$ steht in der vierten Spalte und ist definiert als:

$$\lambda = \frac{\text{t}_{\text{freie Kühlung}}\cdot\epsilon+\text{t}_{\text{mech. Kühlung}}}{\text{t}_{\text{ganzes Jahr}}}$$

In der fünften Spalte steht der $\widetilde{\text{PUE}}$ für $\epsilon$, in der sechsten für $+ \Delta \epsilon$ und in der siebten für $- \Delta \epsilon$.
