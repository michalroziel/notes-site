[[Automatisierte SowareEntwicklung]]

Statische / Dynamische CodeAnalysen 

Linter 

Debugging 

### GrundIdee 

Untersuchung des QUellCodes in Hinblick auf Eigenschaften wie Korrektheit, Robustheit, Sicherheit und Leistung


#### Korrektheit 
#### Dynamische CodeAnalyse 
Analyse des Programms während der Laufzeit
Beispiele : Debugger, Profiler 

**Prinzipien :** 
Laufzeitüberwachung
Instrumentierung : Hinzufügen von Code zur Überwachung zur Laufzeit 


#### Statische Analyse 
Analyse des Codes ohne dessen Ausführung 
Beispiele : Linter, Sicherheits-Scanner, 

**Prinzipien :** 

Überprüfung des QuellCodes ohne dessen Ausführung



# Vor und Nachteile der Dynamischen CodeAnalyse 

### Was ist Dynamische CodeAnalyse ? 
-> Analyse des Codes, mit dessen Ausführung 
Auch genannt DAST - Dynamic Application [[my-notes-site/node_modules/typescript/SECURITY|SECURITY]] Testing 
### Hauptziele der  Dynamischen CodeAnalyse
-> Untersuchung einer Ausgeführten Anwendung auf potentielle Schwachstellen 
-> Schädliches Verhalten kann gekennzeichnet werden 

Findet Memmory LEaks, Performance Bottle NEcks 

### Vorteile 

Kann MEmmory LEaks und NullPointer Exceptions finden 


### Nachteile 

Qualität der Analyse hängt von den [[remote-notes/sem3/mikro/Tests/Tests|Tests]] ab -> schlechte [[remote-notes/sem3/mikro/Tests/Tests|Tests]], schlechte Ananlyse 

Schwer bei nicht-deterministischen Verhalten : Zufall ist schwer zu reproduzieren 


```Java

public class DynamicAnalysisExample {

    public static void main(String[] args) {

        String[] names = {"Anna", null, "Ben"};

  

        for (String name : names) {

            // Laufzeitfehler: name.toUpperCase() wirft NullPointerException bei null

            System.out.println("Name in Großbuchstaben: " + name.toUpperCase());

        }

    }
```



JKOKO -  OpenSource Code Coverage Tool [[Java]] 
ByteCode vor MEssung verändert 
JVM - [[Java]] Agent instrumentiert 
[[Maven]] Support 
Tool stellt Report Zusammen 
Goals : checks setzen, sonst failed der [[build]] 



# Vor und Nachteile einer Statischen Codeanalyse

## Was ist statische Codeanalyse ?
-> Wird bei Übersetzung durchgeführt 
-> QuellText wird einer Reihe von definierten [[remote-notes/sem3/mikro/Tests/Tests|Tests]] unterzogen 

### Hauptziele statische Codeanalyse 
- Früherkennung von Fehlern

- Einhaltung von Standards 

- Verbesserung der CodeQualität 

- Sicherheitslücken zu vermeiden
	- SQL Injections

## Vorteile der statischen CodeAnalyse 

Keine Ausführung Benötigt 
Integrierbar into Workflows 
Frühe ERkennung von Fehlern 
	Spart Kosten und Zeit 
Vermeiden Redundanzen, unused variables, etc. 

Auch gut beim unvollständigen Code 

### Nachteile 

False Positives - falsche Meldungen 
nur syntaktische und strukturelle Probleme
Probleme können übersehen werden -> dynamisch erzeugter COde ? 

Ein " Problem " kann eventuell bewusst so programmiert sein 

```Python
def berechne(x):

    if x == 0:

        return 0

    return x * 2
```
-> kein else fall Nötig, Toll Könnte melden dass das else nciht präsent ist ->  
" *unvollständige Logik*  "

Code Conventions ändern sich -> nicht immer aktuell 

KonfigurationsIntensiv 



Speicherfehler, Semantische Fehler, Coding COnventions, StilRegeln, 
Schwer Erkennbar : Zugriffs Probleme, DEADLOCKS, Laufzeit-Probleme 
API Zuzgriffe können schwer sein 

API : Kontext-Wissen Fehlt oftmals 
Prettier : Code Formatierung 
Sona, Embold (MVC Model)
JetBrains IDE [[Static]] analysis
SQL Schnittstellen 
Linter : NAch vordefinierten Regeln geschrieben 

