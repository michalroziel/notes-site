[[ARM7]]
# 4.1 Datenmanipulationsbefehle 

Die grün hinterlegden befehle sind vergleichsbefehle -> ändern nur die statusbits 
BLAU : keinen operand 1 
ROT : Klassisch logisch-arithmetischen befehle 

4 Bits : 16 BEfehle 
$rd : destination register 

sbz : should be zero
sbo : should be ones 

operand 2 kann register, immediate constante, shift sein 

#20 sbit : ...

#25 I bit : ...

## 4.1.1 Arithmetik- und Logikbefehle


```
Befehl{Bedingung}{S}      Rd,Rn, operand2
```


# -> # = Teppich 


# 4.1.2 Kopierbefehle 

MOv -> MOVE , MVN -> MOVE NOT 
	Hierbei können wir mit MVN auch -1 in ein Register reinladen 


# 4.1.3 Vergleichs- und Testbefehle 


# 4.1.4 Bit-Manipulationen 

Wir können bits setzten, löschen oder auch togglen 
Auch mehrere BIts auf einmal : Mit einer Bit Maske 


>[! Ein CMP auf 0 ist meistens nicht notwendig]


# 4.2 Multiplikationstabelle 


##### Prinzip der Kurzschlussauswertung
vergleiche skript seite 86 Beispiel #073
!! Wenn jemand verlangt, dass wir mehrere Sachen prüfen 


### Klausur  : kombinieren
zb : ladebefehl auch mit Modifiezierungsbefehl kombinieren können : nicht auswendig lernen 


### Ergebnis Multiplikation 
Das Ergebnis der Multiplikation kann entweder 32 oder 64 Bit sein 

Oberste 4 Bits : condition 

#### Wichtig :
Bei Multiplikation ausschließlich Registeradressierung 
Bei shift: nur multiplikation mit 2-Potenzen, oder 2^n -1

```
MOV R1, R1, #4 

ADD R1, R1, R1, LSL #4     R1 <- R1 + R1 * 2^4 = 17*R1

SUB R1, R1, LSL #4         R1 <- R1-R1 * 2^4   = -15 * R1

RSB R1, R1, R1, [x, L2??]    R1 <- R1 * 2^4 - R1 = 15 * R1 
(REVERSE SUBTRACTION)
```

 Bei mulitply( 64 Bit result ) und MAC ( 64 Bit Result ) : 
 U-Bit gibt an ob signed oder unsigned Interpretation 

WICHTIG : Erstmal Werte in Register laden, danach Multiplizieren 

```
	MVN R2, 0x02  -> Lade -3 in Register ( entspricht 0xFFFFFFFD)
```

```
MOV R2, #0x20000 ; R2 ← 131 072
MOV R3, #0x8000 ; R3 ← 32 768
MUL R1, R2, R3 ; R1 ← R2·R3
Hierbei Ergebnis falsch ! 
```

```
MOV R3, #0x20000 ; R3 ← 131 072
MOV R4, #0x8000 ; R4 ← 32 768
UMULL R1, R2, R3, R4


Das Ergebnis in R1 (low) bzw. R2 (high) ist gleich 0x00000000bzw. 0x00000001.
```

> Immer beachten ob wir mit negativen Zahl multiplizieren ! 
> 	Dann müssen wir signed multiplication verwenden ! 

Eigentlich machen wir keine 32 Bit * 32 Bit, sondern 32 Bit * 8 Bit und das 4 mal

Early Termination  : Bestimmte Anzahl von Zyklen 
kann sein n+1 oder n+4 ( oder was dazwischen )


### [[Mikro Klausur]]
	Multiplizieren mit 15 oder 17 nicht mit MUL
	sondern wie oben, mit ADD, SUB, RSB.. etc...
	Dies ist somit schneller 


# 4.3 Sprungbefehle 
Dont repeat yourself : verwende UNTERPROGRAMME ! 
	auch gerne mehr als eins benutzen 

Embedded Bereich : C17 Standard mit Templates, C20 erleichtert Programmierung mit Concepts 

	Branch exchange
	Branch  -> wir brauchen nur den 

	Branch : relativer Sprung 

Chiptuning  im Motor : Austausch von Tabellen im Bordcomputer 

> Der PC ist um den WERT 8 !!! größer als unser Befehl 
> Wir möchten die nächsten 20 Befehle überspringen : nicht 10 addieren, sondern 12, PC ist bereits 8 weitergezählt 
> ABER : DIESE ZWEI BEFEHLE NUR GELADEN, NICHT AUSGEFÜHRT ! 


### Branches
```
B { Bedingung } Label ⟨S10⟩
```

```
CMP R1, #0x10        ; R1 mit 0x10 vergleichen
BEQ val_ok             ; Wenn gleich, dann Sprung zu val_ok 

B           ; Endlos-Schleife, d.h.
            ; Sprung auf sich selbst
val_ok:
ADD R1, R2, R3 ; R1 ←R2 + R3
```

	Poor mans Branch 
```
ADD PC, PC, #     ; Addiere auf den PC etwas drauf -> auch Sprung
```

Wegen den zwei Befehlen : 
	Jeder Befehl der den PC ändert hat zwei extra Zyklen um die Pipeline nochmals zu fluten 

Prozessoren der Firma STM 
	Haben eine Entropiequelle mittels Rauschen, zum Beispiel Halbleiter

Die Rücksprungadresse ist zur Compilezeit nicht bekannt, 
	`Deshalb : LR -> Link Register
	`Branch and Link : Rücksprungadresse steht im Linkregister 

```
MOV PC, LR
```
Nachteil : LR hat eine Rücksprungadresse, Unterprogramme überschreiben Linkregister
*Unterprogramm* ruft *Unterprogramm* auf, hierbei müsssen wir LR speichern

Spekulatives Laden : Der ARM7TDMI hat es nicht ! 
	Hierbei kann der Prozessor Daten aus dem Speicher vorladen 

```

if (...) t = *p; 

Prozessor lädt passowrt in cache 
Bei falscher Condition gibt es keine Schutzverletzung 

if (...) a[*p] = ...

Hierbei kann es trotzdem aus dem Cache gelesen werden
-> Geht nur bei sehr langsamer Bandbreite 

LÖSUNG : Bei rauswerfen von Informationen aus dem Cache muss auch die gesamte Cacheline invalidiert werden
```

## 4.4 Erstes Beispiel eines Assembler Programms 

```
#define N 99U

 unsigned int summe = 0U;
 
 for ( unsigned int k = 1U; k <= N; k++ ){
	summe += k;
 }
```

```
MOV R0, #0               ; S ← 0

 next:
	ADD R0, R0, R1       ; S ← S + N
	SUBS R1, R1, #1      ; N ← N− 1
	BNE next             ; wenn N ̸= 0, dann nochmal
 
 done: ; fertig
```

	SUBS : Subtrahieren und auf 0 prüfen 

*Next WEEK : Ladebefehle !* 


