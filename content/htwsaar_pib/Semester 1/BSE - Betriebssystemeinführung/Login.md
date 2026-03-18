- Es gibt verscheiedene Login Optionen

  

- Eingabe von Benutzername + Kennwort , eventuell auswahl der Oberfläche

- Eingaben werden geprüft - Ist der Benutzername in der Benutzer Datei ?

  

> [!important] Es starten viele Prozesse und Skripte

- damit das System vom Benutzer bedienbar ist

  

> [!important] /sbin /init → Initialprozess der alles weitere startet

  

```Shell
[ kthreadd ] -> ist ein Kernel Thread, der mit weiteren Threads 

							die HW verwaltet 
```

- ==Was ist HW ?==

  

  

### Was ist ein Thread ?

- früher gab es Prozedurale Programmierung → wir sagen dem Programm genau was es tun soll

  

- Programm wird in Hauptspeicher geladen → wenn zu groß dann nach und nach in den Hauptspeicher geladen, nach und nach werde Anweisungen abgearbeitet

  

- Hauptspeicher beschränkt die Ausführung des Programms

  

- Cache → RAM → Festplatte ( Schnelligkeit des Speichers auf dem Computer )

  

> [!important] Ein Thread ist ein Pfaden durch ein Programm

- Die Anweisungen die wir Ausführen laufen für alle Threads gleichzeitig

  

### Was passiert mit einem Programm auf der Festplatte ?

- Es Wird in RAM und danach in den Cache nach und nach geladen

  

> [!important] . profile → win Benutzerdefiniertes SKript im H.D, das beim Start der Login-Shell abläuft

  

  

## Commands :

- ```Shell
    /etc /profile  -> und weitere Skripts, die für den benutzer spezfisch ablaufen 
    
    									und unter anderem diverse Sytemvariablen setzen. 
    ```
    
      
    
    ```Shell
    michalroziel@MBP-michal-5 ~ % ps -ef | wc -l 
         735
    									-> liefert anzahl von den Laufenden Prozessen 
    ```
    
      
    
    ```Shell
    michalroziel@MBP-michal-5 ~ % ps -ef | less
    michalroziel@MBP-michal-5 ~ % ps -ef | grep "^root" | wc -l
           0
    michalroziel@MBP-michal-5 ~ % ps -ef | grep "^michalroziel" | wc -l
           0
    michalroziel@MBP-michal-5 ~ % ps -ef | less                        
    michalroziel@MBP-michal-5 ~ % ps -ef | grep "^usr" | wc -l
           0
    michalroziel@MBP-michal-5 ~ % ps -ef | grep "^em" | wc -l
           0
    michalroziel@MBP-michal-5 ~ % ps -ef | grep "^System" | wc -l
    ```
    
      
    
    > [!important] pstree command → show a tree of working processes
    
      
    
    ```Shell
    michalroziel@MBP-michal-5 ~ % echo $PWD $OLDPWD
    /Users/michalroziel /Users/michalroziel
    michalroziel@MBP-michal-5 ~ % cd Documents 
    michalroziel@MBP-michal-5 Documents % cd htwbse 
    michalroziel@MBP-michal-5 htwbse % cd 
    michalroziel@MBP-michal-5 ~ % echo $PWD $OLDPWD
    /Users/michalroziel /Users/michalroziel/Documents/htwbse
    michalroziel@MBP-michal-5 ~ %
    ```
    
      
    
    ```Shell
    michalroziel@MBP-michal-5 ~ % printenv
    __CFBundleIdentifier=com.apple.Terminal
    TMPDIR=/var/folders/2s/vd7b_xhn4k5gfdfh7n9385300000gn/T/
    XPC_FLAGS=0x0
    TERM=xterm-256color
    SSH_AUTH_SOCK=/private/tmp/com.apple.launchd.NTeNnQuAqO/Listeners
    XPC_SERVICE_NAME=0
    TERM_PROGRAM=Apple_Terminal
    TERM_PROGRAM_VERSION=450
    TERM_SESSION_ID=A2506EF6-805F-4E73-BEC0-6F27FA1295D7
    SHELL=/bin/zsh
    HOME=/Users/michalroziel
    LOGNAME=michalroziel
    USER=michalroziel
    PATH=/opt/homebrew/opt/openjdk@17/bin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/System/Cryptexes/App/usr/bin:/usr/bin:/bin:/usr/sbin:/sbin:/var/run/com.apple.[[my-notes-site/node_modules/typescript/SECURITY|SECURITY]].cryptexd/codex.system/bootstrap/usr/local/bin:/var/run/com.apple.[[my-notes-site/node_modules/typescript/SECURITY|SECURITY]].cryptexd/codex.system/bootstrap/usr/bin:/var/run/com.apple.[[my-notes-site/node_modules/typescript/SECURITY|SECURITY]].cryptexd/codex.system/bootstrap/usr/appleinternal/bin:/Library/Apple/usr/bin
    SHLVL=1
    PWD=/Users/michalroziel
    OLDPWD=/Users/michalroziel/Documents/htwbse
    HOMEBREW_PREFIX=/opt/homebrew
    HOMEBREW_CELLAR=/opt/homebrew/Cellar
    HOMEBREW_REPOSITORY=/opt/homebrew
    MANPATH=/opt/homebrew/share/man::
    INFOPATH=/opt/homebrew/share/info:
    LC_CTYPE=UTF-8
    _=/usr/bin/printenv
    michalroziel@MBP-michal-5 ~ %
    
    -> printenv gibt uns die Umgebung aus 
    
    
    ```
    

  

  

## Meta Zeichen zur Namenssetzung

- gelten für alle Einträge im Baum

- dienen zur Auswahl mittels Namensmustern ( pattern matching )

> [!important] “ * “ → kein, ein, viele Zeichen ( Ausnahme : “ . “ am Beginn des Namens

> [!important] “ ? “ → genau ein Zeichen ( Ausnahme : “ . “ am Beginn des Namens )

  

> [!important] [ string ] → genau ein Zeichen aus dem String [ cms ], [ scm ], [ ccccssmmmm ]

  

> [!important] [ !string ] → kein Zeichen “ “ “

> [!important] [z_1 - z_2 ] → genau ein Zeochen aus der Zeichenfolge z_1 .. z_2

  

> [!important] [[remote-notes/sem3/mikro/Tests/Tests|Tests]] : [ ! - 0 ] [ ! ! ! ] [ ! - - 1 ]

### Beispiele

  

```Shell
z.B : ls -d * m * 
z.B : ls -d ??? -> name von drei zeichen und gehe nicht in die Tiefe 

z.B : ls x- [ cms ]* 

z.B : ls -d x-*[0-2cms-z]*
			-> entweder ein c oder ein m oder ein zeichen zwischen s und z 
```

  

```Shell
 /export /home_  
```