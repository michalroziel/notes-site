[[ARM7]]
### Definition von Symbolen mit EQU ( Equate)
Mit der Pseudo Anweisung EQU kann man einen symbolischen namen definieren und ihm einen Wert zuweisen. Innerhalb eines Moduls ist solch eine Zuweisung nicht veränderbar.

#### Beispiele : 
TRUE           EQU   0x0FF
Max_Wert    EQU 0x4711
Anzahl          EQU 5 

#### Initialisierung von Speicherinhalten ( Verwendung von Programm speicher)
*DCB*     Legt im Speicher eine oder mehrere Byte-Werte ( 8-Bit ) ab
*DCW*    Legt im SPeicher eine oder mehrere Halbwort- Werte ( 16-Bit) ab.
*DCD*     Legt im Speicher einen oder mehrere Wort-Werte (32-Bit Werte) ab.





