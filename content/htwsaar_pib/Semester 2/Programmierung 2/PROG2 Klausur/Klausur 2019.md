**Aufgabe** 2

Implementieren Sie die beiden [[Funktionen]] `findRecursive` und `findIterative` der Klasse  
`SubstringFinder`. Beide [[Funktionen]] sollen prüfen, ob ein gegebener Teilstring `needle`  
in dem String `haystack` enthalten ist. Ist dies der Fall soll `true` zurück gegeben werden,  
andererseits false. Sie dürfen keine Methoden der String-Klasse verwenden mit  
Ausnahme von `length`, `equals`, `substring` und `charAt`.

```JavaScript
public class SubstringFinder {
    public boolean findRecursive(String s, String t) {
        if (t.length() == 0) {
            return false;
        }
        if (t.length() > s.length()) {
            return false;
        }
        if (s.substring(0, t.length()).equals(t)) {
            return true;

        }
        return findRecursive(s.substring(1), t);
    }

    public boolean findIterative(String s, String t) {
        if (t.length() == 0) {
            return false;
        }
        if (t.length() > s.length()) {
            return false;
        }
        for (int i = 0; i < s.length() - t.length() + 1; i++) {
            if (s.substring(i, i + t.length()).equals(t)) {
                return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        SubstringFinder sf = new SubstringFinder();
        System.out.println(sf.findRecursive("hello", "lo"));
    }
}
```

  

**Aufgabe 3**

```Java
package Aufgabe_3;

import java.util.*;
import java.util.function.*;
import java.util.stream.*;

public class CarPortal {
    private Map<Integer, Car> cars;

    // (a)Konstruktor: Initialisiert die Datenstruktur cars. Diese speichert
    // Car-Objekte unter einer ID. Wählen Sie die Datenstruktur so, dass die
    // Car-Onjekte in der Reihenfolge, in der Sie hinzugefügt wurden, abgerufen
    // werden können.
    public CarPortal() {
        this.cars = new LinkedHashMap<>();
    }

    // (b) public void add(Integer id, Car car): Fügt cars unter der gegebenen ID
    // einen neuen Wagen hinzu.
    public void add(Integer id, Car car) {
        cars.put(id, car);
    }

    // (c) public void remove(Integer id): Entfernt den Wagen mit der gegebenen ID
    // aus cars.
    public void remove(Integer id) {
        cars.remove(id);
    }

    // (d) bubbleSort()
    public List<Car> getCarsSorted(Comparator<Car> c) {
        List<Car> carsList = new ArrayList<>(cars.values());
        int n = carsList.size();
        for (int i = 0; i < n - 1; i++) {
            for (int j = n - 1; j > 1; j++) {
                if (c.compare(carsList.get(j - 1), carsList.get(j)) > 0) {
                    Car temp = carsList.get(j - 1);
                    carsList.set(j - 1, carsList.get(j));
                    carsList.set(j, temp);
                }
            }
        }
        return carsList;

    }

    // e) public List<Car> getCarsFilteredAndSorted(Comparator<Car> c,
    // Predicate<Car> p): Gibt eine durch das Prädikat p gefilterte und durch den
    // Comparator c sortierte Liste der Wagen zurück. Implementieren Sie diese
    // Methode mit Hilfe eines *parallelen Streams*.
    public List<Car> getCarsFilteredAndSorted(Comparator<Car> c, Predicate<Car> p) {
        return cars.values().parallelStream().filter(p).sorted(c).collect(Collectors.toList());
    }

    // f) public Map<String, List<Car>> getCarsFilteredAndGrouped (Predicate<Car>
    // p): Filtert die Bestandsliste mit Hilfe des Prädikats p und
    // gibt eine nach Markennamen gruppierte Map der gefilterten Bestandsliste
    // zurück. Im- plementieren Sie diese Methode mit Hilfe eines parallelen
    // Streams.
    public Map<String, List<Car>> getCarsFilteredAndGrouped(Predicate<Car> p) {
        return cars.values().parallelStream().filter(p).collect(Collectors.groupingBy(Car::getBrand));
    }

    // g) public long countCars(Predicate<Car> p): Gibt die Anzahl der Wagen die das
    // gegebene Predicate erfüllen zurück. Implementieren Sie diese Methode mit
    // Hilfe eines parallelen Streams.
    public long countCars(Predicate<Car> p) {
        return cars.values().parallelStream().filter(p).count();
    }

    // Implementieren Sie in der unten aufgeführten Klasse CarPortalTest folgendes
    // und nutzen Sie dabei Lambda Ausdrücke:
    public class CarPortalTest {
        public static void main(String[] args) {
            CarPortal carPortal = new CarPortal();
            String[] colors = { "black", "red", "green", "blue", "yellow" };
            String[] brands = { "Lamborghini", "Ferrari", "Bugatti", "maserati", "Pagani" };
            java.util.Random r = new java.util.Random();
            for (int i = 0; i < 100; i++) {
                carPortal.add(i, new Car(colors[r.nextInt(5)], brands[r.nextInt(5)], 100 * r.nextInt(300)));
            }

            // (h) Zählen Sie alle gelben Lamborghinis.
            Predicate<Car> yellowLamborghini = c -> c.getColor().equals("yellow") && c.getBrand().equals("Lamborghini");

            // (i) Fragen Sie eine nach horsePower sortierte Liste aller Ferraris ab.
            List<Car> sortedFerraris = carPortal.getCarsFilteredAndSorted(Comparator.comparing(Car::getHorsePower),
                    c -> c.getBrand().equals("Ferrari"));

        }

    }
}
```

