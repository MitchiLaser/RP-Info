Das FPGA kann mit der Software Vivado von AMD (ehemals Xilinx) programmiert werden. Dabei ist es wichtig, das die richtige Version von Vivado für das Erstellen eines Projektes verwendet wird! Andernfalls ist es eventuell nicht möglich, die Projekt-Dateien zu öffnen.

Die RP Beispiel-Projekte sowie der fertige Bitstream für die RP Anwendungen wurden mit Vivado Version `2020.1` erstellt. Die Projekte von Pavel wurden mit Version `2020.2` erstellt. Leider ist es nicht ohne großen Aufwand möglich, beides mit einer gemeinsamen Vivado Version zu öffnen.

## Bitstream in das FPGA laden

Um eine `.bit` Datei auf das FPGA hochzuladen, muss der Inhalt in das entsprechende Block-Device geschrieben werden:
```
$ cat bitstream.bit > /dev/xdevcfg
```

## Debugging: Memory Access
Das FPGA und der ARM Prozessor teilen sich einen gemeinsamen Speicher. Für Debugging Zwecke könne die Xilinx System Debugger Kommandos verwendet werden um vorgegebene Werte an Speicherstellen zu schreiben oder um Werte aus Speicherstellen auszulesen:
```
mwr 0x00100000 0x00011111 #Write data to address, 0x00100000
mrd 0x00100000 #Read data at address, 0x00100000
```
