  

## Aufgabe 2

### Welche Höhe besitzt ein binärer Baum mit 2000 Knoten höchstens, welche mindestens ?

  

- im Best-Case ist der Binäre Baum vollständig und jede seiner Ebenene ist vollständig gefüllt.
    
    - Dies verläuft logarithmisch, daher mindestens die höhe $log_2(n)$
    
    - Somit wäre das best case $log_2(2000)$
    

- Worst case wäre ein _==single-linked list==_ ähnender Baum, der somit die höhe n-1 hätte.

  

> [!important] Wenn die höhe
> 
> $n$ ist, dann ist maximale Anzhal von nodes ( vollständiger Baum) = $= (2^n)-1$