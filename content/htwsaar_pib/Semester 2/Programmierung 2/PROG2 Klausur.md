  

  

> [!important]
> 
> ## Was kommt in der [[Klausur]] dran ?
> 
> 1. MC
> 
> 1. Recursion / Iterative Approaches
> 
> 1. [[Generics]] / Lambda Expressions / Streams
> 
> - [[Lambda Ausdrücke]]
> 
> - [[Collections]]
> 
> - [[C]] ( relativ wenig) vielleicht was mit Pointers

  

![[PHOTO-2024-08-31-19-31-52.jpg]]

> [!important] [[Funktionen]] gcc-Compiler
> 
>   
> [[Java]] Map, Queue, List, Tree -> [[Collections]], hauptsächlich [[Funktionen]] zum Hinzufügen/Entfernen  
> stream()  
> Predicate, Comparator  
> Sorting algorithms  
> [[C]] Basics

[[Klausur 2019]]

[[Zusatzaufgaben]]

[[Übungen in Vorlesungen]]

  

[[03-inner Classes]]

  

  

|   |   |
|---|---|
|||

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
|**Collection Type**|Implementation|Ordered|Sorted|Allows Duplicates|Null Keys|Null Values|
|`Set`|==`HashSet`==|No|No|No|N/A|Yes|
|`Set`|==`LinkedHashSet`==|Yes|No|No|N/A|Yes|
|`Set`|==`TreeSet`==|No|Yes|No|N/A|No|
|`Map`|==`HashMap`==|No|No|No (keys)|Yes|Yes|
|`Map`|==`LinkedHashMap`==|Yes|No|No (keys)|Yes|Yes|
|`Map`|==`TreeMap`==|No|Yes|No (keys)|No|Yes|
|`Map`|`Hashtable`|No|No|No (keys)|No|No|
|`Map`|`ConcurrentHashMap`|No|No|No (keys)|No|Yes|
|`List`|==`ArrayList`==|Yes|No|Yes|N/A|Yes|
|`List`|==`LinkedList`==|Yes|No|Yes|N/A|Yes|
|`List`|`Vector`|Yes|No|Yes|N/A|Yes|
|`List`|`Stack`|Yes|No|Yes|N/A|Yes|
||||||||
||||||||

### Explanation:

- **Ordered**: Maintains the order of elements as they are inserted.

- **Sorted**: Maintains elements in a sorted order based on natural ordering or a specified comparator.

- **Allows Duplicates**: Whether the collection allows duplicate elements (for `Set` and `List`) or duplicate keys (for `Map`).

- **Null Keys**: Whether the collection allows null keys (applicable to `Map` only).

- **Null Values**: Whether the collection allows null values.

### Notes:

- `HashSet` and `HashMap` do not maintain any specific order.

- `LinkedHashSet` and `LinkedHashMap` maintain the insertion order.

- `TreeSet` and `TreeMap` maintain elements in a sorted order.

- `Hashtable` and `ConcurrentHashMap` do not allow null keys or values.

- `TreeSet` does not allow null elements, and `TreeMap` does not allow null keys but allows null values.

- `ArrayList`, `LinkedList`, `Vector`, and `Stack` maintain the insertion order and allow duplicates and null values.

  

  

  

## Generics

- allows writing flexible,

- type-safe code

- reusable code

- allow types to be parameters when defining classes, interfaces and methods.

  

### Easy Example :

```JavaScript
package generics;

public class Box<T>{


    /**
     *
     * Here, Box can store any type T.
     */
    private T item ;

    public void setItem(T item ){
        this.item = item;
    }

    public <T> void printItem(T item) {
        System.out.println(item);
    }


}
```

  

- Here, _==printItem( T item )==_ is a generic method, that means that it is not bound to any type.

we can L

  

  

# ! Collections

### Keep in mind :

- when deleting elements while iterating over a [[Collections]] it cna get messed up
    
    - thats why a safe removal is important