[[ARM7]]

## Im folgenden besprechen wir die Eigenschaften des [[ARM7]] Prozessors



- ARM und ISA ( Instruction Set Architecture ) hängen strikt zusammen
- Prozessortypen : ARM1 - ARM 8, 
	Architekturen : ARMv1 - ARMv8

- Wir arbeiten mit dem ARM7TDMI bei 80 MHz
	M -> Multiplikator 

![[Screenshot 2024-10-22 at 18.52.06.png]]

```
  SUB Rd, Rn, Operand2
```

- ARM920T mit der HAWARD Architektur
- ARMv1 wurde nie kommerziell eingeführt
- ARMv2 hat diese schnell ersetzt → 26-Bit-Adressraum, Mehr Register, Multiplikationsbefehl

#### DEEPLY EMBEDDED SYSTEMS → MikroController Programmierung
Beispiel von FlugzeugSteuerSystemen
Hardware Description Languages → VHDL , VERILOG


### Problematik bei Flip Flops : Metastabilität, Functional & instructional Hazards
Es gibt ein kurzes Zeitfenster wo eine 0 auftritt, wo in der booleschen Algebra keine steht

![[Pasted image 20241022191121.png]]

- In den Usa gab es einen Hazard bei Toyota 
- Beispiel des Zündfensters bei Benzin Motoren 

> [!Mikrocontroller reagieren viel schneller als Controller in einem Computer ]
> 

Die Mikrocontroller müssen auf verschiedene mögliche Situationen vorbereitet sein
> " Blue Logic "

Abstandsicherungssystem bei einem Leoparden Panzer verfügt Microcontroller, die zur Entscheidungsfindung dazutragen.
- Hierbei wird ein Elektromagnetisches Feld um den Panzer herum geschaffen, welches erfassen kann wo genau ein Projektil einschlagen wird
- Dies ist ein Beispiel von der Verbindung von Hardware und Software für Sicherheitskritische Anwenungen
- Cortex-Thrust doppelt virtualisiert **?** 

# Eigenschaften des ARM7
- in der RISC sind alle Instructions gleich lang → der PC muss incremented werden
- gemeisnamer BUS für Daten und Instruktionen → Von Neumann Architektur
- Es gibt 3,2,1 und 0 Adressierbare Formate
    - 3 Addressiges Format : a = b + c
- Hier bezieht sich Addressierbar auf Register Adressierung, _**nicht Speicher**_

```
SUB Rd, Rn, Operand2
```

>[!Prozessoren haben Sicherheitskonzepte, deshalb kann nicht jeder Befehl in jedem Kontext ausgeführt werden ]

### Wir haben : 37 Register, für uns 16 + 1 Statusregister nutzbar
Es gibt immernoch *"Shadow Register"* Die Programmierung damit ist sehr Hardwarenahe 
![[Screenshot 2024-10-29 at 13.39.15.png]]

###### Assembler Programmierung ist Typeless ! 
### Exception Handling ist im Embedded Bereich ein kritisches Problem !
Wer *bedient* die Exception ? Was soll dann passieren ? 
Mit der Verwendung der *STL* -> Standard Technic Library können Probleme auftreten
Selbst Funktionen welche als "No Exception" deklariert sind können eine Exception werfen. 
Assertions sind immer implizit vorhanden -> Diese helfen uns, DEbugging um einiges zu verkürzen 
- Undefined behaviour kann allerdings immern noch auftreten

>[!Narrow Contract und Throne ? Contract]
    - System stürzt nicht ab sondern ragiert in einer deterministischen Weise
    - Funktionen dürfe nicht als No Except deklariert werden damit SIe intern eine Exception werfen
    - Bei Bibliotheks Funktionen anschauen ob SIe als No-Except deklariert sind
        - Lösung : Eigene Variante der Funktion entwickeln, die No-Except ist
        - Nur da Exception throwen wo man SIe auch fangen kann
    - Irgendwann ist der Heap auch voll

- *Dynamischer Speicher in EMBDEDDED : Placement NEW ?*
    - Void* Stern als Argument übergeben
    - Die Anfragen an das System sind klar definiert
    - im Embedded Bereich wissen wir wie viele Kommunikationskanäle wir haben

> EIn WORT hat in ARM 32 BITS
- Immer : Lesen, modifizieren, schreiben

### Mutex
Ein **Mutex** (Kurzform für _Mutual Exclusion_, auf Deutsch **gegenseitiger Ausschluss**) ist ein Synchronisationsmechanismus in der Informatik und speziell in der Mikroprozessortechnik. Er dient dazu, den gleichzeitigen Zugriff mehrerer Threads oder Prozesse auf gemeinsam genutzte Ressourcen wie Speicherbereiche, Dateien oder Peripheriegeräte zu steuern.

**Warum sind Mutexe wichtig?**

