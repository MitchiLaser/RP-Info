Auf einem der Micro-USB Ports stellt der RP eine virtuelle serielle Schnittstelle unter dem Benutzer `root` zur Verfügung. Mit dem Programm `Picocom` kann von einem PC aus einem Terminal heraus auf diese Schnittstelle zugegriffen werden:
```
$ picocom /dev/ttyUSB0 -b 115200
```
Die Sitzung kann durch Drücken von `CTRL + a` gefolgt von `CTRL + x` beendet werden. Während der Sitzung stehe eine `ash` Shell zur Verfügung.