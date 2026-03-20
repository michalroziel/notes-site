### ueb02

![[/image 29.png|image 29.png]]

```JavaScript
public class Ggt {

    public int ggtRekuriv(int a, int b) {
        if (b == 0) {
            return a;
        }
        return ggtRekuriv(b, a % b);
    }

    public int ggtIterativ(int a, int b) {
        while (b != 0) {
            int h = a % b;
            a = b;
            b = h;
        }
        return a;
    }
}
```

### ueb03(略)

### ueb04

Implementieren Sie JUnit-[[remote-notes/sem3/mikro/Tests/Tests|Tests]] für die Klasse `LinkedList`.

```JavaScript
package de.htwsaar.esch.Codeopolis.Util;

import java.util.NoSuchElementException;

/**
 * A generic class for a singly linked list.
 * This class provides basic methods for adding, removing, and accessing elements.
 *
 * @param <T> The type of elements in the list.
 */
public class LinkedList<T extends Comparable<T>> {
    /**
     * Internal node class to hold data and link to the next node.
     */
    private class Node {
        T data;
        Node next;

        /**
         * Node constructor.
         *
         * @param data The data item to be held by this node.
         */
        Node(T data) {
            this.data = data;
            this.next = null;
        }
    }

    private Node head;  // Head of the list
    private int size;   // Number of elements in the list

    /**
     * Constructor for MyLinkedList.
     * Initializes an empty list.
     */
    public LinkedList() {
        head = null;
        size = 0;
    }

    /**
     * Adds an element to the end of the list.
     *
     * @param item The element to be added.
     */
    public void addLast(T item) {
        Node newNode = new Node(item);
        if (head == null) {
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
        size++;
    }

    /**
     * Adds all elements from another LinkedList to this LinkedList.
     *
     * @param other The LinkedList containing elements to be added.
     */
    public void addAll(LinkedList<T> other) {
        if (other == null || other.isEmpty()) {
            return;
        }
        Iterator<T> iterator = other.iterator();
        while (iterator.hasNext()) {
            this.addLast(iterator.next());
        }
    }

    /**
     * Removes the first element of the list and returns it.
     * If the list is empty, returns null.
     *
     * @return The removed element or null if the list is empty.
     */
    public T removeFirst() {
        if (head == null) return null;
        T data = head.data;
        head = head.next;
        size--;
        return data;
    }

    /**
     * Checks if the list is empty.
     *
     * @return true if the list is empty, false otherwise.
     */
    public boolean isEmpty() {
        return head == null;
    }

    /**
     * Returns the size of the list.
     *
     * @return The number of elements in the list.
     */
    public int size() {
        return size;
    }

    /**
     * Retrieves the element at a specified index.
     *
     * @param index The index of the element to retrieve.
     * @return The element at the specified index.
     * @throws IndexOutOfBoundsException If the index is out of bounds (index < 0 || index >= size).
     */
    public T get(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index " + index + " out of bounds for length " + size);
        }
        Node current = head;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        return current.data;
    }

    /**
     * Replaces the element at a specified index with a new element.
     * Returns the element previously at the index.
     *
     * @param index The index of the element to replace.
     * @param element The new element to be set at the index.
     * @return The element previously at the index.
     * @throws IndexOutOfBoundsException If the index is out of bounds (index < 0 || index >= size).
     */
    public T set(int index, T element) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index " + index + " out of bounds for length " + size);
        }
        Node current = head;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        T oldData = current.data;
        current.data = element;
        return oldData;
    }

    /**
     * Clears all elements from the list.
     * After this method is called, the list will be empty.
     */
    public void clear() {
        head = null;  // Remove the reference to the head node, allowing garbage collection
        size = 0;     // Reset the size of the list
    }

    /**
     * Removes the element at the specified position in this list.
     * Shifts any subsequent elements to the left (subtracts one from their indices).
     *
     * @param index the index of the element to be removed
     * @return the element that was removed from the list
     * @throws IndexOutOfBoundsException if the index is out of range (index < 0 || index >= size())
     */
    public T remove(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index " + index + " out of bounds for length " + size);
        }
        Node prev = null;
        Node current = head;

        if (index == 0) {
            head = head.next; // Move head
        } else {
            // Traverse to the element before the one to be removed
            for (int i = 0; i < index; i++) {
                prev = current;
                current = current.next;
            }
            // Remove the element
            prev.next = current.next;
        }
        size--;
        return current.data;
    }

    /**
     * Returns an iterator that provides sequential access to the elements in this list.
     *
     * @return an Iterator instance capable of iterating over the elements of the list in sequence.
     */
    public Iterator<T> iterator() {
        return new LinkedListIterator();
    }

    private class LinkedListIterator implements Iterator<T> {
        private Node current = head;

        @Override
        public boolean hasNext() {
            return current != null;
        }

        @Override
        public T next() {
            if (current == null) {
                throw new NoSuchElementException("No more elements in the list");
            }
            T data = current.data;
            current = current.next;
            return data;
        }
    }

    /**
     * Sorts the elements of the list using the Bubble Sort algorithm.
     */
    public void sort() {
        if (size <= 1) {
            return;
        }

        for (int n = size; n > 1; n--) {
            Node current = head;
            for (int i = 0; i < n - 1; i++) {
                Node next = current.next;
                if (current.data.compareTo(next.data) > 0) {
                    // Swap current and next data
                    T temp = current.data;
                    current.data = next.data;
                    next.data = temp;
                }
                current = current.next;
            }
        }
    }


}
```

