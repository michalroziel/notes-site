  

- Collections sind Datenstrukturen die man oft nutzt.

  

> [!important] Es gibt stastische und dynamische Datenstrukturen

  

  

  

## MinHeap

  

- vollstaändiger binäre Baum

- WErt jedes Knoten ist kleiner als der wer tseiner Kinder

- enqueue , dequeue → $O(log n)$

  

  

  

# Java Collections FrameWork

  

- Sammlung von Klassen und Interfaces, welche Datenstrukturen zur Verwaltung von DatenObjekten implementieren.
    
    - Listen, Queues, Bäume
    
    - DatenContainer, Datensammlungen
    
    - inkl. effizienter [[Algorithmen]]
    

- wiederverwendbar

- Reduzierung des Implementierungsaufwands

  

  

  

## ==Collection<E>- Interface==

### Collection erstellen - Achtung ! → Man kann hier ==KEINE== String ArrayList jinzufügen

```Java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world!");


        Collection<Number> c = new ArrayList<Number>();
        c.addAll(new ArrayList<Integer>());
        c.addAll(new ArrayList<Double>());
        
        
        c.addAll(new ArrayList<String>());
        
        
        
    }
}
```

  

```Java
Collection< ? super E> 
```

  

  

  

  

## Maps

  

- Hashmap

- LinkedHashmap

- Treehashmap