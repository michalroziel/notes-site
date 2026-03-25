
```matlab
lineare_reg_start
```

**1. Punktweise Eingabe**
- Hauptmenü: A
- Anzahl: `4`

- dann: 
	- `x=1, y=2 x=2, y=4 x=3, y=5 x=4, y=8`


**2. Regressionsmenü**
- Hauptmenü: `C`

Dann:
- `A` und Grad `1`
- prüfen:
    - Koeffizienten
    - Formel im Command Window
    - Plot mit Regression und Interpolation
    - zweites Subplot mit Abständen

Dann nochmal:
- `A `und Grad `2
	
Dann:
- `C` im Regressionsmenü
- prüfen:
    - Vergleichsplot mit `mehreren` Regressionen
    - Datenpunkte nur einmal

**3. Automatische Gradwahl**

- im Regressionsmenü: `B`
- prüfen:
    - ein Grad wird ausgegeben
    - Plot erscheint
    - Regression wird gespeichert


**4. Fehlerfälle**

bei manueller Gradwahl: `-1` oder `2.5`

- prüfen:
    - Fehlermeldung
    - Menü bleibt offen

**5. Doppelte x-Werte**

- Hauptmenü: `A`
- Anzahl: `4`

- dann: x=1 x=2 x=2 x=4`

- prüfen:
    - check_Data schlägt an


**6. Laden aus vorhandenen Vektoren**  
Vorher im Command Window:

`xTest = [1 2 3 4]; 
`yTest = [2 4 5 8];`

Dann im Main Menu : `B`
- xTest
- yTest

