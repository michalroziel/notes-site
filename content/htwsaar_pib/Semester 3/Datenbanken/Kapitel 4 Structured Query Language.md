[[Datenbanken]]
Das relationelle Modell und die relationelle Algebra bilden das theoretische Fundament von SQL 

## Wichtige Unterschiede :
In SQL gibt es Duplikate ! in der RA werden Mengen betrachtet

### Datentypen in SQL : 
int, smallint, bigint
float
char(n)
varchar(n)
date,time,datetime
money
blob / blob für große Binär- bzw Textdaten

> Die Verfügbarkeit und Benennung der Datentypen unterscheidet sich (leider) zwischen RDBMSs
> In der VL : MS SQL Server und SQLITE


## JOINS 

## Natural Join 

```
SELECT * 
FROM Professoren, Vorlesungen
WHERE Professoren.PersNr = Vorlesungen.PersNr

SELECT * 
FROM Professoren NATURAL JOIN Vorlesungen
```
### Woher weiß SQL, dass auf PersNr gejoint wird ?
Durch einen Natural Join werden direkt Attribute mit gleichem Namen gejoined 


## Allgemeiner Join 
Wir nennen die Tabellen in der *FROM* Klausel, 
Join-Prädikat wird in der *WHERE* Klausel gennant, oder : *JOIN ON* verwenden 

```
SELECT * 
FROM Professoren, Studenten
WHERE Professoren.Name = Studenten.Name

SELECT * 
FROM Professoren
JOIN Studenten
ON   Professoren.Name = Studenten.Name
```

## Mengen Operationen : 
- UNION
- INTERSECT
- EXCEPT 
```
SELECT Name
FROM Studenten
EXCEPT
SELECT Name
FROM Professoren
```



## 4.5 Datenmanipulation 
Durch die DML lönnen wir Tuperl Aktualisieren, EInfügen und sogar löschen!

Das RDBMS - Relational Database Management System überprüft bei den Operationen die jeweiligen Integrittätsbedingungen( Bsp : Primärschlüssel oder Fremdschlüssel)
und verweigert bei Verletzung die Ausführung 

```
	INSERT INTO Professoren 
		VALUES (183422, 'Carla' , 'Cannon', 'Literatur)

	INSERT INTO Professoren ( Name, Fach, Vorname, PersNr)
		VALUES ('Carla', 'Columna', 'Literatur, 183422)
```

```
UPDATE Studenten
SET Name = 'Cole'
WHERE PersNr = 19866

UPDATE Studenten
SET Semester = Semester + 1
```
```
DELETE FROM STUDENTEN
WHERE Fach = 'Datenverarbeitung'
```

Umbennenung vgl S.70
Korrelierte / Unkorrelierte Anfragen S.71 


## 4.6 Äußere Joins  

Professoren und [[Studenten]] mit gleichem Namen ( erhaltung aller Professoren)

```
SELECT * 
FROM Professoren LEFT OUTER JOIN Studenten
WHERE Professoren.Name = Studenten.Name

```
Full Outer Join : ( Erhaltung aller Tupel)
```
SELECT * 
FROM Professoren FULL OUTER JOIN Studenten
WHERE Professoren.Name = Studenten.Name
```

## 4.7 Gruppierung & Aggregation 

Hiermit lönnen wir Aggregat-[[Funktionen]] auf Gruppen von Tupeln anwenden 
Beispiele : 
	Durchschnitts Note je Vorlesung 
	SWS je Professor
	Anzahl der [[Studenten]] je Fach 

Fächer Absteigend Sortiert nach Anzahl der [[Studenten]] : 

```
SELECT Fach, Count(*) as ANZAHL 
FROM Studenten
GROUP BY Fach
ORDER BY ANZAHL DESC
```
Namen von Professoren in versch Fächern : 
```
SELECT    Name, Fach, Count( * )
FROM      Professoren
GROUP BY  Fach, Name 
```

## 4.8 Quantifizierung 

```
SELECT * 
FROM Professoren p
WHERE EXISTS (
    SELECT * FROM Studenten s WHERE p.Vorname = s.Vorname
);
```
Hierbei ist dies eine Korrelierte Anfrage.


Geben Sie aus wie viele Künstler es aus jedem Herkunftsland gibt, absteigend sortiert nach der ermittelten Anzahl.
```
SELECT  DISTINCT Location , Count(*) As ANZAHL  
FROM Artists  
Group By Location  
ORDER BY ANZAHL DESC
```