==From ChatGPT==

```JavaScript
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import java.util.Iterator;
import java.util.NoSuchElementException;

import static org.junit.jupiter.api.Assertions.*;

public class LinkedListTest {

    private LinkedList<Integer> list;

    @BeforeEach
    public void setUp() {
        list = new LinkedList<>();
    }

    @Test
    public void testAddLastAndSize() {
        assertTrue(list.isEmpty(), "Liste sollte anfangs leer sein");

        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        assertEquals(3, list.size(), "Die Größe der Liste sollte 3 sein");
        assertFalse(list.isEmpty(), "Liste sollte nach dem Hinzufügen von Elementen nicht leer sein");
    }

    @Test
    public void testRemoveFirst() {
        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        assertEquals(10, list.removeFirst(), "Das erste Element sollte entfernt werden");
        assertEquals(2, list.size(), "Die Größe der Liste sollte nach dem Entfernen 2 sein");
        assertEquals(20, list.removeFirst(), "Das neue erste Element sollte entfernt werden");
        assertEquals(1, list.size(), "Die Größe der Liste sollte nach dem Entfernen 1 sein");
        assertEquals(30, list.removeFirst(), "Das letzte Element sollte entfernt werden");
        assertTrue(list.isEmpty(), "Liste sollte nach dem Entfernen aller Elemente leer sein");
    }

    @Test
    public void testRemoveByIndex() {
        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        assertEquals(20, list.remove(1), "Das Element an Index 1 sollte entfernt werden");
        assertEquals(2, list.size(), "Die Größe der Liste sollte nach dem Entfernen 2 sein");

        assertEquals(30, list.remove(1), "Das letzte Element sollte entfernt werden");
        assertEquals(1, list.size(), "Die Größe der Liste sollte nach dem Entfernen 1 sein");

        assertEquals(10, list.remove(0), "Das erste Element sollte entfernt werden");
        assertTrue(list.isEmpty(), "Liste sollte nach dem Entfernen aller Elemente leer sein");
    }

    @Test
    public void testGet() {
        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        assertEquals(10, list.get(0), "Das erste Element sollte 10 sein");
        assertEquals(20, list.get(1), "Das zweite Element sollte 20 sein");
        assertEquals(30, list.get(2), "Das dritte Element sollte 30 sein");
    }

    @Test
    public void testSet() {
        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        assertEquals(20, list.set(1, 25), "Das Element 20 sollte durch 25 ersetzt werden");
        assertEquals(25, list.get(1), "Das zweite Element sollte nun 25 sein");
    }

    @Test
    public void testGetWithInvalidIndex() {
        list.addLast(10);
        list.addLast(20);

        assertThrows(IndexOutOfBoundsException.class, () -> list.get(-1), "IndexOutOfBoundsException sollte bei negativem Index geworfen werden");
        assertThrows(IndexOutOfBoundsException.class, () -> list.get(2), "IndexOutOfBoundsException sollte bei einem zu großen Index geworfen werden");
    }

    @Test
    public void testClear() {
        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        assertEquals(3, list.size(), "Die Größe der Liste sollte 3 sein");
        list.clear();
        assertEquals(0, list.size(), "Nach dem Leeren sollte die Größe der Liste 0 sein");
        assertTrue(list.isEmpty(), "Nach dem Leeren sollte die Liste leer sein");
    }

    @Test
    public void testIterator() {
        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        Iterator<Integer> iterator = list.iterator();
        assertTrue(iterator.hasNext(), "Der Iterator sollte ein Element haben");
        assertEquals(10, iterator.next(), "Das erste Element sollte 10 sein");
        assertTrue(iterator.hasNext(), "Der Iterator sollte ein weiteres Element haben");
        assertEquals(20, iterator.next(), "Das zweite Element sollte 20 sein");
        assertTrue(iterator.hasNext(), "Der Iterator sollte ein weiteres Element haben");
        assertEquals(30, iterator.next(), "Das dritte Element sollte 30 sein");
        assertFalse(iterator.hasNext(), "Der Iterator sollte keine weiteren Elemente haben");

        assertThrows(NoSuchElementException.class, iterator::next, "Eine NoSuchElementException sollte geworfen werden, wenn keine Elemente mehr vorhanden sind");
    }

    @Test
    public void testSort() {
        list.addLast(30);
        list.addLast(10);
        list.addLast(20);

        list.sort();

        assertEquals(10, list.get(0), "Das erste Element sollte nach dem Sortieren 10 sein");
        assertEquals(20, list.get(1), "Das zweite Element sollte nach dem Sortieren 20 sein");
        assertEquals(30, list.get(2), "Das dritte Element sollte nach dem Sortieren 30 sein");
    }

    @Test
    public void testAddAll() {
        LinkedList<Integer> other = new LinkedList<>();
        other.addLast(40);
        other.addLast(50);

        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        list.addAll(other);

        assertEquals(5, list.size(), "Die Größe der Liste sollte nach dem Hinzufügen aller Elemente 5 sein");
        assertEquals(40, list.get(3), "Das vierte Element sollte 40 sein");
        assertEquals(50, list.get(4), "Das fünfte Element sollte 50 sein");
    }
}
```

  

