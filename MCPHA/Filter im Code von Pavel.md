
Pavel verwendet einen CIC Filter und einen FIR Filter. Der CIC Filter realisiert den Decimation Faktor.

Was der FIR Filter macht ist nicht klar, seine Übergangsfunktion ist über hardkodierte Stützstellen definiert. Sehr wahrscheinlich handelt es sich dabei um einen Convolution Filter, der die Gaussförmigen Pulse erkennen soll. Ein Plot der Funktion die diese Stützstellen darstellen ist hier zu sehen, die Achsenbeschriftung bezieht sich auf die Floating-Point Werte aus dem Code und die Index-Nummer der Stützstelle: ![[Stützstellen_FIR_Filter.png]]
Quelle der Stützstellen: Datei `red-pitaya-notes/projects/mcpha/block_design.tcl`

Informationen über den [CIC Filter](https://docs.amd.com/v/u/en-US/pg140-cic-compiler)
Informationen über den [FIR Filter](https://www.xilinx.com/support/documents/ip_documentation/fir_compiler/v7_2/pg149-fir-compiler.pdf)
