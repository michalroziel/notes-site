### Erklären, was /dev/random ist

`/dev/random` ist eine Datei in Linux Betriebssystemen, welche mit Zufallszeichen gefüllt ist. Standardmäßig sind diese in `base64` gecoded, also für Menschen unlesbar.

Um wirklich zufällige Zufallszahlen zu generieren, beispielsweise für Passwörter, kann man `/dev/random` verwenden. → Es ist direkt mit Kernel verbunden, Falls Muster entdeckt werden, werden diese direkt neu generiert.

→ Hohe Entropie

  

###   
1. Erklären, was head, cut und sed machen

`head` zeigt die ersten ==**X**== Zeilen oder Bytes eines bestimmten Datei an → default = 10

`cut` wird benutzt um innerhalb einer Datei Spalten zu trennen bzw Zeichen zu schneiden

`sed` steht für stream editor, und wird benutzt um Zeichen oder spezifizierte Elemente zu ersetzen.

  

### berechnen, wie viele Bits ein 32-Zeichen Hash hat

Da wir 4 bits fpr ein HEX Zeichen brauchen → 128 Bits

  

## HashMACs

  

###   
Unter welchen Rahmenbedingungen funktioniert die Authentifizierung mit einem HashMAC

Die Rahmenbedingungen sehen wie folgt aus : Jeder Der Kommunikationspartner hat einen Secret Key, mit dem vom Sender ein Digest erstellt wird, und anschließend ein Digest vom Empfänger erstellt wird. Diese werden dann verglichen. Bei dem Verschicken wird dieser allerdings nicht mitgeschickt. Dies ist die Baseline von Mac. HMAC arbeitet mit MACs, aber schreibt zusätzlich noch eine Weise vor wie das Verfahren durchgeführt wird.

Der HashWert wird zusammen mit der Message geschickt, aber nicht der secret key !

### Alice hat ein Dokument mit HMAC verschlüsselt - welche CIA-Eigenschaft wird damit garantiert?

Damit wird die Integrity gewäherleistet.

###   
Gibt es noch andere Wege, um diese Eigenschaft zu garantieren?

- Public Key Infrastructure

- CRC Prüfverfahren aud Bit-Ebene

  

##   
Semaphoren und Shared Memories

### Geben Sie jeweils ein Argument an, warum man statt Shared Memory nicht folgende Methoden nutzt:

1. Übergabe von Werten beim Start (Funktionsparameter, [[Umgebungsvariablen]])

1. Schreiben und lesen aus Dateien

1. Kommunikation via TCP/IP

  

1. Daten sind nur einmal übergebbar → Änderung zur Laufzeit sind nicht möglich.

1. Zu langsam, da auf die Festplatte zugegriffen / gelesen werden müssen.
    
    Es entstehen unnötige `I/O` Operationen.
    

1. **Komplexer** und mit zu viel **OverHead** verbunden → Protokoll / Socket-Handling
    
    Braucht viele Ressourcen obwohl Prozesse lokal laufen
    
      
    

  

### Lückentext zu Semaphoren (Zahlen mit + und - einsetzen)

  

1. Eine Semaphore wird initiiert wenn die Ressource verfügbar ist mit : `1`

1. Bei einer P-Operation wird `-1` gerechnet, danach hat die Semaphore den Wert `0`

1. Wird eine P-Operation auf einer Semaphore aufgerufen kann sie nur durch, wenn die Semaphore größer als `0` ist, sonst blockiert sie

1. Ein Prozess führt eine V-Operation aus, dabei wird `+1` gerechnet und die Semaphore hat den Wert `1`