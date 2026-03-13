  

```Plain
v2 - Linux - Dateisystem:
-------------------------
- Welche Dateisysteme gibt es?
- Größenordnungen und Bezeichnungen
- Anlegen von neuen FS
- Die Datei /etc/fstab
- Anzeigen von Festplatten-Details
- Linux Dateibaum
- Anzeigen & Navigation in der Shell durch den Dateibaum
- Dateien anlegen & anzeigen
- Finden von Dateien
- Home-Verzeichnis
- .profile vs. .bashrc
```

---

## Welche Dateisysteme gibt es?

### **Blockbasierte UND Objektbasierte Dateisysteme**

Stell dir vor, ein Dateisystem ist wie ein riesiges Regal, in dem alle deine Bücher (Dateien) ordentlich einsortiert sind. Bei Linux gibt es vor allem **zwei** Arten: ==**Blockbasierte**== **UND** ==**Objektbasierte Dateisysteme**==

- **Blockbasierte Dateisysteme:** Diese teilen die Daten in kleine, gleich große Stücke (Blöcke) auf – so wie wenn du ein Puzzle in viele kleine Teile zerlegst. + Schnell Zugriff

- **Objektbasierte Dateisysteme:** Hier werden Dateien als komplette Objekte mit zusätzlichen Informationen (Metadaten) gespeichert – fast so, als ob jedes Buch eine eigene kleine Geschichte über sich hat.

---

## Größenordnungen und Bezeichnungen

### Tabelle

![[/image.png|image.png]]

---

## Anlegen von neuen FS!

### Schritt für schritt Anleitung

Stell dir vor, du hast eine große, leere Kiste (deine Festplatte) und möchtest sie in kleine Fächer (Partitionen) unterteilen, damit du darin deine Spielsachen (Dateien) ordentlich ablegen kannst. So funktioniert das Anlegen eines neuen Dateisystems:

  

### 1. Festplatte in Fächern aufteilen (**Partitionierung**)

Zuerst nimmst du ein Werkzeug namens **parted** zur Hand. Damit schaust du, welche Kisten es überhaupt gibt, und wählst die aus, die du aufteilen möchtest. Dann teilst du die Kiste in Fächer ein.

![[image 1.png]]

- Du startest ==**parted**== und lässt dir alle vorhandenen Festplatten anzeigen.

- Mit einem Befehl wie ==select /dev/sdb== sagst du, welche Festplatte du bearbeiten möchtest.

- Mit ==mklabe==l erstellst du eine neue „Regalkarte“ (Partitionstabelle). Für kleinere Kisten benutzt man oft den Typ **msdos**, für größere **gpt**.

- Dann legst du mit Befehlen wie ==mkpart== ==primary ext4 0% 50%== und ==mkpart primary ext4 51%== 100% die einzelnen Fächer an.

**Diese Schritte sind so, als würdest du deine große Kiste in zwei kleinere Schubladen unterteilen.**

  

### 2. **Jedes Fach für Spielzeuge herrichten (Formatierung)**

Nun muss jedes Fach (jede Partition) so vorbereitet werden, dass es genau weiß, wo die Spielsachen (Dateien) hingehören.

  

- Hier kommt der Befehl ==**mkfs**== ins Spiel, der das Fach mit einem bestimmten Dateisystem (wie z. B. **ext4**) „anmalt“ oder einrichtet.

- Zum Beispiel: ==mkfs -t ext4 -f /dev/sdb1== richtet das erste Fach ein, damit es ab jetzt weiß, wie und wo Dateien gespeichert werden können.

  

### 3. **Fächer im Haus (Computer) sichtbar machen (Mounten)**

Nachdem die Fächer vorbereitet sind, musst du sie an einen festen Platz in deinem Haus (dem Dateibaum) stellen, damit du sie auch nutzen kannst.

  

- Mit dem Befehl ==**mkdir**== erstellst du einen Ordner, der als „Platz“ für dein Fach dient, z. B. /daten1.

