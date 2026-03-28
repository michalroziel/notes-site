[[Programming 3]]
![[PIB-PR3 - 06 [[Technische Schulden und Clean Code]] - v2024-10-29.pdf]]
# 1.1 Ausgangssituation 
```
calc() -> calculateTotal()

x -> total_value 

null :

Optional<Item> itemOp = Optional.of(Item)




y -> tempPrice()

//Wir können ebenfalls switch Cases verwenden um if-checks zu vermeiden



"var" anstatt von Item 
```

# 1.2 Refactoring 
Um in dem Code unnötige Verschachtelungen zu vermeiden, können wir eigene Methoden verwenden
```
calculateItemCost() methode 
```

# 1.3 Reflexion 

Wir haben variablen namen geändert, Optionals, var benutzt
einzelne Berechnungen wurden in einzelne Methoden ausgelagert

# 2. DRY - Don't repeat yourself

## 2.1 Ausgangssituation
```
public enum membership = "REGULAR", "VIP", "PREMIUM"

Dieses enum ermöglicht uns customerType.equals("VIP"); zu vermeiden
```
![[Screenshot 2024-10-29 at 17.00.00.png]]


# 3. Single Responisbility Principle (SRP)
*Das Single Responsibility Principle (SRP)* besagt, dass eine Klasse oder Methode nur eine einzige Verantwortung haben sollte, um die Verständlichkeit und Wartbarkeit zu erhöhen. In dieser Aufgabe werden wir den bestehenden Code so refaktorisieren, dass jede Klasse oder Methode nur eine spezifische Aufgabe erfüllt.

# 3.1 Ausgangssituation 

# 4. Modernes Java 

