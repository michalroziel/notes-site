
> Gezielter [[test]] für Crash Recovery des Edges, nicht von dem ganzen Tech Stack 


Grundsätzlich wenn der Edge abstürzt, durch `kill -9`, dann soll dieser wieder gestartet werden, und der persistente Zustand wieder hergestellt werden. 

Unterschied zu **S5** : 
- hierbei wird nur die Edge Neu gestartet, 
- nicht die recovery des gesamten systems 


## Ablauf : Aufbau ähnlich zu S5 : 

1. alte services beenden 
2. origin edge und router neu starten 
3. Prepare [[test]] State : 
	1. register Edge @ Router
	2. [[test]] File anlegen
	3. TTL neu setzen 
4. warm cache
5. hard kill Edge with `kill -9`
6. Nur diese edge wird neu gestartet, nur hier wird die Zeit gemessen 

7. Danach wird geprüft:
    - Cache-Zugriff ist direkt wieder HIT
    - Dateiinhalte sind unverändert
    - Recovery dauert < 10 Sekunden



