Der RP ist mit 2 analogen Ausgängen ausgestattet:
- Auflösung: 14 Bits
- Ausgangsspannung: $\pm{}\pu{1 V}$
- Samplingrate: $\pu{125 MSps}$ Voll-Dublex
Beide analogen Ausgänge werden von einem DAC Chip betrieben: [AD9767](http://www.analog.com/media/en/technical-documentation/data-sheets/AD9763_9765_9767.pdf) (Quelle: [Mouser Webseite Beschreibung](https://www.mouser.de/c/n/embedded-solutions/?m=Red%20Pitaya)). Dieser Chip hat zwei analoge Ausgänge und wird über einen 14 Bit breiten parallelen Bus gesteuert. Der Chip kann in 2 Modi betrieben werden:
1. Parallel mode: Beide Ausgänge werden parallel zueinander betrieben und haben ihre eigene parallele Schnittstelle. Sie teile sich eine gemeinsame Clock.
2. Interlieived mode: Beide analoge Ausgänge teilen sich eine parallele Schnittstelle (in diesem Fall die Schnittstelle für Ausgang A). Beide Ausgänge werden nacheinander angesprochen. Dafür wird die Clock doppelt so schnell betrieben
Beim RP STL 125-14 wird der DAC im interlieved Modus mit einer 250MHz Clock betrieben. Höchstwahrscheinlich ist das die maximale Frequenz mit der der FPGA Chip betrieben werden kann.

## DAC Performance Probleme durch Rauschen

Der folgende [Blog-Eintrag](https://ln1985blog.wordpress.com/2016/02/07/red-pitaya-dac-performance/) beschreibt ein Problem wodurch einige Bits vom DAC wegen zu hohem Rauschen nicht verwendet werden können. Der DAC erzeugt eine Ausgangsspannung im Bereich von $\pu{0 V}$ bis $\pu{2 V}$, welche nachträglich um $\pu{1 V}$ nach unten verschoben wird. Die $\pu{1 V}$ Referenz-Spannung wird über einen Spannungsteiler von der $\pu{3,3 V}$ Spannungsversorgung bezogen. Leider ist die $\pu{3,3 V}$ Versorgungsspannung nicht gut genug geglättet und schwankt während GPIO-Pins vom FPGA ein und ausgeschaltet werden. Der DAC wird ebenfalls über GPIO Pins angesprochen, was dazu führt, dass während der Benutzung des DAC die $\pu{1 V}$ Referenzspannung schwankt. Die "Effective Number of Bits" liegt bei ca. $\pu{10 Bits}$ wenn nur der DAC betrieben wird und bei $\pu{8 Bits}$ wenn andere Komponenten (ADC, LEDs auf dem Board) mitbenutzt werden.

Mögliche Lösungen:
- Während der DAC in Betrieb ist keine anderen Komponenten auf dem Board verwenden: ADCs und Onboard-LEDs ausgeschaltet lassen
- Wie im Blog-Eintrag beschrieben: Die zwei Widerstände vom Spannungsteiler entfernen. Das verschiebt den Wertebereich der Ausgangsspannung aber auf $\pu{0 V}$ bis $\pu{2 V}$.
Die Low-Noise Variante des RP hat dieses Problem gelöst (Vermutung: Verwendung eines Linearreglers zum Erzeugen einer stabileren Referenzspannung).