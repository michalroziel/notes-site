
- End to End REcovery Test für den Stack aus Origin, edge, Router 
	- Nicht nur restart, sondern auch recovery von zustand der edge 


- Cache-Inhalt bleibt erhalten
- TTL-Policy bleibt erhalten
- Router kann wieder korrekt routen
- alles innerhalb von < 10s


Recovery Mechanismus  : EdgeRecovery Bootstrap 

Runtime Config & TTL Policy : EdgeRuntime State Store

Cache Entries : Edge Cache State Store


## Ablauf 

1. Stoppe alte Prozesse 
2. Origin, EDge und Router als exec JARs starten, nicht mit maven

3. Test State ERzeugen : 
	1. Edge beim Router registrieren 
	2. Test Datei anlegen
	3. setze TTL 

4.  EDge Cache Warm 

5. 10 000 requests schicken 

6. gesamten stack neu starten und zeit messen 

7. Prüfen : 
	1. Router liefert wieder `307` redirect. 
	2. file nach Edge Restart wieder `HIT`
	3. recovery Zeit < 10 selunden 


## wichtig : 

- Die 10 000 requests gehen an den `router` 
- ABER : `curl` folgt dem redirect nicht - `Option ausgelassen `
- Es wird geprüft ob das routing `funktioniert`

> Die Requests holen die Datei nicht 10 000 mal von der edge 

