```TOML
v8 - Datentypen & Variablen:
----------------------------
- Definition einer Variablen
- Auslesen einer Variablen
- Variable als Konstante definieren
- Integer Arithmetik (sh, bash)
- Kommando-Substitution
- Zeichenketten
- cut
- filter tr
- sed
- Effekt Single-/Double-Quotes
- Arrays
- export von Variablen
- Umgebungsvariablen
- Automatische Variablen der Shell (!!)
```

  

---

## Definition einer Variablen

```Bash
$ Name="Michal" # Name hat den String Michal 
```

---

## Auslesen einer Variablen

```Bash
$ echo §Name \#Die Variable muss immer mit $ beginnen! 
```

---

## Variable als Konstante definieren

```Bash
$ readonly Name 
```

---

## Integer Arithmetik (sh, bash)

```Bash
expr 4 + 6 # Als ergebniss bekommen ich 10 raus 
expr 3 \* 4 # Wichtig hier bei ist der Back slash 
```

---

## Kommando-Substitution

```Bash
Var1=10 
Var2=20

Var3='expr $var1 + §var2'
echo $var3
```

---

## Zeichenketten ???

---

## cut

```Bash
cut -c1 \#Gebe mir die erste zeile an.
cut -c2-5 \#Hier nur die 2.stelle bis 5 stelle 
cut -C1,5,6 # Stelle 1. 5. 6. werden ausgeschnitten
```

---

## filter tr

```Bash
tr a b < Text.txt # jetzt werden alle wörter die A's beinhalten mit einem b  
									 # erstetzt Bsp. paar -> pbbr
```

---

## sed

```Bash
echo "ich habe Apfel" | sed 's/Apfel/Banane/' \#Ich mag Banane 

echo "Apfel, Apfel, Apfel" | sed 's/Apfel/Banane/g' # Banane, Banane, Banane

sed -i 's/Apfel/Banane/g' datei.txt \#ändert die datei!

sed '/Fehler/d' protokoll.txt # löscht den Wort Fehler von der Datei!
```

---

## Effekt Single-/Double-Quotes

![[/image 14.png|image 14.png]]

---

## Arrays

```Bash
array=(hallo Baby ASd) # Arrays erstellt 
echo "${array[0]}" # gibt dir die 0 stellte, also "hallo"
echo "${array[*]}" # gibt alles aus, also Hallo, Baby, Asd
array[3]="HALLLOOOO" # in der hallo Baby ASd HALLLOOOO
```

---

## Export / Umgebnungsvariable

```Bash
\#die variabelen die man erstellt sind locale varibale, dass heißt nur der 
\#der termial die du offen hast weisst was array ist ein neuer termial 
# kennt es nicht. 
# Um es eine umgebungs variable zu erstellen muss man den befehl export benutzen.

export array
```

---

## Automatische Variablen der Shell (!!)  

![[/image 1 5.png|image 1 5.png]]

```Bash
#!/bin/bash
echo "Skriptname: $0"
echo "Erstes Argument: $1"
echo "Zweites Argument: $2"
echo "Anzahl der Argumente: $#"

Skriptname: ./mein_skript.sh
Erstes Argument: Hallo
Zweites Argument: Welt
Anzahl der Argumente: 2
```