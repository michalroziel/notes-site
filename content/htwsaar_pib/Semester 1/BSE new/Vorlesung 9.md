```Bash
v9 - Kontrollstrukturen:
------------------------
- if
- if ... else
- if ... elif ... else
- Kommando test
- Integer test
- Zeichenketten (Stringvergleich) test
- Operatoren zum testen des Dateityps
- Operatoren zum Testen der Zugriffsrechte
- Operatoren zum Testen von charakteristischen Eigenschaften
- Negation, UND, ODER
- Short-Circuit-Test
- case
- Schleifen (for, while, until)
- Kontrollierte Sprünge (continue, break ,exit)
- Endlosschleifen
```

---

## if / if … else / if … elif … else

```Bash
1 # Demonstriert eine Verzweigung mit if
2 # Name: aif1
3 # Benutzer in [[Vorlesung 12|/etc/passwd]] suchen ...
4 if grep "^$1" /etc/passwd
5 then
6 # Ja, grep war erfolgreich
7 echo "User $1 ist bekannt auf dem System"
8 exit 0; # Erfolgreich beenden ...
9 fi
10 # Angegebener User scheint hier nicht vorhanden zu sein ...
11 echo "User $1 gibt es hier nicht"
```

---

## Test

  

![[/image 15.png|image 15.png]]

## Siehe auch

- [[Vorlesung 7]]
- [[Vorlesung 8]]
- [[Umgebungsvariablen]]
- [[Klausur]]