### ueb05

![[/image 1 10.png|image 1 10.png]]

```JavaScript
import java.util.function.Function;

public class Iterate {

     // x0 Startwert
     // Anzahl der Iterationen
     // Funktion f: R → R
    public static double iterate(double x0, int n, Function<Double, Double> f) {
        double result = x0;
        for (int i = 0; i < n; i++) {
            result = f.apply(result);
        }
        return result;
    }

    public static void main(String[] args) {
        // Teilaufgabe (b)

        // f(x) = 2x
        Function<Double, Double> f1 = x -> 2 * x;
        double result1 = iterate(1.0, 5, f1);  // Startwert 1.0, 5 Iterationen
        System.out.println("Ergebnis1: " + result1);

        // f(x) = 0.5x
        Function<Double, Double> f2 = x -> 0.5 * x;
        double result2 = iterate(1.0, 5, f2);  
        System.out.println("Ergebnis2: " + result2);

        // f(x) = ax(x-1), für a ∈ (0,1)
        double a = 0.9;  // Beispielwert für a
        Function<Double, Double> f3 = x -> a * x * (x - 1);
        double result3 = iterate(1.0, 5, f3);  
        System.out.println("Ergebnis3: " + result3);
    }
}
```

(function 2 and 3 as example) same as

```JavaScript
 // ...in class... 
 public static Double function2(Double x) {
        return 0.5 * x;
    }
    
 public static Double function3(Double x, Double a) {
        return a * x * (x - 1);
    }
    
   //...in main...
    Function<Double, Double> f1 = IterateExample::function1;
    double result1 = iterate(1.0, 5, f1);
    
    double a = 0.9;
    Function<Double, Double> f3 = x -> function3(x, a);
    double result3 = iterate(1.0, 5, f3); 
```

### ueb06(略) ähnlich wie 5, lambda Übung

### ueb07