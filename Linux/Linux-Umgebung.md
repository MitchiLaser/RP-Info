Über eine [Serielle Konsole](Serielle%20Konsole.md), die an einem der Micro-USB Ports verfügbar ist, kann mit Root Rechten auf das Betriebssystem zugegriffen werden.

## Einrichten der SD-Karte mit dem offiziellen RP OS Image
Siehe [RP Wiki Eintrag](https://redpitaya.readthedocs.io/en/latest/quickStart/SDcard/SDcard.html)

Mit `dd` kann das Image auf die SD-Karte geschrieben werden.
```
$ sudo dd bs=4M if=redpitaya_os.img of=/dev/mmcblk0p1
```
Dabei müssen das richtige image `if=` und das richtige Block-Device für die SD-Karte `of=` ausgewählt werden.

## Einrichten von Pavels Image
Siehe [Webseite von Pavel](https://pavel-demin.github.io/red-pitaya-notes/alpine/)
