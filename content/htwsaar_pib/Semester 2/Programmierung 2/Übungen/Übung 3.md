  

## Aufgabe 1 - Codeopolis.

> [!important] Die Klasse DomainModel.Plants.Conditions ist inhaltlich sehr eng mit der Klasse Grain ver- wandt. Es gibt daher Argumente, sie als innere Klasse zu implementieren. Refactorieren Sie daher die Implementierung so, dass Conditions eine statische innere Klasse von Grain ist. Überlegen Sie, welche Vor- und Nachteile dies hat und diskutieren Sie dies im Review.

  

Wir definieren die [[Static]] nested [[class]] in der Grain [[class]] wie folgt :

```Java
/* Grain Class Code */

public static class Conditions{

/*  Conditions Code */

public static de.htwsaar.esch.Codeopolis.DomainModel.Plants.Grain.Conditions generateRandomConditions() {

/* random conditions code */

return new de.htwsaar.esch.Codeopolis.DomainModel.Plants.Grain.Conditions(soilConditions, averageTemperatureSummer, averageTemperatureWinter, drought, fusarium, leafDrought, powderyMildew, barleyGoutFly, deliaFly, fritFly);



}
```

- Da nun Conditions eine statische Klasse ist kann sie nicht auf nicht stastische Member der umgegeben Klasse Grain zugreifen.

- Man muss immer Grain.Conditions angeben

- Man erstellt keine Codnditions Objekt mehr sondern Grain.Coditions Objekte

  

### ==Vor und Nachteile ;==

- Kapselung : Der Code ist organisierter da Conditions nur im Kontext von grain verwendet wird

- Kann private Memeber accessen : Auch wenn die Instanzvariablen von Grain _==private==_ sind, kann die Klasse Conditions sie accessen

- höhere Kohäsion

- Einfacher zu lesen : Der Code-Aufbau ist so einfacher zu lesen, da weniger Top-Level Klassen existieren

  

- ZU viele innere Klassen : Wenn man viele innere Klassen einbaut steigt die Komplexität des Codes

- Hohe Kopplung : Wenn wir Conditions im anderen Kontext verwenden würden ist es schwerer damit zu Arbeiten : ==Äußere Klasse kann innere nicht extenden==

  

  

## Aufgabe 2 - Codeopolis.

> [!important] Die Klasse Depot verwaltet Silos mit verschiedenen Getreidesorten. Um es zu ermöglichen, nur über die Silos des Depots zu iterieren, die eine bestimmte Getreidesorte enthalten, soll ein entsprechender Iterator hinzugefügt werden. Da der Iterator nur im Kontext der Klasse Depot sinnvoll ist, soll er als Inner [[class]] implementiert werden. Gehen Sie bei der Implementierung wie folgt vor:

  

- Code für den Iterator :

```Java
public interface Iterator {
        /**
        * Checks if there are further objects available for iteration.
        *
        * @return {@code true} if more objects are available; {@code false} otherwise.
        */
        boolean hasNext();
        /**
        * Returns the next {@link Silo.Status} object in the iteration.
        * This method should only be called if {@code hasNext()} returns {@code true}.
        *
        * @return The next {@link Silo.Status} object.
        * @throws NoSuchElementException if no more elements are available.
        */
        Silo.Status next();
}
```

- Diesen Code implementieren wir als Inneres Interace innerhalb der Depot Klasse.

- Anschließend implemenetieren wir eine Klasse DepotIterator

  

  

  

### b)

> [!important] Implementieren Sie die Klasse DepotIterator als private innere Klasse, die das Interface Iterator implementiert. Über den Konstruktor des Iterators wird die Getreidesorte gesetzt. Der Iterator iteriert dann nur über die Silos dieses Typs.

  

### c)

> [!important] Der Iterator gibt ein Objekt vom Typ Silo.Status zurück. Implementieren Sie diesen Typ als innere Klasse. Die Klasse Silo.Status soll public sein, aber nur
> 
> ==private Konstruktoren== besitzen, so dass sie nur innerhalb der Klasse Silo instanziiert werden kann. Silo.Status speichert die Kapazität und den aktuellen Füllstand des Silos. Stellen Sie sicher, dass Objekte der Klasse Silo.Status immutable1 sind.  
> Um ein Silo.Status-Objekt erzeugen zu können, fügen Sie der Silo-Klasse eine getStatus- Methode hinzu.

- Frage : Welche Konstruktoren zusätzlich ? Factory Methode die aus einem Parameter Objekt ein neues Objekt macht?

  

### d)

> [!important] ImplementierenSieeinepublic-Methode, die ein Iterator-Objekt zurück gibt,damit ein Iterator-Objekt auch außerhalb der Depot-Klasse instanziiert werden kann.

  

> [!important] Schreiben Siedie Methoden
> 
> ==_public int getCapacity_==(Game.GrainType grainType) und ==_public int getFillLevel_==(Game.GrainType grainType) so um, dass der Iterator verwendet wird.  
> Überlegen Sie, wie Sie diese Funktionalität ohne innere Klassen implementieren können und disku- tieren Sie im Review die Vor- und Nachteile der Implementierungsvarianten.

  

  

> [!important] ==**Wie könnten wir die Funktionalität ohne innere Klassen schaffen ?**==

- DepotIterator als TopLevel Klasse erstellen welche ein Graintype und ein silo Array hat. Der DepotIterator implementiert das Iterator Interface

- Könnte dann keinen privaten Konstruktor haben

  

- Iterator : Top Level Interface

  

- Status als TopLevel Klasse welche ein Silo Objekt besitzt
    
    - daraus die Capacity und FillLevel rausliest.
    
    - return Status Objekt
    

  

- getFillLevel und getCapacity müssten einen Iterator außerhalb der eigenen Klasser erstellen

  

  

## Aufgabe 3 - Codeopolis

> [!important] Schreiben Sie die Methode
> 
> _==Depot.toString()==_ so um, dass eine lokale Klasse DepotVisualizer verwendet wird, um die String-Repräsentation eines Silos zu erzeugen. Die eigentliche toString- Methode sieht dann wie folgt aus:
> 
>   
> 
> ```[[Java]]
> DepotVisualizer result = new DepotVisualizer();
> for (Silo silo : silos) {
> result.appendSiloInfo(silo);
> }
> return result.visualize();
> ```
> 
>   
> Überlegen Sie welche Vor- und Nachteile die Implementierung mittels einer lokalen Klasse hat und diskutieren Sie diese im Review.  
> 4. Aufgabe (Codeopolis)

  

  

## Aufgabe 4 - Codeopolis

> [!important] Passen Sie die Methode
> 
> ==_City.plant_== so an, dass beim Pflanzen von Weizen mit einer Wahrschein- lichkeit von 0.1 eine spezielle Weizensorte gepflanzt wird, die den doppelten Grundertrag hat. Im- plementieren Sie diese spezielle Sorte als annonyme Klasse.  
> Überlegen Sie, warum es sinnvoll ist, dies als anonyme Klasse zu implementieren und diskutieren Sie dies im Review.