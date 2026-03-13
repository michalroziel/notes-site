Stell dir vor, du hast Schubladen mit Etiketten drauf, z. B. “Dein Zuhause” oder “Deine Sprache”. Diese Etiletten heißen **Umgebungsvariablen.**

Beispiele:

- [[Vorlesung 2|HOME]] —> Zeigt dir, wo dein “Zuhause” im Computer ist.

- [[Vorlesung 8|PATH]] —> Sagt dem Computer, wo der Programme finden.

---

## Datei- und Verzeichnisrechte

Stell dir vor, du hast eine Schatzkiste. Wer darf was reinlegen und wer darf sie öffnen?

Es gibt **drei Gruppen von Personen:**

1. **DU** (Eigentümer) U

1. **Deine Freunde** (Gruppe) G

1. **Fremde** (alle anderen) O

  

**Es gibt drei Dinge, die man tun kann:**

1. r (lesen)

1. w (schreiben)

1. x (ausführen

  

Beispiel: Mit einem Zauberspruch „[[Vorlesung 3|chmod]]” kannst du sagen, wer was darf!

  

![[/image 9.png|image 9.png]]

---

## Was sind Inodes?

Stell dir Inodes wie kleine Zettelchen vor, die sagen, was in der Schatzkiste stecken:

- Wie groß sie ist.

- Wem sie gehört

- Wann sie zuletzt geöffnet wurde

---

## Besondere Zauberrechte

1. Setuid (Ausführer-Zauber): Wenn jemand dein Programm benutzt, tut er es mit deinen ZAuberkräften

1. **SETGIT** (Gruppen-Zauber): Neue Sachen in deiner Schatzkisten gehören automatisch deiner Gruppe.

1. **Sticky bit** (klebe-Zauber): Nur der Schatzmeister (du) darf Sachen rausholen.

im Command ist nur ein x.

---

## Standardrechte und [[Vorlesung 3|umask]]

Wenn du eine neue Schatzkiste machst, hat sie automatisch gewisse Regel:

**Datei (Blatt** Papier): Du und deine Freunde dürfen lesen / schreibe, Fremde dürfen nur lesen.

**Verzeichnis** (Kiste): Du und deine Freunde dürfen reinschauen /reinschreiben, Fremde dürfen nur reinschauen

---

## Wer hat meiste Zauberkräfte?

Superuser([[Vorlesung 12|Root]]):

Der König im Computer! Er darf alles.

Sudoer (Helfer mit Extra-Zauber):

Jemand, der für bestimmte Dinge die Superkraft ausleihen kann (z. B. mit sudo)  

---

## Übungsblatt 3

  

Aufgabe 3.1

1. **Ziegen sie alle Umgebnungsvariablen an.** Der Command ist printevn.  
    

1. **Fügen Sie eine neue Umgebungsvariablen MYVAR mit dem Wert HelloWorld hinzu.** **???**  
    

1. **Überprüfen Sie, ob die Umgebungsvariable MYVAR korrekt gesetzt wurde.**  
    **???**  
    

1. **Legen Sie im Home-Verzeichnis ein** ==**Unterverzeichnis**== **skripte an.**  
    **Legen Sie darin ein** ==**Skript**== ==**[hallo.sh](http://hallo.sh/)**== **an mit dem Inhalt** ==**echo “Hallo”**== **und setzen**  
    **Sie Ausführrechte. Versuchen Sie, das Skript von unterschiedlichen Verzeichnissen**  
    **aus auszuführen.**  
    **Erweitern Sie die Umgebungsvariable PATH um das neu angelegte Verzeichnis und**  
    **sehen Sie sich nun den Inhalt der PATH-Variablen an. Versuchen Sie jetzt erneut,**  
    **das Skript von unterschiedlichen Verzeichnissen aus auszuführen.**  
    **Welchen Unterschied stellen Sie fest?**  
      
    Ich würde mit mit [mkdir Skripte] ein ==Unterverzeichnis== an.  
    Dann mit dem touch befehel einen datei ==name hallo.sh  
    ====So mit Nano kann ich datei hallo.sh mit werten== ==[befüllen.](http://befüllen.In)== ==Ich befülle es mit====[echo “HELLO”]==.  
      
    Ich habe keine Ahnung WIE PATH FUNKTIONIERT.

  

Aufgabe 3.2

  

1. **Erstellen Sie eine Datei namens myfile.txt. Sehen Sie sich mit dem ls-Kommando**  
    **die Rechte an. Setzen Sie die Lese- und Schreibrechte für den Benutzer und die**  
    **Gruppe und sehen sich die Rechte erneut an. Was hat sich verände**  
      
    So mit dem Befehl touch myfile.txt erstelle ich die datei.  
    Mit ls -l sehe ich die rechte, was die datei hat meisten steht da  
    rwx-wx-r-x Datei-name Datum und so weiter und so  
      
    Jetzt ist die Aufgabe die Rechte zuverwalten.  
    mit chmod kann ich die Rechte verwalten.  
    Also chmod o + r, habe ich rechte für others hinzugefügt.  
    

1. **Legen Sie eine Datei [script.sh](http://script.sh/) an, die das aktuelle Datum ausgibt. Versuchen Sie,**  
    **das Skript auszuführen. Geben Sie dem Skript nun das Ausführungsrecht für alle**  
    **Benutzer und führen Sie es erneut aus. Welchen Untershied gibt es?**  
      
    Genau so wie auf der aufgabe 1, muss man mit chmod x, rechte hinzufügen. Da eine sh-Datei automatisch keine rechte gibt.  
      
    

1. **Erstellen Sie ein Verzeichnis shared_dir und setzen Sie das sticky-Bit.**  
    **Was bewirkt das sticky-Bit und wofür wird es eingesetzt?**  
      
    Das heißt der sticky bit erlaubt nur den Root User Oder eigentümer, die Datei zu löschen.  
    

Aufgabe 3.3

  

1. Was sind Umgebungsvariablen und wozu werden sie verwendet?  
      
    

1. Welche Umgebungsvariable gibt den aktuellen Benutzer an?

1. Was bedeuten die Optionen u, g, o in den chmod-Befehlen?

1. Erklären Sie den Unterschied zwischen symbolischem und absolutem (oktalem)  
    Setzen von Datei- und Verzeichnisrechten

1. Wie können Sie den aktuellen umask-Wert anzeigen, und was bedeutet er für neue  
    Dateien?

1. Erklären Sie die Besonderheiten des Users root. Wie wird er noch genannt?

## Siehe auch

- [[Vorlesung 3]]
- [[Vorlesung 7]]
- [[Vorlesung 8]]
- [[Vorlesung 9]]
- [[Klausur]]