- Dann montierst du das Fach mit ==mount -t ext4 /dev/sdb1 /daten1==, sodass dein Computer weiß, dass in /daten1 deine neue Partition liegt.

  

### 4. **Alles bleibt auch nach dem Neustart bestehen (Eintrag in /etc/fstab)**

Damit die Fächer (Partitionen) immer da sind, auch wenn der Computer mal neu startet, schreibst du einen kleinen Eintrag in die Datei **[[Klausur|/etc/fstab]]**. Dieser Eintrag ist wie eine Liste, in der steht, welche Partition wo immer eingehängt werden soll, zum Beispiel:

```SQL
/dev/sdb1  /daten1  ext4  defaults  0  0
```

So wird deine Festplatte Schritt für Schritt in nutzbare Bereiche unterteilt, formatiert und fest in den Computer eingebunden – ganz so, als würdest du ein neues Regal zusammenbauen und ordentlich beschriften, damit du später immer weißt, wo deine Spielsachen liegen.

![[image 2.png]]

![[image 3.png]]

## Die Datei /etc/fstab

Denk an /etc/fstab wie an eine große Anleitung oder einen Fahrplan, der dem Computer sagt: „Hey, häng diese Festplatte hier ein und jene Festplatte dort!“  
In dieser Datei steht, welche Geräte (also die Partitionen) wo im Dateibaum eingehängt werden sollen und welche Einstellungen (Optionen) benutzt werden.  

![[image 4.png]]

  

![[image 5.png]]

  

  

## Anzeigen von Festplatten-Details

Um zu sehen, wie voll oder leer deine Regale sind, benutzt du Befehle wie ==df -h==“. Diese zeigen dir, wie viele Daten auf einer Festplatte liegen und wie groß die einzelnen Partitionen sind – ähnlich wie du zählst, wie viele Legosteine in einer Kiste sind.

## Linux Dateibaum

Der Linux-Dateibaum ist wie ein echter Baum, in dem die Wurzeln der wichtigste Teil sind und alle anderen Äste (Ordner) daran hängen.  

Die Wurzel heißt „/“ und von dort verzweigen sich viele spezielle Ordner wie /bin, /etc, /home und so weiter.  
Jeder Ordner hat eine eigene Aufgabe, genau wie in einem echten Baum jeder Ast andere Blätter trägt.

![[image 6.png]]

## Anzeigen & Navigation in der Shell durch den Dateibaum

Um in diesem Dateibaum herumzulaufen, benutzt du die [[Vorlesung 7|Shell]] (eine Art Kommando-Zentrale). Einige wichtige Befehle sind:

- ==**ls**==**:** Zeigt dir, was in einem Ordner liegt, ähnlich wie wenn du in einen Raum schaust.

- ==**cd**==**:** Mit diesem Befehl wechselst du in einen anderen Ordner – wie wenn du von einem Raum in den nächsten gehst.

- ==**pwd**==**:** Dieser Befehl zeigt dir, in welchem Raum (Ordner) du gerade bist.

So findest du immer den Weg, egal wie groß der Baum ist.

## Dateien anlegen & anzeigen

Wenn du eine neue Datei erstellen möchtest, ist das, als würdest du ein leeres Blatt Papier nehmen.

- ==**touch**==**:** Erstellt eine leere Datei, genau wie ein frisches Blatt Papier.

- ==**cat**==**:** Zeigt dir den Inhalt einer Datei an, ähnlich wie wenn jemand dir vorliest, was auf dem Blatt steht.

Manchmal benutzt man auch Editoren wie „==vi==“ oder „==vim==“, um die Datei zu schreiben – das ist wie ein Bleistift, mit dem du auf das Blatt schreibst.

## Finden von Dateien

![[image 7.png]]

  

## [[Umgebungsvariablen|HOME]] VERZEICHNIS

![[image 8.png]]

## Siehe auch

- [[Vorlesung 1]]
- [[Vorlesung 3]]
- [[Vorlesung 7]]
- [[Klausur]]
