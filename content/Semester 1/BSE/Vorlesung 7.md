```SQL
v7 - Shell-Programmierung:
--------------------------
- Was ist die Shell?
- Warum Shell?
- Kenntnisse über die Basis Befehle
- Was ist die She-bang?
- Skriptaufruf mit/ohne Subshell
- Kommentare in Shell Skripte
- Debugging Informationen an/aus
- Standard-Datenströme in der Shell (!!)
- Umleitungsoperatoren (!!)
```

  

---

## Was ist die Shell und Warum shell?

Die **Shell** ist eine **Schnittstelle zwischen dem Benutzer und dem Betriebssystem**. Sie ermöglicht es dir, **Befehle einzugeben**, um Programme zu starten, [[Vorlesung 2|Dateien]] zu verwalten oder [[Vorlesung 4|Prozesse]] zu steuern.

**Warum Shell ?**

- man kann Aufgaben mit der shell deutlich schneller erledigen, wie zum Beispiel sachen im internet zu downloden

- und kann automationen einrichten

  

---

## Kenntnisse über die Basis Befehle

|   |   |   |
|---|---|---|
|Befehl|Funktion|Was wird ausgegeben?|
|pwd|Zeigt das aktuelle Verzeichnis|Den Pfad, in dem du dich gerade befindest|
|who|Zeigt alle eingeloggten Benutzer|Eine Liste aller aktiven Benutzer|
|whoamI|Zeigt den aktuellen Benutzer|Den Benutzernamen, mit dem du angemeldet bist|
|wc|Zählt alles buchstaben in einer datei|Kommt i.eine zahl raus|
|ls|eine liste von der jetzigen Pfad wird angezeigt||
|cd|im Verzeichnis wechsle||
|touch|Datei anlegen||
|mkdir|Verzeichnis anlegen||
|nano|Editor||
|rm|löschen||
|rmdir|verzeichnis löschen||
|cp|copy|cp datei1 → datei2|
|mv|move|mv datei1 → /../…/absolten pfad/|
|cut|-c1|gibt mir den 1 Bustabe|
|cut|-c1-4|gib mir die Bustabe von der erste bis 4 reihe|
|export|export Hallo|Ich kann die Locale variable zu einer [[Vorlesung 8|Umgebungsvariable]] machen|
|readonly|readonly Hello|wird zu einer Konstante, kann nicht verändert werden|
|2>&1|Flasche output wird zu 1 gewechselt||
|expr|expr 1 + 2 = 3  <br>expr 5 \* 3|wichtig bei * bruache ich einen Back slasch|
|tr|tr a b < txt.datei|kann die bustabe wechseln. In dem Bsp. werden alle wörter die ein A beinhaltet zu b um gewandelt. z.B p**aa**r → p**bb**r|

---

## Was ist die She-bang?  

```SQL
#!/bin/bash
```

Wenn man eine leere Datei erstellt mit dem befehl touch, dann in der erste Zeile #!/bin/bahs ein trägt, dann weist das proramm “oh es kommt ein bash code”, und man muss nicht extra den Datei einen dateitypen verpassen. also kein .sh oder txt oder pdf.

---

## Skriptaufruf mit/ohne Subshell

  

|   |   |   |
|---|---|---|
|**Befehl**|**Was passiert?**|**Wichtiger Unterschied**|
|.**/**script.sh|Startet das Skript in einem neuen Unterprozess (Subshell).|Änderungen an [[Vorlesung 8|Umgebungsvariablen]] gelten **nur innerhalb des Skripts**.|
|. script.sh|Führt das Skript im akktuellen Termial prozess aus.|Änderungen an [[Vorlesung 8|Umgebungsvariablen]] **bleiben im aktuellen Terminal** bestehen.|

---

## ==#==Kommentare in einem Skript

  

![[/image 13.png|image 13.png]]

---

## Debugging Informationen an/aus

  

Verwendung des set Kommandos:  
▶ set -x : Aktiviert die Ausgabe jedes Befehls vor der Ausführung  
▶ set +x : Deaktiviert die Ausgabe jedes Befehls  
▶ set -e : Beendet das Skript bei einem Fehler

  

```SQL
Termial: 
set -x \#egal was ich jetzt schreibe, es ist wie ein Papagei. 
set +x \#jetzt ist der Papagei still
set -e \#wenn ich i.was flasch flasch mache ist der papagei tot und ich muss mir 
			# einen neune kaufen :(
```

---

## Standard-Datenströme in der Shell (!!)

![[/image 1 4.png|image 1 4.png]]

---

## Umleitungsoperatoren (!!)

![[/image 2 3.png|image 2 3.png]]

## Siehe auch

- [[Vorlesung 2]]
- [[Vorlesung 3]]
- [[Vorlesung 8]]
- [[Vorlesung 9]]
- [[Vorlesung 10]]
