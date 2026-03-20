[[Programming 3]]
# Situation : Tilgung von technischen Schulden

## Besser : gleich bei der Entwicklung gut wartbaren Code schreiben

# Refactoring als Frühjahrsputz
Refactoring verbessert die Qualität und Wartbarkeit des Codes

Ziel : Senkung der Kosten für die Weiterentwicklung 
Die Art der Codebasis macht einen großen Unterschied, wie Änderungen vorgenommen werden
Verbesserungen sind oft eine Schicht über der anderen, was die Durchführung kompliziert macht

> Refactoring zielt darauf ab, dass Änderungen die Komplexität des Codes nicht steigern

Jedes kleine Refactoring hat kleine Auswirkungen, eine ganze Reihe von Änderungen kann zu großen Auswirkungen führen 
Bei kleineren Refactorings ist es wahrscheinlicher dass weniger schief geht 

> Die interne Struktur wird geändert, ohne das Äußere Verhalten zu ändern 

Gutes Refactoring spart nicht nur Kosten, sondern reduziert auch technische Schulden

Bei Updates : Ist die Codestruktur refaktorisiert, um neue Ergänzungen einfach zu gestalten ? 

Next Week : [[Zuverlässiger Code durch TDD und Unit-Testing]] 

# Refactoring != Cleanup 
Cleanup ist einfaches aufräumen von Code
Refactoring : Struktur durch regelmäßges Vorgehen *methodisch* zu erweritern / Verbessern 


# Rename Field 
Code Smells : Kontostand mit Buchstabe "b" bennen ist kein clean Code
Magic Numbers vermeiden  : [[MATH]].PI verwenden anstatt 3.14159 einzugeben 

```
private static final double PI = 3.14159
```

# Replace Conditionals with Polymorphism 

## Open-Closed Principle
Offen für Erweiterungen, verschlossen für Modifizierungen 

> Gezielte Umstrukturierung zur Verbesserung der Wartbarkeit und dem Ermöglichen von Erweiterungen 

### Regelmäßiger, iterativer und kontinuierlicher Prozess zur Vermeidung technischer Schulden

## Eine schwer verständliche Codebasis, bremst aus 
Spätestens dann wenn der eigene Workflow ausgebremst wird, sollte über Refactoring nachgedacht werden 
- TDD
- Litter-Pickup Refactoring
- Comprehension-Refactoring

### Zwei-Hüte Metapher
#### Refactoring
Jede änderung ist klein und macht verursacht Großen Veränderungen

#### Funktion hinzufügen
Jede Änderung ist eine Erweiterung 
Es ist ratsam, Änderungen klein zu halten 

> Beim Programmieren kann man oft Hüte wechseln, man trägt aber nur einen 


### Refactoring zur Verständnisverbesserung 
Gute Entwickler legen Wert auf Clean Code

> [! Ward Cunningham :]
> " Whenever you have to figure out what code is doing, you are building some understanding in your head. Once you've built it, you should move that understanding into the code so nobody has to [[build]] it from scratch in their head again"
- Mit Teamkollegen über den Code sprechen 

> Pfadfinder-regel : Code in einem bessern Zustand hinterlassen, wie man ihn gefunden hat 

> Often, when a team learns, code written a few months ago can now seem lacking, and should be fixed!
> Fixing right away is a good move, if its simple of id the fix will make it easier to add the feature you wanted to add



## Refactoring als Vorbereitungsmaßnahme
Neue Funktionalitäten passen oft nicht in bestehende Strukturen
! Preparatory Refactoring can be done when adding a new feature 



### Refactoring als Langfristmaßnahme 
Ziel : stabile und wartbare Arhcitektur schaffen 
Ein solches Refactoring kann mehrere Monate dauern 
Beispiele : Ersetzen eines großen Moduls 
Änderung des [[Datenbank]]-Persistenz-Frameworks


### Refactoring als eine Schönheitskur ? 
Refactoring erleichtert das Veständnis 

> ZIEL : Langristige Einsparungen und Beschleunigung künftiger Anpassungen
> Refactoring und neue Funktionalitäten im Einklang 


> Refactoring -> Clean Code && Faster Delivery 