Aufgabe 4

```Java
package Aufgabe_4;

import java.util.*;
import java.util.function.Predicate;

public class Dictionary<K, V> {
    private TreeMap<K, V> dict;

    /* a */
    public Dictionary() {
        this.dict = new TreeMap<>();
    }

    /* b */
    public void insert(K key, V value) {
        dict.put(key, value);
    }

    /* c */
    public boolean insertAll(List<? extends K> keys, List<? extends V> values) {
        if (keys.size() != values.size()) {
            return false;
        }
        for (int i = 0; i < keys.size(); i++) {
            dict.put(keys.get(i), values.get(i));
        }
        return true;
    }

    /* d */
    public V getTranslation(K key) {
        return dict.get(key);
    }

    /* e */
    public void printAll() {
        Iterator<Map.Entry<K, V>> it = dict.entrySet().iterator();
        while (it.hasNext()) {
            Map.Entry<K, V> entry = it.next();
            System.out.println(entry.getKey() + " -> " + entry.getValue());
        }
    }

    /* f */
    public void removeIf(Predicate<K> p) {
        dict.keySet().removeIf(p);
    }

    public static class Translation implements Comparable<Translation> {
        private String language;
        private String translation;

        public Translation(String language, String translation) {
            this.language = language;
            this.translation = translation;
        }

        public String getLanguage() {
            return this.language;
        }

        public String getTranslation() {
            return this.translation;
        }

        /* g */
        @Override
        public int compareTo(Translation other) {
            return this.language.compareTo(other.language);
        }

        @Override
        public String toString() {
            return this.language + ": " + this.translation;
        }

    }

    public class DictionaryTest {
        public static void main(String[] args) {
            /* h */
            Dictionary<String, TreeSet<Translation>> dict = new Dictionary<>();
            /* i */
            TreeSet<Translation> translations = new TreeSet<>();
            translations.add(new Translation("French", "Salut"));
            translations.add(new Translation("English", "Hello"));
            dict.insert("Hallo", translations);

            /* j */
            TreeSet<Translation> helloTranslations = dict.getTranslation("Hallo");
            helloTranslations.stream().filter(p -> p.getLanguage().equals("French"))
                    .map(p -> p.getTranslation().toLowerCase()).forEach(System.out::println);

            /* k */
            dict.removeIf(p -> p.startsWith("H"));
        }

    }
}
```

Aufgabe 5

```Java
\#include <stdio.h>

void findMax(int *arr, int size, int *max)
{
    if (size <= 0)
    {
        *max = -1;
        return;
    }

    *max = arr[0];

    for (int i = 1; i < size; i++)
    {
        if (arr[i] > *max)
        {
            *max = arr[i];
        }
    }
}

int main()
{
    int arr[] = {3, 7, 2, 5, 8, 4};
    int size = sizeof(arr) / sizeof(arr[0]);
    int *max;

    findMax(arr, size, &max);

    printf("Das Maximum im Array ist: %d\n", *max);

    return 0;
}
```

  

```Java
\#include <stdio.h>

typedef struct {
    int i;
} someStruct;

void dosomething(int i, int arr[], int k, int *p, someStruct s) {
    i++;          // i wird lokal um 1 erhöht, aber nicht außerhalb der Funktion sichtbar
    arr[0]++;     // arr[0] wird erhöht, diese Änderung ist im Aufrufer sichtbar
    k++;          // k wird lokal erhöht, aber nicht außerhalb der Funktion sichtbar
    (*p)++;       // arr[2] wird erhöht, da p auf arr[2] zeigt
    s.i++;        // s.i wird lokal erhöht, aber die Änderung ist außerhalb nicht sichtbar
}

int main() {
    int i = 0;
    int arr[3] = {0, 0, 0};
    someStruct s = {0};
    
    dosomething(i, arr, arr[1], &arr[2], s);
    
    // Erwartete Ausgabe: i = 0, arr[0] = 1, arr[1] = 0, arr[2] = 1, s.i = 0
    printf("%d, %d, %d, %d, %d\n", i, arr[0], arr[1], arr[2], s.i);
    
    return 0;
}
```