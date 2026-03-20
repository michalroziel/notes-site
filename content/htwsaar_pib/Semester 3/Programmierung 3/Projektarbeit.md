[[Programming 3]]
# Erfordernisse 
### mindestens :
jeder macht etwas 
Anwenden der VL Inhalte 

Pflegen von Anforderungen mittels priorisierten *Product Backlogs*
	"[[Scrum]] auf einem Bierdeckel erklärt"
Anforderungen in Form von [[User Stories]] 
***Github [[Projects]]*** aktivieren, dort die Zusammenarbeit machen 
Am Ende des Projekts ist klar, was umgesetzt wurde, was nicht 

Text-basiertes TextInterface 
	CLI : Picocli als Library 
	TUI : ein Menü in der Anwendung ( Scanner/Console/Lanterna)
***Das Interface ist, wie die gesamte Anwenung bestriebssystemunabhängig.*** 
Ein Graphisches Interface GUI ist nicht notwendig 

Anwendung kann Daten speichern und Laden !
Daten : Lokale SQLITE [[Datenbank]]
Saubere Trennung von Logik und TextInterface

JOOQ KEIN HIBERNATE  

#### Drei-Schichten-Architektur 
1. Präsentationsschicht 
2. Logikschicht
3. Persistenzschicht

Einfahce Wartung und Erweiterung der Anwendung  
BSP : Textoberfläche kann einfach mit einem GUI ersetzt werden 

### Anleitung 
[[Java]] -jar Datei muss ausführbar sein 
Anwendungsbeispiele, auf Fehler und Einschränkungen hinweisen 
>[! Wenn nicht möglich zu starten : Fail ]
## gute Projektarbeit :

Model View Controller - MVC, unterteilt Anwendung in 3 components 

- Model : 
	- Verwaltet Daten und Geschäftslogik
- View :


 Alternative : Model View Presenter - MVP, hierbei auch Model & View 
 
vgl  : [Martin Fowler :  GUI Architectures]( https://martinfowler.com/eaaDev/uiArchs.html)



## Projekte 

Vgl VL SLides - 13 vorgestellte Projekte 


## Empfehlungen 
Nicht eine Woche vorher Anfangen 
Testen ! 
vgl SWT : Inktementell und Interativ vorgehen 
keine Wissensmonopole inerhaln des Teams 

Sicherstellen, dass alle involviert, und auf dem neusten Stand sind.
Schnelle Reaktion auf Veränderungen
Förderung des agilen Mindsets 
Tägliche Besprechungen : Kurze, regelmäßige Besprechungen in denen alle über den Fortschritt informiert werden
Schaffung von Transparenz : vgl SWT 07.01.2025
Retroperspektive
Pair Programming oder Mob Programming 

[Making sense of MVP](https://blog.crisp.se/2016/01/25/henrikkniberg/making-sense-of-mvp)
[[Scrum]] ist etwas zu viel des Guten 
		Kanban ist schlank, ideal für kleine Teams und überschaubare Projekte 
	<<
## Abgabe 

Abgabe first am Freitag 28 Februar 18 Uhr 
Keine Fristgerechte Abgabe : nicht bestanden 
Github : Lesezugriff für : "martinburger"
Code - Maven Projekt, Github Actions 
Actions 
Project(Kanban Board)
Abgabeversion als Release 
Git-Tag : submission 
Releasetitel : Abgabeversion 

 URl- Github-Projekt
 <Anmeldename.zip>
 mamu01234.zip
 Ergebnis der Reflextion des Vorgehens und des Gelernten als Markdown-Datei
 <Anmeldename.md>

	! Vorlage bezüglich Reflextion folgt in den nächsten zwei Wochen 

Benotung der Projekte wird relativ Erfolgen 
Dinge bewerten, die man im Rahmen des Projekts lernen konnte 

Erkennbare Umsetzug der Kerninhakte aus den vorgegangenen Vorlesungen und Praktikumsaufgaben 

SOLID - Prinizipien für saubere [[Architektur]]
Es wird geprüft, obn der Code und die Arhcitektur sauber sind. 




## Beratung 

## Spaß 