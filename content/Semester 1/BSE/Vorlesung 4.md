v4 - Prozesse:  
--------------  
- Was ist ein Prozess?  
- Prozesszustände  
- Verfahren zur Zuteilung  
- Prozesse anzeigen (und deren Eigenschaften erklären)  
- Vordergrund- und Hintergrundprozesse  
- Daemons  
- systemctl  
- Signale  
- Exit status  
- Wiederkehrende Aufgaben: cron/crontab

---

## Was sind Prozesse ?

**Ein Prozess** ist wie ein **kleines Männchen**, das in deinem Computer Aufgaben erledigt.  
Zum Beispiel, wenn du ein ==SPIEL== spielst, gibt es Männchen die das ermöglichen.**Jedes Männchen** bekommt seine eigene **Nummer** ==(PID)==.Damit weist der Computer welche männchen was tuhen. **Prozesse** haben **immer ihre eigenen Bereich,** damit sie nicht in die Arbeit von anderen einmischen können.

  

Laut der Vorlesung: Prozess ist die Laufende Instanz eines Programms oder Befhls. wird durch PID gekennzeichnet

---

## Prozesszustände

haben 3 zustände. Warten, rechned und blockiert

---

## Verfahren zur Zuteilung

  

1. **Wer kommt zuerst, arbeitet zuerst(FCFS)** → Wie bei einer Warteschlage bei McDonalds 🙂

1. **Das schnellste Menschen zuerst (SJN)→** Die Männchen die ihre Aufgaben schnell erledigen können, dürfen zuerst.

1. Alle bekommen die gleiche Zeit (Round Robin) → Jedes Männchen bekommt ein bisschen Zeit und dann ist das nächste dran.

---

## Prozesse anzeigen (und deren Eigenschaften erklären)

ps -ef | more

  

PID Prozesse Id  
PPID Elternprozesse  
C CPU Auslastung  
STIME - wie lange

---

## Daemons

Ein Prozess, der meist beim Hochfahren des Systems automatisch gestartet  
wird und im Hintergrund darauf wartet, seine Aufgaben zu erf¨ ullen

---

## Signale Senden

![[/image 10.png|image 10.png]]

![[/image 1 2.png|image 1 2.png]]

---

## Exit Status

![[/image 2 2.png|image 2 2.png]]