[[ARM7]]


Intrinsics : Compiler umsortiert bei der Optimierung die Befehler nicht 
	COmpiler darf das tun ( im Sinne der Observability) -> solange das rochtige rauskommt

Wir schreiben : Flag setzen, dann Code ausführen
	Wenn Compiler umsortiert : Falsche Ergebnisse 

ARM C-lang hat noch nicht alles drin -> Store LDRX ? 

ARMC ( erster Prozessor ) : es gab intrisics, haben aber falschen code erzeugt

## Mit dem Inline Assembler : 
C und Assembly Routinen mischen 

Schlüsselwörter : ``` asm , _asm  oder _asm_ ```
Jeder Anbieter hat siene eigene Syntax 

[ARM Dev Reference](https://developer.arm.com/documentation/101754/0620/armclang-Reference/armclang-Inline-Assembler)


```
MOV R0, R1, ROR #1

INLINE : asm( " MOV R0, R1, ROR #1 ");
```

```
asm( 
"\t...\n"
"\t...\n"
"\t...\n");
```

Reihenfolge der Register in der Angabe : von Links nach Rechts 
	ABER : Kann sein dass der compiler es doch falsch macht 

Hochgradig Optimierte Compiler heutzutage : Code wird übersetzt (Maschinenunabhängig) und wird dann auf Maschinensprache übersetzt, Optimierung passiert auf dem Maschinenunabhänigegen Code


Durch viele Probleme der Interaktion und Interoperation von ASM und C wurde die erweiterte Syntax entwickelt. 


## 7.3 Erwiterte Syntax 

```

asm( "..." ,  : output : input : clobber  );
```
immediate konstante auch möglich 
Clobber : Seiteneffekte 

Im hohen Optimierungsgrad : Abhängigkeitsliste wird erzeugt 
	Was wurde potentiell geändert  ?
Wir schreiben in die Clobber Liste wenn wir was verändern : 
	Welche Register Lese ich ? 
	Welche Register Schreibe ich ? 
	Darf die Assembler Anweisung umsortiert werden ? 
		Dies darf man in der Assembler Anweisung angeben 

**Schlüsselwort** memmory : Speicherzugriif 
**Schlüsselwort** status ? : Statusregister
*ABER* : Es ist Prozessorabhängig 

## 7.4 Eingabe- und Ausgabeoperationen - S.129


```
asm("MOV %[res], %[val], ROR #1" : output : input);
```

##### An den Compiler : 
% -> irgendeine Angabe für dich 
[ ] -> der name 

```
asm("MOV %[res], %[val], ROR #1" : [res] "=r" (y) : [val] "r" (x));
```

> Durch den constraint string gibt man die Art des Operanden an. Register–Operanden werden durch r gekennzeichnet.

i -> immediate 
m -> m für memmory gibt es, kann der Prozessor aber nicht 

*res* ist Register für das nur geschrieben wird
*val* ist Register für das nur gelesen wird 

[Inline assembly with Arm Compiler for Embedded](https://developer.arm.com/documentation/100068/0623/Migrating-from-armcc-to-armclang/Inline-assembly-with-Arm-Compiler-for-Embedded-6)



[Extended Asm - Assembler Instructions with C Expression Operands]( https://gcc.gnu.org/onlinedocs/gcc/Extended-Asm.html)
 
Beispiel aus der Website : 
```
int src = 1;
int dst;   

asm ("mov %1, %0\n\t"
    "add $1, %0"
    : "=r" (dst) 
    : "r" (src));

printf("%d\n", dst);
```

Von Sytax müsste dst das erste Argument sein, ist aber das zweite 
deshalb : Notation mit Namen verwenden 


Wenn wir einen Befehl haben, den der Prozessor kann, der Compiler, aber nicht kann es zu PRoblemen kommen 


```

uint16_t   a , b , c :

a = 1; 
b = 2;
c = a+b;  <-- 32 Bit 
```
STRH ? zum speichern für c? 
L und R -Values beachten 

```
ADD R0, R1, R2
AND R0, R0 0xFFFF  -> Führt zu Problemen, da der C Compiler 32 Bit daraus macht 
```

```
// Type your code here, or load an example.
#include<stdint.h>

uint16_t sum( uint16_t a, uint16_t b){

  
	return a + b;    // STANDARD : als 32 Bit auszuführen

				  // Wird als 16 Bit optimiert-> gute Opt.

}

```

```
sum(unsigned short, unsigned short):

sub sp, sp, #4

mov r2, r1

mov r3, r0

strh r0, [sp, #2]

strh r1, [sp]

ldrh r0, [sp, #2]

ldrh r1, [sp]

add r0, r0, r1

mov r1, #255

orr r1, r1, #65280

and r0, r0, r1

add sp, sp, #4

bx lr

```

Wenn wir Optimieren wollen : Nur wenn man sich *sicher* ist, dass es schneller wird 

Was wenn wir einen Befehl ahben, dem der Compiler gar nicht verwenden kann ? 
	-> Wir müssen auf Assembler wechslen 

Auf der Webisite oben vgl. : #### 6.50.2.4 Flag Output Operands

```
asm volatile ( " ... " : output : input : clobber);
```
Restriktivste Variante von Compiler angaben.

Beispiel : Schleife

```
int x;


for ( int i = 0; i  <100 ; i++ ) {

		
	int count t = x + x ;

	}

Würde die anweisung count aus der Schleife rausziehen
```

*volatile* Betrifft nur C compiler 


### Was tun damit es nicht verändert / wegoptimiert wird ? 
*volatile* angeben ! und in der *CLobber Liste* memmory angeben ( S.141)

FÜR UNS : Wenn wir in der Praxis Asembler brauchen : Erstmal mit ***Inline Assembler*** versuchen 


#### Figure 1 : System architecture for STM32H7A
...
STM32H7A kostet 5-10 euro
Datenspeicher : Write-Allocate oder Write-Through ! 
Dummy reads auf die gleiche Speicherstelle ?
Cortex M7

Nächste Woche : Alle möglichen Fragen Stellen 




