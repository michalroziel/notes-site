August 20, 2025

Es gibt Tickets für eine Veranstaltung. Die Tickets enthalten eine QR-Code mit Name, Vorname, E-Mail-Adresse und Ticketnummer des Besuchers. Der QR-Scanner hat keinen Zugang zum Internet.

  

### a) Bestimmen Sie, wie in diesem Kontext die CIA-Eigenschaften dargestellt werden können.

**Confidentiality (Vertraulichkeit)** ist hierbei nicht automatisch gegeben, Wenn etwas keinen Zugang zum Internet hat, bedeutet das nicht automatisch, dass eine Nachrichtenübertragung geheim stattfindet. Vetraulichkeit könnte gewährleistet werden, wenn keine privaten User Daten übertragen / angezeigt werden.

  

**Integrity (Integrität)** ist auch nicht garantiert. Auch wenn das Gerät nicht ans Internet verbunden ist, könnte eine Person den QR Code bei dem Scannen modifizieren. → `Screenshots`

→ Wird nicht vor Duplicates / Verfälschungen geschützt.

  

**Availability** ist nicht direkt gegeben, bei einem Kaputten Scanner / nassem Papier wäre das scannen nicht möglich

  

### b) Mit welchen von Ihnen durch die Vorlesung bekannten Mittel könnte die Sicherheit des Systems gewährleistet werden?

- **[[Encryption]]** für `Confidentiality`, **Schutz vor unbefugten Zugriff**

- **Hashverfahren** für `Integrity` , Schutz vor unbemerkter Veränderung

- AusfallSichere Scanner oder QR auf Plastik Karten anstatt auf Papier für **Availability**

  

  

### Schreiben Sie ein Bash-Script, welches als Argument einen Ordner D entgegennimmt und folgenden Output erstellt:

```Bash
~$ script.sh /etc/irgendwas

1 a.txt
2 b.mp4
3 c.pdf
```

Das Skript soll Exit-Code 1 ausgeben, wenn es den Ordner nicht gibt und Exit-Code 2, wenn der Ordner leer ist.

# UNIX und Timestamps

a) Sie sind Nutzer eines UNIX-Systems und möchten ein Programm starten. Sie sehen folgenden Terminal-Output:

```Bash
~$ firefox
-bash: firefox: command not found
```

### Geben Sie 3 Möglichkeiten an, was passiert sein könnte und wie man es beheben kann.

- firefox könnte nicht installiert sein,
    
    - Man könnte es mit einem package manager installieren → `brew install firefox`
    

- Das alias auf ein [[plugin]] `web_search` könnte nicht gesetzt sein :
    
    - `alias firefox=web_search firefox`
    
      
    

- Es kann vielleicht nicht im `$PATH` liegen, somit wird es nicht gefunden
    
    - ergänze firefox zu [[Umgebungsvariablen]]
    

  

### b) Erklären Sie, welches Problem welche UNIX-Systeme am 19.01.2038 bekommen

Ab dem 01.01.1970 wird die Zeit in UNIX Systemen in einer Variable `time_t` gemessen.

Ab dem **19.01.2038** werden 32 Bit Systeme nicht mehr mit der Zeit Messung klarkommen , da Sie die Zeit nicht mehr in der Variable speichern können.

  

### c) Sie sind in einem UNIX-System eingeloggt. Wie können Sie herausfinden, welches Betriebssystem läuft?

Mite dem Kommando `uname -s` Kann man den Namen des OS herausfinden : `MacOS : Darwin`

  

  

# Semaphores und Shared Memory

### Wozu ist Shared Memory gut und wieso braucht man meist Semaphoren, um es korrekt zu benutzen?

  

