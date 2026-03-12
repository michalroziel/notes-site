v3 - Umgebungsvariablen, Datei- & Verzeichnisrechte:  
----------------------------------------------------  
- Was sind Umgebungsvariablen  
- PATH-Variable, Kommando which  
- Inodes  
- Datei- & Verzeichnisrechte  
- Manipulation von DR & VR (chmod)  
- uid-, gid- & sticky bit  
- umask  
- Besondere Linux-User

  

Stell dir vor, du hast Schubladen mit Etiketten drauf, z. B. “Dein Zuhause” oder “Deine Sprache”. Diese Etiletten heißen **Umgebungsvariablen.**

Beispiele:

- HOME —> Zeigt dir, wo dein “Zuhause” im Computer ist.

- PATH —> Sagt dem Computer, wo der Programme finden.

---

  

## Was sind Umgebungsvariablen

  

eine **Umgebungsvariable** ist eine Variable im Betriebssystem, die Programme und Skripte nutzen, um Einstellungen oder Pfade zu speichern Vordefinierte Umgebungsvariablen sind z. B. HOME, PATH, PWD, LANG

---

## Inodes

Was sind Indoes ?

Inodes sind eigentlich metadaten, da sind daten wie zugriffsrechte, dateityp und größe gespeichert! Habe einige nummer und sind immer mit einer datei verbunden

---

## PATH-Variable, Kommando which

  

Mit dem WHICH Befehl sucht er die ausfürbaren programme die im path sind. Die programme die nicht im Phat drin sind müssen mit dem Absoluten pfad aufgerufden werden oder in de n$PATH hinzu gefügt werden.

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

  

Beispiel: Mit einem Zauberspruch “chmod” kannst du sagen, wer was darf!

  

![[/image 9.png|image 9.png]]

---

  

## Besondere Zauberrechte

1. Setuid (Ausführer-Zauber): Wenn jemand dein Programm benutzt, tut er es mit deinen ZAuberkräften

1. **SETGId** (Gruppen-Zauber): Neue Sachen in deiner Schatzkisten gehören automatisch deiner Gruppe.

1. **Sticky bit** (klebe-Zauber): Nur der Schatzmeister (du) darf Sachen rausholen.

im Command ist nur ein x.

---

## Standardrechte und umask

Wenn du eine neue Schatzkiste machst, hat sie automatisch gewisse Regel:

**Datei (Blatt** Papier): Du und deine Freunde dürfen lesen / schreibe, Fremde dürfen nur lesen.

**Verzeichnis** (Kiste): Du und deine Freunde dürfen reinschauen /reinschreiben, Fremde dürfen nur reinschauen

---

## Wer hat meiste Zauberkräfte?

Superuser(Root):

Der König im Computer! Er darf alles.

Sudoer (Helfer mit Extra-Zauber):

Jemand, der für bestimmte Dinge die Superkraft ausleihen kann (z. B. mit sudo)