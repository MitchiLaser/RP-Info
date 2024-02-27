Die Platine verfügt über folgende I/O Ausstattung:
- 2 High-Speed [Analoge Eingänge](ADC)
- 2 High-Speed [Analoge Ausgänge](DAC)
- 10 / 100 / 1000 MBit Ethernet
- Micro-USB Stromversorgung
- Micro-USB Serielle Konsole
- USB Host
- Micro SD-Karten Slot
- GPIO Pins mit langsamen ADCs, DACs und sonstigen Verbindungen
- 2 SATA Anschlüsse verwendet werden können um die Clock von mehreren Red Pitayas zu verbinden. Damit können mehrere Geräte zusammen geclustert werden.
- Das Herzstück der Platine bildet ein [Xilinx Zynq SoX](FPGA-Chip)

Link zum Schaltplan: [https://downloads.redpitaya.com/doc/Red_Pitaya_Schematics_v1.0.1.pdf](https://downloads.redpitaya.com/doc/Red_Pitaya_Schematics_v1.0.1.pdf)

Block-Diagramm der Ansteuerung der analogen Ein- und Ausgänge:
![Image](https://assets.koheron.com/images/blog/2016-11-29-red-pitaya-cluster/pll_adc_dac.png?02022024140356)

