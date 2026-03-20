

nasa website -> sonnen position 
	-> JPL -> jet propulsion lab 
		API zur Sonnenposition 

Sonnenstrahlung -> unterschiedliche Schemas 
	NASA -> API zur bestimmung von bestimmten Ort zur bestimmten Zeit 

Deutscher Wetterdienst (DWD) Sonnenstrahlung -> Data nur via .zip 

Untersuchen, woher können wir die Sonnenstrahlung bagreifen und darstellen 


nicht schlimm wenn nicht feature-complete 

Website : Modular Programmmieren, BSP : easy change of API 
SOnnenstrahlung : einfaches wechsel des Modells, der Schnittstelle 

*[!] nicht Quick and Dirty* 

## Nasa Jet Propulsion Lab 
API Name : Horizons 



## D3.js
kompliziert 
Support service zu kaufen 

## Three.js 
angenehm zu lernen 

## openJsCad 
Werkzeug um auch CAD Objects zu erstellen 



## Nasa the power project - Sonnenstrahlung

Data Quelle zum Zugriff auf Sonnenstrahlung 
Asimuth und Höhe  
Asimuth -> Winkel

Modell eines Gebäudes, Schattenwurf der Oberfläche des Gebäudes 
	nice to have, aber nicht nötig 

Darstelllung der Sonne auf einer Halbkugel, aufgrund von Asimuth und Evelation 
Asimuth und Evelation, Betrachter in der Mitte 


## EntwicklungsWerkzeuge 
**Node JS** um Versionen von Bibliotheken zu verwalten 

npm direkt dabei ? 

```
npm --version
```


### WebStorm IDE 
nicht alles via click -> 


**JS** -> Läuft direkt auf dem Browser, gravierende Nachteil : Implizite DatenTypen kann man addieren -> chaotische Programme 

## VUE JS 
software veraltet, erfahrung veraltet nie ! 


## TypesScript 
-> Type Warnings, keine Standarisierung, Änderung von TS ist subtil aber tut weh :( 

## Deployment 
Website Deploy via HTW server 
Jeder muss Software via master branch deployen können 




## Wichtig : 
Automatisierte [[remote-notes/sem3/mikro/Tests/Tests|Tests]] 
	UNIT [[remote-notes/sem3/mikro/Tests/Tests|Tests]]


Node JS 
ausschließlich auf dem Browser 

CROSSOVER Problem 
	Proxy zwischen unserer Domain und JPL API benutzen Gestelltes Proxy 
	JPL bietet keine HTTP Header, damit keine andere domain außer Nasa darauf zugreift 



unsere Software spricht nicht mit API sondern mit der Proxy 

JSX Graphs : Curve plotting 
	Beschränkung : Überwiegend für 2D projektionen 





## Caching 
Keine DB, dafür localStorage 

developer.mozilla.org : localStorage 

Erst sinnvoll wenn Sun Path Diagramm zu PDF exportieren 





