
Für jede Matrix sollst du:

1. das **charakteristische Polynom** berechnen
2. daraus die **Eigenwerte** bestimmen
3. zu jedem Eigenwert einen **Eigenvektor** finden

Die allgemeine Idee ist immer:
# Aufgabe 3 
`cot_x = 1 ./ tan_x`
Hier ist ./ das punktweise anwenden des Operators 

```MATLAB
SOLUTION = [x.' sin_x.' cos_x.' tan_x.' cot_x.']
```
Hier ist `.'` das Transponieren von Zeilen into Spalten Vektoren


# Aufgabe  4 

`[eigenVektoren_A, eigenWerte_diagonal_A] = eig(A)`

`eig(A)` gibt uns die  Matrix der Eigenvektoren 
und 
Diagonal Matrix der Eigenwerte 

#### Mathematisch
Ein Eigenvektor `v` und ein Eigenwert `lambda` erfüllen : 

```matlab
A * v = lambda * v 
```
> Wenn man A auf den Vektor anwendet ändert sich nur die Länge, aber bleibt auf derselben Geraden 

