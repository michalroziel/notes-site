

## Von Virtuellen zu physischen Speicher 

### Typisches Adressraum Layout 

Stack (Thread 0)
Stack (Thread 1)

### Dynamisch Allokierte Daten (Heap)
- Aufruf von *malloc* oder *new* 
- 

### Statisch allokierte Daten
- Shared Libraries
- Instruktionenen / Code
- Globale Variablen



> **Heap** und **Stack** sind beides dynamisch allokierte Größen : Bestimmt bei Laufzeit
> >**Stack** : Daten von Funktionsaufrufen : Parameter, lokale Variablen, Rücksprungadressen 
> >**Heap** : Dynamische Daten

---

### Warum sind Adressraum Layouts wertvolle Informationen für Hacker ? 
- Weil Sie verraten, wo im Speicher sich was befindet
- Hacker können zum Beispiel die Rücksprungadressen rauslesen 

Ein Adressraum [[layout]] verrät wo sich im Speicher welche Bereiche befinden

- Code-Segment (z. B. [[Funktionen]])
- Stack (z. B. Rücksprungadressen, lokale Variablen)
- Heap (z. B. dynamisch allokierter Speicher)
- Shared Libraries (z. B. libc.so)
- [[Umgebungsvariablen]]

Der Hacker kann somit gezielt einen Speicherbereich manipulieren 

## Adress Space Layout Randomisation 
Durch ASLR werden wichtige Speicherbereiche eines Prozesses bei jedem Start zufällig neu angeordnet. 
- Der **Stack** (wo Rücksprungadressen liegen)
- Der **Heap** (für dynamische Speicherallokationen)
- Das **Textsegment** (der Programmcode)
- **Shared Libraries** (z. B. libc)
> Die Adressen ändert sich somit jeded mal 




## Der Speicher, zwei Prozesse 


## Hands on Erfahrung 

### Relocation Problem 

### Ziel : Separate Adressräume 

Variante 2 : 
Hardware + OS kümmern sich um Umrechnung im Hintegrund 


## Memory Management Unit - MMU 

- Verantwortlich für das Mapping von virtuellen auf physische Adressen 
- Page-basiertes oder Segment-basiertes Mapping
- Anzahl der Level
- Größe der Pages

### Page-Based Virtual Adressing 

- speicher eingeteilt in pages - 4KB 
- MMU liegt in CPU 
	- innerhalb einer page des OS liegen die Page Tables. MMU muss die BasisAdresse dieser PageTable wissen 
- ersten 20 Bits : Entscheiden welcher eintrag der Page Table der Relevante ist 
- Für jede Anwendung gibt es ihre eigene PageTable, und eine eigene Übersertzung 

- Jeder einzelner Prozess hat ie Illusion dasss es nur diesen gibt 
- Eine Übersetzung : Single Level 
	- Es gibt mehrere Stufen 

[NEXT TIME] : Page Tables, etc.  


## Page-Based Virtual Adressing 
- basierend auf einer Single-Level Page Table 

## Relocation Problem 

## Speicher für single-level Page Table

Page  Größe : 2^22 ? 


### Aufteilung in 4MB Stücke 

Ziel : Unbenutzte Page Tables nicht im Arbeitsspeicher zu referenzieren 

## Einführung eines Page Directory


[...]


### Virtual Address Translation 

Ziel : Anstatt einer 4MB Page Table : 4KB Page Table 


## Page Directory Entry (vereinfacht)

Jede Adresse : 32 Bit 
Entscheidung mit dem Present-Bit ob der Eintrag valide oder nicht ist 

Base Adresse von Page Table ist in Page Directory 
Base Adresse von Page Frame ist in Page Table


	Folie 99 : Zusammenfassender Vergleich 




## Wiederholung 
MMU zeigt auf die Basis adresse der Page Table 


## Was ? 4MB für jeden Prozess ? 
Man zeigt auf Page Bereich 
Was ist 4 KB Groß ? -> Die Pages selbst 

Wie von 4KB auf 4MB ? -> 

Page Frame ist ein Verweis 
Displacement ist 12 

`
```

2^20 = 1.048.576 Einträge 
Page Table Eintrag = 4 Bytes 
1.048.576 * 4 = 4.194.304

```

## Wie können wir vom 4MB runterkommen ? 

Woe können wir sparen ? -> Wir reduzieren die Größe einer Page Table 
Diese kleineren Page Tables werden durch eine Page Directory verwaltet 

> Page Directory ist ähnlich wie eine Page mit 1024 Einträgen 

Auslegung der Bits : 10, 10, 12

Anstatt einer Großer Page Table haben wir viele Kleine Page Tables

Anstatt einer Million Einträge haben wir 1024 Einträge

Bei jedem Prozess können wir einfach die Page Directory laden 

## Page Table Entry (vereinfacht)

## Zeit ist Geld 

## TLB Translation Lookaside Buffer

Warum ist Hashing Sinnvoll ? 

Was cachen wir in diesem Konstrukt ?  
MMU müsste eine iDee haben, welche tables zuletzt accessed wurden 

TLB = Cache für Page Table Einträge

Nur wenn es im Cache nicht vorhanden ist, wird die Page Table übersetzt

## Segment basierter Ansatz 

Paging : Keine Addition, es reicht eine Konkatenation 
> Hinteren 12 Bits (Displacemen)t) sind immer null 

> Hier : Wir müssen eine Addition durchführen um zu der richtigen Zeile zu kommen 

Nachteil Segmentierung : Addition ist teuer 


Nachteil Paging : Mindestens 4KB, auch nur bei einem Bit 

Bei Paging ist es egal wo in der Page die Adresse ist

## Segmentierung
Kann sein dass wie keinen Platz mehr für einen Prozess haben, danach muss fragmentiert und neu verteilt werden 

## Hybrid Paging und Segmentierung

## Intel 64 (EM64T) Mode Paging 

linearer Adressraum wird übersetzt zu Page Tables 




