  

## 1. Weiß, wie ich bei einer Redhat-VM gezielt eine der vier verfügbarenden Desktop-Oberflächen auswählen kann

  

- sehen wir im Login - Screen von der VM

  

  

## 2. Stamdard vs Classic RedHat VM

  

## 3. effizient die PId meines systemd bekomme

```Shell
pgrep systemd
```

  

  

## 4. Weiß, wie ich effizient nach dem Login in einer Shell die Baumstruktur meiner Prozesse zeigen kann

  

- utree command

  

  

## 5. Weiß, wozu PATH dient

- dient dazu herauszufinden, wo die Binaries sind ( ausführbare Dateien )

  

  

## 6. weiß, was der Bestandteil “ : . : “ in der Systemvariable PATH bewirkt

- die Shell schaut nach und checkt ob die Binary / executable Datei im aktuellen Verzeichnis ist

  

## 7. weiß, wie ich mir alle aktuell vorhandenen Shell-Variablen mit Namen und Inhalt ansehen kann

```Shell
printenv
```

  

  

## 8. Weiß, wie die Zeichen * und ? bei der Suche nach Filenamen  
verwendet werden können

- * → alles anzeigen

- ? → je nach dem wie viele ? man angibt werden Dateinamen und Dateien mit der gleichen anzahl von ? ausgegeben

  

  

## 9. Weiß, wie ich mir nur die Namen aller Einträge in meinem  
HOME-Directory anzeigen lassen kann, die mit einem Punkt  
beginnen und an dritter Stelle ein "n " haben

  

```Shell
ls ~ .??n*
```

  

## 10. Weiß, wie ich mir die Namen aller Java-Quelldateien in den  
Ordnern anzeigen lassen kann, deren Name mit "pe " bzw.  
"p i " beginnt und mit "e " endet. Dabei stehe ich in meinem  
HOME-Directory und die fraglichen Ordner liegen im Teilbaum  
Beispiele /java /fuer_anfaenger-BlueJ .

  

```Shell
ls ./Beispiele/java/fuer_anfaenger-BlueJ/[pe][pi]*e.java
```

  

  

## 11. weiß, warum für eine Datei namens "mit Leerzeichen " mit  
folgendem Kommando keine Eigenschaften anzeigt:  
ls -l mit Leerzeichen

  

```Shell
╭─    ~ ────────────────────────────────────────── ✔  17:13:52  ─╮
╰─ ls -l mit leerzeichen                                               ─╯
ls: leerzeichen: No such file or directory
ls: mit: No such file or directory

╭─    ~ ──────────────────────────────────────── 1 ✘  17:14:13  ─╮
╰─ ls -l " mit leerzeichen"                                            ─╯
ls:  mit leerzeichen: No such file or directory
```

  

## 12. Weiß, welche Dateinamen zu folgenden Mustern passen  
[!-0] [!!-1] [!--1] [\!--1]

1. Alle vorherige Kommands außer der letzte.

1. Nur der letzte Kommand

1. Nicht valid

1. überprüft, ob die Dateiname ein “!” oder “-” hat