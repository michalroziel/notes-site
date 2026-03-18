

## Caching in der Edge 

- In-Memory Cache für schnelle Zugriffe
- Properties-Dateien für Recovery nach neustart/crash

> Der zentrale fachliche Einstieg ist `EdgeFileService.[[Java]]`

### Request : 

Client fragt eine Datei beim Edge an : 
1. Edge normalisiert den Pfad 
2. Im Edge Memory cache nachschauen : **getFresh** im `EdgeFileService.[[Java]]`
3. Falls nicht abgelaufen : `HIT`
4. Wenn nciht : Datei vom Origin holen, hash prüfen, in dne cache legen, snapshot auf disk, dann MISS 

> Der X-Cache Header kommt aus `EdgeFileController.[[Java]]`

## Was liegt in Memory ? 
Im **RAM** liegt der aktive Arbeitscache. Dieser wird durch EdgeCache abstrahiert und kann als `LRU` oder `LFU` 

#### Cache Entry : - `CacheEntry.java`
- [[Body]] der Datei als byte[]
- contentType
- sha256
- expiresAtMs

>[!important]
>Der Cache Zustand wird zusätzlich in einer Properties Datei geschrieben 
- jeder Cache-Eintrag wird als entry.N.* gespeichert
- der [[Body]] wird Base64-kodiert
- expiresAtMs wird mitgespeichert
- abgelaufene Einträge werden gar nicht persistiert

## Was liegt in den Properties ? 
1. Cache Content
2. Runtime Config -> region, TTL, maxEntries 

Das Laden von Cache Entries passiert in `EdgeFileService.[[Java]]`

### Wie funktioniert TTL und Eviction ? 
Die Standardwerte kommen aus `application-edge.properties (line 12):`

- TTL standardmäßig 60000 ms
- max. 100 Einträge
- Strategie LRU

Zusätzlich gibt es Präfix-Regeln in` TtlPolicyService.[[Java]] (line 63):`

- längster passender Präfix gewinnt
- sonst gilt die Default-TTL

