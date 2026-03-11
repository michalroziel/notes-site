[[ARM7]]
## Beispiel eines einfachen Programms 

```
AREA PROG1, CODE, READONLY
ENTRY 

MOV R0, #0x11       ; load initial value into Register R0 
MOV R1, R0, LSL #1  ; shift by 1 bit left 
MOV R2, R1, LSL #1  ; shift by 1 bit left 


stop   B   stop     ; stop program 

END 
```
Damit der [[ARM7]] Assembler einen Code Block erstellt, brauchen wir eine *AREA* Declaration. , *CODE* gibt uns die Art der Daten an, Hierbei : *Instruktionen*
Wir deklarieren diesen Part von dem Code als Read-only. 
Da Jedes Programm eine ENTRY Deklaration benötigt, schreiben wir diesen danach. 


## EIn weiteres einfaches Programm wäre [[Factorial Calculation]]




Der Assembler übersetzt die Quelldateien und erzeugt dabei einen sogenannten object file 
Der Linker verbindet diese Dateien

	Der Locator passt das Programm an den vorhandenen Speicher des Prozessors an 

Meistens ist der Link und Lcoator zusammengefasst 

JTech ist eine genormte Schnittstelle um vom PC aus Software auf den verbundenen Prozessor zu schreiben 

