  

### Man kann Kommandos in Listen zusammenfassen

  

```Java
pwd ; { cd /bin ; pwd; }; pwd
```

```Java
╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:06:51  ─╮
╰─ pwd ; { cd /bin ; pwd; }; pwd                                                                                      ─╯
/Users/michalroziel
/bin
/bin

╭─    /bin ────────────────────────────────────────────────────────────────────────────────────── ✔  12:07:27  ─╮
╰─
```

  

```Java
╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:07:59  ─╮
╰─ pwd ; ( cd /bin ; pwd; ); pwd                                                                                      ─╯
/Users/michalroziel
/bin
/Users/michalroziel

 pwd                  pwd
---------->          --------->
						cd ; pwd
           --------->

```

  

```Java
╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:10:22  ─╮
╰─ pwd ; { cd /bin ; pwd; } > xxx ; pwd                                                                               ─╯
/Users/michalroziel
/bin

╭─    /bin ────────────────────────────────────────────────────────────────────────────────────── ✔  12:11:06  ─╮
╰─ ls xxx                                                                                                             ─╯
ls: xxx: No such file or directory

```

  

```Java
╭─    /bin ──────────────────────────────────────────────────────────────────────────────────── 1 ✘  12:11:14  ─╮
╰─ pwd ; { cd /bin ; pwd; } > $HOME/xxx ; pwd                                                                         ─╯
/bin
/bin

╭─    /bin ────────────────────────────────────────────────────────────────────────────────────── ✔  12:12:00  ─╮
╰─



pwd   { cd /Bin ; pwd } > ..... ; pwd
-----> ------------------> ----> ----->
													xxx
												> $HOME/xxx

Aufgrunf von Zugriffsrechten -> kein Zugriff
```

  

### Unix/Linux Kommandos Extended Teil 2

- ==javac TestMyMath …. ausprobieren==

  

  

## Prioritäten von Kommando - Separatoren

- Priorität Hoch : |

- Priorität Mittel : && ||

- Priorität Niedrig : ; &

  

```Java
kill -9 [ Prozess iD ]
```

  

  

## Kommandos zum Knobeln

```Java
( sleep 5: date )& ls


╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:25:07  ─╮
╰─ ( sleep 5; date; )& ls                                                                                             ─╯

[1] 38968
Applications         Downloads            Music                fgrep                xxx
Creative Cloud Files IdeaProjects         Pictures             node_modules         yarn.lock
Desktop              Library              Public               package-lock.json
Documents            Movies               VirtualBox VMs       package.json

╭─    ~ ───────────────────────────────────────────────────────────────────────────────────── ✔    12:25:23  ─╮
╰─ Fri Jan 19 12:25:28 CET 2024                                                                                       ─╯

[1]  + 38968 done       ( sleep 5; date; )
╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:25:23  ─╮
╰─
```

  

```Java
		                      ls	 	
------>                    ---------------->
				( sleep 5; date; )&
				------------------>

Ohne den Hintergrundprozess : 



╰─ ( sleep 5; date; ); ls                                                                                             ─╯

Fri Jan 19 12:28:23 CET 2024
Applications         Downloads            Music                fgrep                xxx
Creative Cloud Files IdeaProjects         Pictures             node_modules         yarn.lock
Desktop              Library              Public               package-lock.json
Documents            Movies               VirtualBox VMs       package.json

╭─    ~ ────────────────────────────────────────────────────────────────────────────────── ✔  5s   12:28:23  ─╮
╰─
```

  

  

![[/[[Untitled]] 4.png|[[Untitled]] 4.png]]

  

## Shell Variablen

  

### LINENO - wie viele Kommandos habe ich in diesem Fenster eingegeben

  

```Java
echo $PATH

echo PATH

╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:41:16  ─╮
╰─ echo $LINENO                                                                                                       ─╯
52

╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:41:24  ─╮
╰─
```

  

### SECONDS - seit wie vielen Sekunden läuft die Shell

  

```Java
╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:41:24  ─╮
╰─ echo $SECONDS                                                                                                      ─╯
134179
```

  

### IFS → Internal File Separator

  

  

### printenv → print environment - Umgebungsvariablen Zeilenweise ausgeben

  

### random → zufallszahlen generieren

```Java
echo $RANDOM
```

  

```Java
╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:47:38  ─╮
╰─ MyVar=hello                                                                                                        ─╯

╭─    ~ ───────────────────────────────────────────────────────────────────────────────────────── ✔  12:48:23  ─╮
╰─ echo $MyVar                                                                                                        ─╯
hello
```

  

- der variablenname muss mit einem Buchstaben beginnen

- → sind nur in der aktuellen Shell vorhanden
    
    - → damit in der Subshell zugägnglich → variable exportieren
    

  

### export und import Kommandos

- mit export Variablen in die Subshell runter geben

- mit import Variablen von Subshell nach Shell Hoch geben
    
    - aber : danach existiert die Subshell nicht mehr
    

  

### Aufgaben mit lokalen, globalen, und sublokalen variablen

  

```Java
./sk1

. ./sk2 ---> nicht dasselbe !!!!
```

  

> [!important] in Unix/Linux ist alles eine Datei