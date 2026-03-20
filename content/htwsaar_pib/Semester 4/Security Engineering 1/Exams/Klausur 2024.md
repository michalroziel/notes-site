  

- **Situation**: Auf einem System sind zwei verschiedene Programme installiert:
    
    - `/usr/bin/ssh`
    
    - `/usr/local/bin/ssh`
    

- **Fragen & Antworten**

### Wie kann man herausfinden, welches Programm durch den Befehl `ssh` gestartet wird?

→ Das, welches in $PATH zuerst vorkommt.

### Wie kann der Admin ohne die Installation der Programme zu verändern, die Programme durch `ssh1` und `ssh2` aufrufbar machen?

  

```Bash
alias /usr/bin/ssh=ssh1
alias /usr/local/bin/ssh=ssh2

ln -s /usr/bin/ssh1 /usr/bin/ssh
ln -s /usr/local/bin/ssh2 /usr/local/bin/ssh
```

  

### Was passiert auf Ebene der Systemcalls, wenn ein Benutzer ein Programm per Kommandozeile startet? Dabei soll man annehmen, dass man sich im Hintergrundprozess befindet

### Typischer Ablauf beim Programmstart (aus einem laufenden Prozess, z. B. einer Shell):

1. `**fork()**`
    
    – Der aktuelle Prozess (z. B. die Shell) erzeugt einen Kindprozess.
    

1. `**execve()**`
    
    – Das Kind ersetzt seinen Speicherbereich durch das neue Programm (z. B. `ls`, `ssh` …).
    
    – Dabei wird das Programmfile (ELF-Binary, Script) vom Kernel geladen.
    

1. `**wait()**`
    
    – Der Elternprozess (die Shell) wartet ggf. auf die Beendigung des Kindes, um den Rückgabewert zu bekommen.
    

  

### Nenne 4 Verschiedene Benutzershells

- zsh - Z Shell

- csh - [[C]] Shell

- bash - Bourne again shell

- ksh - Korn Shell

- sh - shell

  

### Erläutern, wie man alle lokalen Login-Namen ausgeben kann (Format wie bei der Datei /etc/passwd)

  

`ls /Users`

`cut -d: -f1 /etc/passwd`

  

### Was bedeutet das Kürzel aes-128-cbc?

Dieses Kürzel ist ein ==**Verschlüsselungsverfahren**==, hierbei steht `aes` für `advanced [[[[Encryption]]]] system` . `CBC` bezieht sich auf `Cipher` `Blocking` `Chain`. Es handelt sich um eine 128 Bit verschlüsselung

  

### Abschätzen, eie lange 1000 CPUs mit je 1 GHz Takt brauchen, um einen 128-Bit langen Schlüssel zu knacken. Dabei sollte man annhemen, dass pro Schlüssel 100 Takte gebraucht werden (bei Brute-Force Attacke)  

  

Wenn eine CPU mit **1  GHz** läuft und **100 Takte pro Schlüssel** braucht: Wie viele **Schlüssel pro Sekunde pro CPU** schafft sie?

(1 GHz = $10⁹$ Takte/s) , und wir bauchen **100** Takte/Schlüssel

Somit können wir $10⁷$ Schlüssel Pro Sekunde durchteste, und mit 1000 CPUs sind es $10¹⁰$ Schlüssel pro Sekunde.

  

Mit **128 Bits** haben wir $2¹²⁸$ Mögliche Kombinationen.

  

### Sagen, ob Aussagen zu Hard- und Softlinks wahr der falsch sind + Begründung

  

Ein Programm hatte folgende Zeiten (time-Befehl)

`real:55.399s user:22.34s system:0.003s`

  

### Wie lange hat der CPU gerechnet

Das System hat `user + system` Zeit gerechnet

  

### Wie lange musste der Benutzer auf das Ergebnis warten?

Der Benutzer hat `real` Zeit gebraucht

  

### War das Program I/O-Intensiv

Ich denke ja, weil der User für 22 Sekunden Damit beschäftigt war, input zu lesen / Einzugeben

  

### 2 Fälle schildern, die bewirken können, dass es diesen recht großen Unterschied zwischen real und user gibt

  

- CPU ist ausgelastet mit höher priorisierten Tasks

- Viele Libraries müssen zur Runtime geladen werden

  

### Semaphoren und Shared Memory erklären und dabei auf die Funktion `int semop(int semid, struct sembuf *sops, size_t nsops)` eingehen (auf die sembuf-Struktur musste nicht genauer eingegangen werden)