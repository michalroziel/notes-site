
volatile keyword beschreiben können 
Vergleichsoperatoren kennen 

Wie Inhalt Register vertauschen ohne extra Register zu benutzen ? 

Programm Speicher :  Nur Lese Speicher 

align keyword 

PC- relative adressierung :
```
LDR R5,[PC,#offset]
```
DCD , DCW, DCB keywords 


Was ist das LR  - Link Register, und warum müssen wir es speichern ? 
Warum Speichern wir uns auf dem Stack die RücksprungAdresse ?
	Wenn wir vom unterprogramm ein neues unterprogramm aufrufen, vergessen wir nicht wohin wir am ende wieder springen müssen 

	
Was ist die ISR ? - Warum brauchen wir diese ? 

## Condition Flags mit und ohne Vorzeichen !



```
RSB <Rd>, <Rn>, <Operand2>
Rd = Operand2 - Rn


REGULAR SUB : 
Rd = Rn - Operand2

```
1. Wann wird die N Flag bei MOVS R10 R10 gesetzt ? 
2. Welches Register ist das Link Register ? -> R14
3. Wie ruft man das Unterprogramm _Unterprogramm_ auf ? -> BL Unterprogramm
4. Wo ist die Adresse gespeichert zu der man nach Abschluss des Unterprogramms zurück springt -> LR
5. RSC R1, R2, R3 -> R1 = R3 - R2 - NOT(C)
6. ADDS R3, R9, R9 , LSLio#3 -> Ergebnis 9-Fache von R9
7. Was bedeutet die Anweisung Zahl EQU 0x50000100 -> PSeudo Anweisung...
8. ORRS mit ASR  


SUB R1, R2, R3  -> R1 = R2 - R3 

RSB R1, R2, R3 -> R1 = R3 - R2 


RSC R1, R2, R3 -> R1 = R3 - R2 - NOT(C)





