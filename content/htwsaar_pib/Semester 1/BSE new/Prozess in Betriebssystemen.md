

## Was sind Prozesse ?


Ein Prozess ist wie ein  ```kleines Männchen```, das in deinem Computer Aufgaben erledigt.  
Zum Beispiel, wenn du ein ==SPIEL== spielst, gibt es Männchen die das ermöglichen.**Jedes Männchen** bekommt seine eigene **Nummer** ==(PID)==.Damit weist der Computer welche männchen was tuhen. **Prozesse** haben **immer ihre eigenen Bereich,** damit sie nicht in die Arbeit von anderen einmischen können.

---

## Was macht der Computer mit den Prozessen?

Der computer ist super schnell und kann viele Dinge auf einmal machen. Aber im wirklichkeit arbeitet immer nur ein Männchen auf der CPU. Die anderen Warten.  
  
ES GIBT DREI ARTEN VON PROZESSEN!

1. **Rechnend** (arbeitet gerade an etwas).

1. **Wartend** (hat nichts zu tun).

1. **Blockiert** (wartet auf etwas, z. B. eine Datei).

---

## Wie entscheidet der Computer, welche Männchen zuerst arbeiten darf?

Der **Scheduler** ist ein “LERHER”, der sagt, welche Männchen wann daran ist. Er benutzt verschiedene Regeln wie in [[Vorlesung 4|der Prozessverwaltung]]:

1. **Wer kommt zuerst, arbeitet zuerst(FCFS)** → Wie bei einer Warteschlage bei McDonalds 🙂

1. **Das schnellste Menschen zuerst (SJN)→** Die Männchen die ihre Aufgaben schnell erledigen können, dürfen zuerst.

1. Alle bekommen die gleiche Zeit (Round Robin) → Jedes Männchen bekommt ein bisschen Zeit und dann ist das nächste dran.

---

## Wie sehen ich welche Prozesse am Arbeiten sind?

Du kannst im Termial sagen, er soll dir die Männchen zeigen.  
Mit dem Commando ==ps -ef== und er liestet alle Prozesse auf.  
Und mit dem Commando ==top==, sieht du live , welche Prozesse gerade ie CPU benutzt.

![[/image 17.png|image 17.png]]

---

## Übung

Aufgabe 4-4: Übungen zu [[UNINTS|Diensten und Units]]

1. **Mit welchem Kommando kann man einen Dienst starten bzw. stoppen?**  
    FINDE NICHT IN DER VORLESUNG

1. **Zeigen Sie alle Units an, die sich aktuell im Hauptspeicher befinden.**  
    MIT COMMAD top

1. **Zeigen Sie die Abhängigkeiten des Dienstes NetworkManager an.**  
    Steht die Abhängigkeit bei dem Bereich CPU an.

  
  

Aufgabe 4-5: Übungen zur Prozesssteuerung

 **Ein Prozess mit der PID 12345 benötigt eine geordnete Beendigung, damit er seine**  
    **Daten sichern kann. Sie möchten verhindern, dass wichtige Daten verloren gehen.**  
      
    Welchen Befehl würden Sie ausführen, um den Prozess geordnet zu beenden?
    
    Was passiert, wenn der Prozess nicht auf das erste Signal reagiert?
    A) Geordnet beenden benutze ich den Command ==Kill -TERM 12345==  
    B) Dann bennede ich es direkt mit dem Command ==kill -KILL 12345==  
    

##### Sie stellen fest, dass mehrere Instanzen des Programms firefox auf Ihrem System  
    laufen und das System stark belasten. Sie möchten alle Instanzen von firefox ofort beenden
      
    Welchen Befehl verwenden Sie, um alle Prozesse mit dem Namen firefox
    gewaltsam zu beenden?
      
    Vielleicht mit dem befehl ==pkill -Kill -x firefox  
    
**Aufgabe 4-6: Übung zum [[Vorlesung 4|Exit-Status]]**  
**Sie haben einen Befehl ausgeführt, um Dateien nach einem bestimmten Muster zu durchsuchen, erhalten aber keine Rückmeldung, ob das Muster gefunden wurde oder ob ein**  
**Fehler aufgetreten ist.**  
  
• Welchen Befehl verwenden Sie, um den Exit-Status des zuletzt ausgeführten Kommandos abzufragen?  
• Was bedeutet ein Exit-Code von 0? Was bedeutet ein Exit-Code von 1?  
  
A) ich benutze den $echo $? um ihn anzufragen.  
B) 0 ist erfolgrei und andere zahelen heißen fehler

  

  

Aufgabe 4-7: Übungen zu [[Vorlesung 4|Cron]] und Automatisierung (keine ahnung wie die aufgabe funktsoniert…

1. Sie möchten das Skript [backup.sh](http://backup.sh/) jeden Tag um Mitternacht automatisch ausführen lassen.  
    • Wie würden Sie den Crontab-Eintrag schreiben, um diese Aufgabe zu automatisieren?  
    • Wo würden Sie diesen Eintrag speichern, wenn er nur für Ihren Benutzer gelten  
    soll?

1. Sie möchten ein Wartungsskript einmal pro Woche, sonntags um 3 Uhr morgens,  
    ausführen lassen.  
    • Schreiben Sie den Crontab-Eintrag für diese Aufgabe.  
    • Verwenden Sie alternativ die spezielle Zeichenkette für wöchentliche Aufgaben.

## Siehe auch

- [[Vorlesung 4]]
- [[UNINTS]]
- [[Vorlesung 5]]
- [[Vorlesung 7]]
