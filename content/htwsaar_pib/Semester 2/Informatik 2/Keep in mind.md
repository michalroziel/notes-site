  

#

### Das Handshake Lemma

> [!important] $v∈V∑​deg(v)=2∣E∣$

  

  

# Breitensuche vs Tiefensuche

  

Die Wahl zwischen Tiefensuche (DFS - Depth-First Search) und Breitensuche (BFS - Breadth-First Search) hängt von den Anforderungen und Eigenschaften des Problems ab. Lass uns die Unterschiede und die Eignung beider Ansätze in diesem Kontext betrachten:

### Tiefensuche (DFS):

- **Vorgehensweise:** DFS erkundet einen Pfad bis zum Ende (d.h., bis es nicht weitergeht oder das Ziel erreicht ist), bevor es zurückgeht und alternative Pfade erkundet.

- **Vorteile:**
    
    - DFS ist speichereffizienter, da es in der Regel weniger [[Speicher]] benötigt (nur den aktuellen Pfad und einige Markierungen).
    
    - Es kann in manchen Fällen schneller zum Ziel gelangen, insbesondere wenn das Ziel tief in einer bestimmten Richtung liegt.
    

- **Nachteile:**
    
    - DFS garantiert **nicht** den kürzesten Weg, es sei denn, man durchsucht den gesamten Raum und vergleicht die Längen aller gefundenen Wege.
    
    - Es besteht die Gefahr, dass DFS in eine lange, unnötige Sackgasse geht, bevor es den tatsächlichen kürzeren Weg findet.
    

### Breitensuche (BFS):

- **Vorgehensweise:** BFS erkundet alle Knoten einer Ebene (alle Knoten mit gleicher Entfernung vom Startknoten) bevor es zur nächsten Ebene übergeht.

- **Vorteile:**
    
    - BFS garantiert den **kürzesten** Weg in einem ungewichteten Graphen, da es die erste gefundene Lösung auf der kürzesten Ebene ist.
    
    - Es ist systematischer und vermeidet unnötige Erkundungstiefe.
    

- **Nachteile:**
    
    - BFS benötigt tendenziell mehr [[Speicher]], da es alle Knoten in der aktuellen Ebene speichern muss.
    

### Anwendung auf das Labyrinthproblem:

- Da die Aufgabe explizit nach dem **kürzesten Weg** von s nach t fragt, ist die **Breitensuche (BFS)** in diesem Fall besser geeignet. Sie garantiert, dass der erste gefundene Pfad zum Ziel auch der kürzeste ist.
    
    ss
    
    tt
    

- **Tiefensuche (DFS)** könnte zwar auch das Ziel erreichen, aber sie könnte auch einen längeren Pfad zuerst finden und müsste dann möglicherweise viele weitere Pfade durchsuchen, um den kürzesten zu ermitteln.

### Fazit:

- **BFS** ist in diesem Szenario optimal, weil sie den kürzesten Pfad sicher findet.

- **DFS** könnte genutzt werden, aber sie bietet nicht dieselbe Garantie für den kürzesten Pfad, und du müsstest zusätzliche Maßnahmen ergreifen, um den kürzesten Pfad sicherzustellen (z.B. alle möglichen Pfade vergleichen).

Wenn du also sicherstellen möchtest, dass du den kürzesten Weg findest, ist BFS die richtige Wahl. Wenn du jedoch mit DFS experimentieren möchtest oder die Speicheranforderungen verringern willst, kannst du DFS verwenden, solltest aber im Hinterkopf behalten, dass du möglicherweise nicht sofort den kürzesten Pfad erhältst.

  

  

  

  

  

![[Screenshot_2024-08-16_at_13.59.13.png]]