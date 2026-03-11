[[ARM7]]
###### Der Asynchrone Interrupt 
Wenn wir etwas in den Speicher schreiben wo eigentlich kein Speicher ist, wird ein *Abort-interrupt* ausgeführt

```
svc befehl 
```

Interrupt Vektor Tabelle -> Sprungzieladresse der Routinen die anzuspringen sind, wenn ein Interrupt ausgeführt ist 

```
reset befehl ist auch ein Interrupt
```
Manchmal wird auch zwischen Hardware und Software Interrupts auslöst 

Asynchron -> ohne bezig zur Ablaufstruktur 

##### VGL Seite 14 Skript
Das System startet im Supervisor Modus mit reset Befehl -> höchste Priorität

##### Deeply Embedded Bereich 
Hier gibt es keine verschiedene Prozesse und keine virtuelle Speicherverwaltung 
Nicht wie in einem Computer wo wir den File Explorer, etc starten können

Es gibt im kritische Anwendungsbereiche für Embedded Systems 

Interrupts können auch gesperrt werden -> Durch eine Bitmaske : 0 oder 1 
Interrupt -> Interrupt Service Routine -> Interruot tut was er muss

Mit dem sperren der Interrupts sperren wir die Reaktivität des Systems 
Für Motor Zündungen sind diese esentiell 

Interrupt ausgelöst : Welche der Peripherien hat den Interrupt ausgelöst ?

Empfehlung : Prioritisierungs schema während der Laufzeit nicht zu ändern 
Mit Interrupts zu Programmieren ist es einfacher als mit Echtzeitsystemen 
	Hierbei wird nämlich ein Interrupt Stack erstellt
Eine Interrupt Service Routine darf nie blockiert werden 

Wir können die ISR nicht pausieren, andere Interrupts können diese allerdings blockieren 

```
yield suspend - Befehle 
```

Wenn die ISR blockiert wird, ist das unterbrochene Programm unterbrochen
ISR sollten kurz und klein woei kompakt sein 

QUATIX , CORTEX ? M32 ; M... haben den gleichen Interrupt Controller 

### MMU 
der ARM7 hat *keine MMU-Memmory management Unit*

> In Systemen ohne MMU oder bei einem ungültigen Instruktionswort ist die zugehörige Unterbrechung lediglich das Symptom eines vorangegengen, sehr schwerwiegenden Software-Bugs 

> Das bedeutet für uns : wir benutzen Assertions , da diese uns weiterhelfen

Wenn das Sytem dauernd die ISR ausführt, ohne sie kommt nie mehr : Nachschauen ob mal beim letzten Mal die ISR richtig beendet hat 

	'Memo Map IO ?' -> peripherieregister, mit dem wir ein D FLIP FLOP connecten können, eine Leuchtdiode, Q Ausgang des DFF an den Datenbus 

Mit dieser Verbindung können

Adress Bus , Adressdecoder Adresse vergleichen

#### Peripherie vs Speicher
Speicher : bleibt so lange stehen bis wir was reinschreiben 


Peripherie :

```
int i = 0 ;

int a[2] = {1,2};
a[i] = i++;         Zwei Seiteneffekte : lese i und schreibe i++

Bei dem Seiteneffekt ist nicht definiert, was zuerst passieren soll


Sequence point : Punkt zu dem ein Seiteneffekt ausgeführt werden muss
Semikolon ist zum Beispiel ein Sequence Point 
```

	'bei jedem Prozessor ist der Speicherzugriff der Flaschenhals '

Start : Registerzugriff
Ende : registerzugriff

```
t0 = timer ;
...
t1 = timer ;
dt = t1-t0:
```

### VOLATILE IS THE SOLUTION
Eine variable kann *const* und *volatile* gleichzeitig sein
Sagt dem Compiler ! nicht Prozessor ! Redunande Variablen werden nicht wegoptimiert und der Ablauf nicht verändert 

#### "const" == read only 
kann nicht auf der linken seite eines gleichheitszeichens stehen 
ist ein L Side Evaluable 

```
int x = 42;
int const * p = &x;

*p = 43; // FAILURE ! 

 x = 44;

if (*p == 44) ...... ; 
```


```
 static int const answer = 42; // Hat die Speicherklasse storage class

	// answer wird im ROM gelagert, ist read only 

 answer = 43; // FAILURE ! 
```

```
int* const p = &answer ; // FAILURE

int* const q = ( int const* )&answer;

*q = 44;

Auf dem PC kann das funktionieren : Das Programm läuft im RAM ! kein ROM
```


Dem Compiler müssen wir immer angeben ob volatile etc. ...


### Inversion of Control 

RMW -> read modify write 

Im Embedded Bereich kann es mittels Semaphoren zu Deadlocks kommen 
Darauf achten, 


## Interplanetarische Betriebssystemupdates 