Shared Memory erlaubt uns, einen gemeinsamen Speicherblock für zwei oder mehrere Prozesse zu benutzen. Diese Prozesse wollen gelichzeitig auf dem Speicherplatz arbeiten, das geht allerdings nur falls gesteuert wird wer wann arbeiten kann, diese Aufgabe überhnehmen Semaphoren. Semaphoren sind Kontrollstrukturen, welche steuern wie viele Ressourcen gerade reserviert sind, weil Prozesse darauf arbeiten, und wie viele Ressourcen frei sind (reserviert werden können). Um das umzusetzen implementieren Semaphoren Zähler (counter) um die Anzahl der freien oder reservierten Ressourcen zu protokollieren.

  

## Was passiert, wenn ein Hacker

  

### a) die IP eines Rechners verändern kann

Der Hacker kann so das Verschicken / Empfangen von Nachrichten umleiten, sodass beispielsweise ein angegriffener Rechner keine Packets mehr von den gewünschten Kommunikationspartnern erhält, sondern von dem PC des Hackers.

Hierbei könnte es zum Beispiel zu einem `man-in-the-middle` attack kommen. Ein Hacker könnte sich somit auch als einer der Kommunikationspartner ausgeben → `defrauding`

  

### b) das Default Gateway verändern kann

Wenn ein Hacker das default GateWay ändern würde, könnte er beispielsweise eine Route zu seinem eigenen PC eintragen, so dass beim versuch Packets ins Internet zu verschicken, diese anschließend zu dem Hacker gelangen würden

  

### c) den DNS-Server verändern kann

Falls ein Hacker einen DNS Name Server ändern würde, dann könnte er beispielweise das bekannten IP Adressen Mapping ändern, sodass `[google.com](http://google.com)` nicht zu der eigentlich IP korrespondieren würde, sondern zu einem von dem Hacker aufgestellten `Web Service` .

Andernfalls könnte er auch vielleicht `MX Records` ändern, und so Email Einträge ändern, dass eine Email Adresse so wirkt, als wäre Sie eine dem `User` bekannte.

  

### Erklären Sie den Unterschied zwischen Public-Key Verschlüsselungsverfahren und symmetrischen Verschlüsselungsverfahren (in exakt drei Sätzen!).

  

Ein symmetrisches Verschlüsselungsverfahren arbeitet so, dass der Schlüssel mit dem eine Nachricht verschlüsselt wird, genau der gleiche ist, wie der mit dem Sie wieder entschlüsselt wird. Das Public Key Verfahren arbeitet mit 2 Schlüsseln, der Public Key ist offen für jeden und verschlüsselt Nachrichten, während der Private Key stets privat bleibt und der einzige Key ist, mit dem Nachrichten entschlüsselt werden können. Das Public Key verfahren ist sicherer als das symmetrische Verfahren.

  

  

### Es wurde eine Sicherheitslücke in `libc.so`, welche von einem Programm `prog` benutzt wird, gefunden.

  

### a) Wie stellen Sie fest, ob `prog` von diesem Problem betroffen ist?

Auf Linux können wir den Befehl `ldd` verwenden, um zu schauen ob die Dependency `[libc.so](http://libc.so)` in dem Programm `prog` dynamisch eingebunden wird. ldd → `list dynamic dependencies`

Falls es dort aufgelistet wird, dann ist `prog` ebenfalls davon betroffen.

### b) Welches Problem stellt die Sicherheitslücke für die Sicherheit des Gesamtsystems dar?

Durch die Sicherheitslücke in `[libc.so](http://libc.so)` könnte Malware bei dem ausführen des Programms `prog` gelangen. Somit könnten Würmer oder andere Viruse in das System gelangen.

  

### c) Was ist beim Beheben der Sicherheitslücke zu beachten?

Bei dem beheben dieser Sicherheitslücke muss man Abhängigkeiten und Versions unterschiede beachten. Hierbei könnte eine Änderung in `[libc.so](http://libc.so)` negative Auswirkungen auf die Funktionalität von `prog` haben

- Zusätzlich sollte man den HashWert von einer `Trusted authority` prüfen, ob dieser mit dem lokalen Hashwert der binary übereinstimmt