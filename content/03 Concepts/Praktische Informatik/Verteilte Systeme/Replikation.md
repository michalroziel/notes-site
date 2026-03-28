
## Definition
Replikation bedeutet, dass Daten oder Dienste mehrfach auf verschiedenen Knoten eines Systems vorhanden sind.

## Warum das wichtig ist
Replikation verbessert Verfügbarkeit, Ausfallsicherheit und teilweise auch die Leseleistung.

## Vorteile
- höhere Fehlertoleranz
- bessere Verfügbarkeit
- geringere Latenz in manchen Szenarien

## Nachteile
- Konsistenz wird schwieriger
- Aktualisierungen werden komplexer
- zusätzlicher Koordinationsaufwand

## Verwandte Konzepte
- [[Verteilte Systeme]]
- [[Fehlertoleranz]]
- [[Skalierbarkeit]]
- [[CAP-Theorem]]
- [[Eventual Consistency]]

## Verwendet in
- [[CDN]]
- [[Verteilte Datenbanken]]
- [[Mini CDN]]

## Beispiel
Ein CDN repliziert statische Inhalte auf mehrere Edge-Server, damit Nutzer Daten von einem nahegelegenen Standort abrufen können.

## Gesehen in
- [[Verteilte Systeme - Vorlesung 01]]

## Offene Fragen
- Was ist der Unterschied zwischen synchroner und asynchroner Replikation?
- Wie werden Konflikte aufgelöst?