In Systemen mit **Parallelität** oder **Nebenläufigkeit** können mehrere Ausführungseinheiten (Threads oder Prozesse) gleichzeitig laufen. Wenn diese Einheiten auf gemeinsame Ressourcen zugreifen, kann es ohne geeignete Synchronisation zu Problemen wie **Race Conditions**, **Deadlocks** oder **Inkonsistenzen** in den Daten kommen.
**Wie funktioniert ein Mutex?**- **Sperren (Lock):** Bevor ein Thread auf eine geteilte Ressource zugreift, versucht er, den zugehörigen Mutex zu sperren. Wenn der Mutex bereits von einem anderen Thread gesperrt ist, muss der anfragende Thread warten, bis der Mutex freigegeben wird.- **Freigeben (Unlock):** Nach Abschluss des Zugriffs auf die Ressource gibt der Thread den Mutex wieder frei, sodass andere Threads darauf zugreifen können.


### Semaphoren
Semaphoren: Ein weiterer Synchronisationsmechanismus, der sich von Mutexen dadurch unterscheidet, dass er einen Zähler verwendet und somit mehr als einen gleichzeitigen Zugriff zulassen kann.

- Ein Adressiege Operanden sind zum Beispiel Akkumulator Maschinen
    - Akkumulator + Ziel
- 0 Adressiege Operanden
    - Bsp : Java Byte machine : Klar dass on top of the stack
![[Screenshot 2024-10-29 at 14.27.38.png]]

- Eine Lange PipelLine ( wie 11 steps ) kann sogar die Latenz erhöhen
    - Allerdings können wir die Taktfrequenz erhöhen → Durchsatz von Befehlen erhöhen
    - Latenz Zeit veringern : Weniger PipeLine Stufen benutzen
![[scREEN.png]]
- Operand 2 ist entweder ein Register Inhalt oder ein SpeicherInhalt ?
    - Operanden sind nicht gleichwertig, mit dem OP1 können wir mehr machen
- Immediate Konstanten wurden aus dem Speicher gelesen
- Auch Komplexe Befehle möglich : Bsp. : 8 register gleichzeitg lesen

## 2.2.2 Register im ARM Modus 
Der ARM7 Prozessor mit dem wir uns beschäftigen verfügt über 37 Register.
Davon stehen uns als Programmers 16 + 1 zur Verfügung. 
Dies beinhaltet Register R0-R15 + 1 Statusregister 



![[Screenshot 2024-10-29 at 14.30.19.png]]

> R15 ist der Programm Counter !
> 	Kann somit für Logisch-Arthmetische Befehle genutzt werden 

> R14 ist das Link Register 
> 	Rücksprungadresse des letzten Programms kann hier gespeichert werden 

> 	R13 ist das Stack Pointer Register 

> ABI -> Application Binary Interface 

> R0 - R12 
> Diese Register sind frei verwendbar, -> Calling Convention 
> Callee vs Caller Sage Registers 

> Register R0 - R7 stehen und ebenfalls zur Verfügung 


## 2.2.3 Exception Modus des ARM7
- Unterbrechungen
- Etwas ist passiert, was den Prozessor dazu bringt fden aktuellen Befehl zu beenden und etwas besonderes zu machen
    
- Beispiel : Aktives Warten bzw Polling , Sinnloses Warten
    
    - Fußball schauen auf der Couch und warten auf den Pizza Boten
        - Lösung : eine Klingel benutzen
    - **der Untebrochene Vorgang wird transparent fortgesetzt**
    
    > Der Gesamte Prozessor-Zustand wird wiederhergestellt und gerettet
    
    - Wo lagern wir den Kontext switch aus ?
    - Kann auch in der Hardware (gelb) passieren
![[screre.png]]

> Wenn wir R13 / R14 Im Interrupt Modus verwendne, erhalten wir die gelben Varianten

- CPSR , SPSR wird auch gerettet !
- Wir müssen uns nur um R0 bis R12 kümmern, um diese später rekonstruieren zu können
- Am Prozessor liegt das Interruot Signal

## HI-Priority Interrupt 
- Warum nicht immer HI-PRIO Interrupt?
- Wenn wir nur einen haben dann OK!
- Metapher sonst : Wir haben eine Klingel UND einen _**FEUERMELDER**_
    - HI-PRIO unterbricht “normalen” Interrupt
- Deshalb : Granularität beachten : Wichtig / Unwichtig
- VIC -> Vector Interrupted Comtroller 


#### Questions 
Was muss ich über die Unteschiedlichen Prozessor Typen 

### Summary 
**SUMMARY**

- Cortex - Thrust Reihe von Prozessoren sind essentiell

> Prozessoren _**können : gut , billig , schnell sein**_

- Die Phasen der Befehlsausführung lernen
- CISC vs RISC wiederholen
- NÄCHSTES MAL Embedded Systems </aside>


- Es gibt zwei Interrupt Requests :
- Interrupt, und HI Prio Interrupt 
