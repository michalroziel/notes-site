[[Programming 3]]
# Code Smells 
## Beispiele für Code Smells
- zu viele geschachtelte if Abfragen
- variablen mit schlechten Namen
- Methoden name " calc"
- 3.1459 statt [[MATH]].PI

### Wie wirkt sich das auf die Weiterentwicklung aus ?
- schwere, langsame Wartung 

# Technische Schulden
### Interne Qualitätsmängel durch Ballast cruft
- "Schuld" für die man Zinsen zahlen muss
- Die meisten Softwaresysteme enthalten unnötigen Ballast (engl. cruft)

## Zinsen zahlen
wir müssen ein Feature hinzufügen, mit dem aktuellen code braucht man 6 Tage dafür, mit guten Code würde es 4 Tage dauern
Die zwei zusätzlichen Tage sind die Zinsen für den ineffizienten Code 

Ineffiziente Stellen verlangsamen den Code 
## Haupttypen technischer Schulden 
- Absichtliche technische Schulden
	- Bewusstes eingehen von Schulden um Deadlines zu schaffen, provisorische Lösungen
	- Oft bleibt es bei der absichtlichen Lösung mit Schulden

- Unabsichtliche Technische Schulden
	- Sehr hohe Zinsen, unbewusst dass der Code schlecht ist

	Leichtfertig (Reckless) eingebaute Schulden vs Verantwortungsvoll (Prudent) eingebaute Schulden 

### Jede Software hat Schulden, wir wissen erst später was wir hätten machen sollen

Technical Quadrant von Martin Fowler 

> [!Technical Quadrant von Martin Fowler ]
> 

Technische Schulden haben Negative Auswirkungen auf die EntwicklungsQuality 

### Es ist manchmal in Ordnung technische Schulden einzugehen 


# Clean Code
CC zielt darauf ab, lesbaren und wartbaren Code zu schreiben, der langfristige Effizienz und Qualität sicherstellt. 

## Prinzipien des Clean Code 
einheitliche Formartierung
Zielgerichtete Kommentare

### Lesbarkeit und Verständlichkeit 
 Starke Veerschachtelung machen den Code nur schwer lesbar
 Early return statements 
 Auslagerung von Code in eigene Methoden 
 Kleine, spezialisierte Methoden 
 Klar benannte Variablen Namen helfen bei der Verständlichkeit des Codes
Magic Numbers vermeiden 
Einheitliche Formatierung( Einrückung von unregelmäßigen Leerzeichen)



# Ihre Fragen, unsere Antworten 

Methodenlänge und Parameter sollten standarisiert sein 
Abkürzungen sind manchmal auch von Vorteil 

Mit Technischen Schulden hat ein [[Scrum]]-Team eine kleinere Velocity wie ohne.


# Liebes Lern-Logbcuh 

