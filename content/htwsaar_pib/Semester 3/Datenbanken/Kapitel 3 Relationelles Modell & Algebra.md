[[Datenbanken]]








# Umsetzung schwacher Entity Typen

Ein Schwacher Entity Typ wird zu eigener Relation 
- übernimmt Schlüssel des übergeordneten starken EntityTyps uund ergänzt ihn um die unterscheidenden Attribute 
- 




# Eliminierungs- und Anfrageübung Musik-Streaming-Dienst 
Die Relation publish kann elimiert werden, da sie aus einem 1:N -Beziehungstyp resultiert:
Records : __[ RecordId]__  , ...


# 3.3 Relationale Algebra 
Wie können wir Daten extrahieren ? d.h Anfragen auf 


## Selektion 
***Selektion*** o (sigma) wählt Tupel (Zeilen) aus einer Relation R anhand einer Selektionsbedingung aus. 

$\sigma$ [ Location = Ecuador] ([[Studenten]])  
$\pi$  Die Projektion Pi wählt Attribute aus einer Relation aus 

### Beispiel

 $\sigma$[ Semester = 1 ] ($\sigma$[ Vorname "Moritz" ([[Studenten]])])
$\equiv$
 $\sigma$[Semester = 1 und Vorname = "Moritz"] ( Stundenten)
 $\equiv$
$\sigma$[Vorname = "M" ] ( $\sigma$  [Semester = 1 ](Studenten) )


# Umbennenung von Relationen und Attributen 

Beispiel von RecordId, MediumId und DiskNumber 

## Kandidatenschlüssel vs Primärer Schlüssel 
Die Menge der Kandidaten die wir wirklich auswählen, nennen wir Primärer Schlüsel 

Die Projektion $\pi$ liefert keine Duplikate 

Mit dem umbennenungsoperator $\rho$ können wir eine Namensänderung durchführen, damit keine relationen mit gleichen Namen gegeben sind 



### Equi Join $\Join$
verwendet das joinprädikat $\theta$ nur Vergleiche mittels "=", spricht man auch von einem Equi-Join 

## Cross Product $\times$
Lässt sich durch geschachtelte Schleifen ( nested loops ) implementieren 

## Outer Join 
Wir haben : *full outer join*, *right outer join* und *left outer join* 
right left gibt an, weo die tupel bleiben ewnn sie keinen join partner finden 

## Natural Join…
was passiert, wenn bei einem natural join keine gemeinsamen attribute vorhanden sind ? 
Das Join Prädikatist dann leer, und es wird als immer wahr angenommen 



# Operatorbaumdarstellung 
Ausdrücke der relationalen Algebra lassen sich alternatic auch als sogenannte Operatorbäume darstellen 

$\Join$ [s.MatrNr = h.Matr] $\equiv$ $\sigma$ [s.MatrNr = h.MatrNr] ( S x h )

Wir können mittels der relationellen Algebra nicht immer alle "interessanten" Anfragen darstellen



