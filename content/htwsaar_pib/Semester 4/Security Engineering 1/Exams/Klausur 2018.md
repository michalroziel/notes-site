  

# Aufgabe 1 (Sicherheitsprobleme) (3+3 P.)

**a**)

Der Mitarbeiter der Bundestagsverwaltung Christoph beklagt sich, dass die Inhalte  
seines streng geheimgehaltenen Dokuments haushaltsplanung 2019.pdf bekannt  
wurden. Er hat das Dokument auf dem UNIX-Server des Bundestages mit dem  
Befehl `chmod 600 haushaltsplanung 2017.pdf` gesichert.**Geben Sie drei mögliche Szenarien an, wie das Dokument trotzdem frühzeitig an die**  
**Öﬀentlichkeit gelangt sein könnte.**

  

1. Jemand hat die [[Login]] Daten von Christoph herausgefunden, diese genutzt um sich auf dem Portal zu registrieren und die PDF herunterzuladen.

1. Christoph ist zwar **Owner der Datei,** aber nicht `root`. Der `root` user kann **immer** auf Dateien zugreifen.

1. Die Datei liegt in einem Directory mit “Lockeren” Rechten, etwa `/tmp` oder ähnliches.  
    → Wenn die Directory in der die Datei liegt, die Rechte `777` hat, dann haben automatisch alle darin liegenden Dateien `777` .

  

**b)**

Am 20.02.2016 drangen Hacker in den Server der Linux-Distribution Mint ein und  
fügten Schadcode in das Download-Image für die Mint–CD (ISO) ein.

**Wenn Sie untersuchen sollten, wie es zum Eindringen der Hacker kam, an welchen Stellen**  
**würden Sie ansetzen (3 Möglichkeiten)?**

  

1. `syslogd` - Alles was in einem Linux OS passiert, wird in ein System Log geschrieben, hier würde stehen was vorgefallen ist, und welche Schritte die Hacker vorgenommen haben.

1. Prüfen ob der Server `CVE` Schwachstellen hat (==**Common Vulnerability Enumeration**==) Dies könnte man auf Foren online nachschauen

1. Prüfen der Integrität mit Offiziellen Prüfummen - etwa MD5. Checken ob Hacker neue Benutzer Accounts hinzugefügt haben

  

# Aufgabe 2 (Sicherheitsmechanismen)

**a)** Zu Softwarepaketen (wie z.B. ISO-Images) werden häaufig solche Hexcodes angegeben :

  
`6e7f7e03500747c6c3bfece2c9c8394f linuxmint-17.3-cinnamon-32bit.iso`

  

### i) Was bedeuten diese Hexcodes?

Hexcodes wie diese bezeichnen Prüfsummen - Checksums, mit denen wir als Nutzer die integrität, also die Echtheit einer jeweiligen Linux Distribution prüfen können.

  

### ii) Wie wurde obenstehender Hexcode vermutlich erzeugt?

Die HexCodes wurden vermutlich mit einem HashAlgorithmus wie `MD5` erzeugt.

→ 32 HexZeichen, 32 * 4 = 128 bit, MD5 hat 128 BIts

  

### iii) Wodurch entsteht die Sicherheit, die dieser Hexcode bereitstellen soll?

Die Sicherheit entsteht durch den Fakt dass es möglich ist, die Integrität dieser Hashes zu prüfen. Es ist nicht irgendeine Zahl, sondern ein klarer unique HashWert welcher in der Lage ist, die Echtheit zu gewährleisten. Auch eine kleine Änderung produziert einen komplett anderen HashWert.

  

### iv) Welche Sicherheitseigenschaft (im CIA–Modell) soll hierdurch bereitgestellt werden?

Hierduch wird die Eigenschaft der Integrity, Integrität gewährleistet. Falls jemand Änderungen an der `.iso` Datei vornimmt, werden diese durch einen ganz anderen HashWert gekennzeichnet.

  

### v) Bonusfrage: warum ist gerade dieser linuxmint-Hexcode nicht besonders vertrauenswürdig?

Hierbei ist der HexCode nicht besonders vertrauenswürdig, da wir Ihn nicht vergleichen können. Beispielseweise konnten Hacker auch Online den HashWert ändern, somit würde es so aussehen, als ob es die “echte” `.iso` Datei ist.

  

  

**b)** Verschlüsselung

OpenSSL bietet Ihnen zum Verschlüsseln von Nachrichten die Möglichkeiten:

  

`-aes-128-cbc -aes-128-ctr -aes-128-ecb -aes-128-xts -aes-192-ctr -aes-192-ecb -aes-256-cbc -aes-256-ctr -aes-256-ecb -des-cbc -des-ecb`

  

### i) Von welchen Modi sollte man abraten und warum?

Man sollte Nutzer von dem Benutzen von `*-ecb` Methoden abraten, da diese Verschlüsselungsmethoden stets Blockweise encrypten. Das Bedeutet Anschaulich, dass bei einem Bild etwa auch nach dem encrypt immernoch Muster erkennen kann.

`*-des-` hat nur eine Key Length von `65` Bits.

`*-xts`

Besser wäre die Variante mit `*.cbc` , da hierbei Jeweils das verschlüsselte Element als Input für die nächste [[Encryption]] genommen wird.

  

  

### ii) Welche Sicherheitseigenschaft (im CIA–Modell) soll durch Verschlüsseln bereitgestellt werden?

Durch das Verschlüsseln sollte die Confidentiality gewährleistet werden.

  

  

  

# Aufgabe 3 (Klassifizieren von Sicherheitslücken)

Am 23.02.2018 wurden folgende Sicherheitslücken zu Apache Tomcat beschrieben

![[Screenshot_2025-08-19_at_14.59.08.png]]

### Welches grundlegende Sicherheitsziel (im CIA–Modell) wurde durch diese Lücken verletzt?

  

Hierbei wurde die Confidentiality verletzt. Nicht vorher authorisierte User hatten Zugriff auf Dateien welche Sie eigentlich nicht accessen dürften. Web Services wurden exposed

  

  

# Aufgabe 4 (System Calls)

Kommentieren Sie die mit ,,*” markierten folgenden CALL-Zeilen des `ktrace/kdump`–  
Output. Welches UNIX-Kommando mit welchen Parametern wollte der Benutzer hier  
ausführen und was war das Problem hierbei?

  

> [!important]
> 
> - `**ktrace**` **= aufzeichnen** (Kernel/Process Events in Datei schreiben).
> 
> - `**kdump**` **= anzeigen** (Trace-Datei interpretieren und ausgeben).

  

```Bash
*11759 ln CALL stat(0xbfbfe7ef,0xbfbfe570)   // Prüfen ob die Datei ls existiert
11759 ln NAMI "ls"
11759 ln RET stat 0
*11759 ln CALL lstat(0xbfbfe7f2,0xbfbfe570)  // Prüfen ob das Verzeichnis doir existiert
11759 ln NAMI "dir"
11759 ln RET lstat -1 errno 2 No such file or directory
*11759 ln CALL stat(0xbfbfe7f2,0xbfbfe570)   // Prüfen ob eine datei mit dem Namen dir existiert
11759 ln NAMI "dir"
11759 ln RET stat -1 errno 2 No such file or directory
11759 ln CALL lstat(0xbfbfe7f2,0xbfbfe570)
11759 ln NAMI "dir"
11759 ln RET lstat -1 errno 2 No such file or directory
*11759 ln CALL link(0xbfbfe7ef,0xbfbfe7f2)   // Versuch den hardlink ln ls dir anzulegen
11759 ln NAMI "ls"
11759 ln NAMI "dir"
11759 ln RET link -1 errno 13 Permission denied
```

Der Benutzer wollte einen Hardlink von ls auf dir erstellen. `ln ls dir`

  

# Aufgabe 5 (chmod)

Ergäanzen Sie folgende Tabelle, die den Zustand der (mit “ls -l” sichtbaren) Zugriﬀsrechte  
einer Datei mittels `chmod [mode] datei` wobei Sie als “mode” den absoluten Wert per Oktalsystem einsetzen.

|   |   |   |
|---|---|---|
|[mode]|Zugriﬀsrechte||
|640|`r w -` `r - -` `- - -`||
|4711|`r w s` `- - x` `- - x`||
|4550|`r - s` `r - x` `- - -`||
|1777|`r w x` `r w x` `r w t`|WICHTIG : Hinten ==“t”==|
|755|`r w x` `r - x` `r - x`||
|4750|`r w s` `r - x` `- - -`||
|2751|`r w x` `r - s` `- - x`||
|554|`r - x` `r - x` `r - -`||
||||

  

# Aufgabe 6 (Statisches vs. dynamisches Linken von Programmcode)

  

Erklären Sie, was statisches und dynamisches Linken bedeutet.  
Geben Sie die jeweiligen Vorteile der beiden Methoden an.

  

Statisches Linken Beschreibt das Einfügen von alle benötigten Libraries in das zu gestartete Programm.

==Vorteil== wäre, dass so alle benötigten Dependencies zur Compile Time vorhanden sind

==Vorteil== wäre dass kein Laden von Libraries mehr notwendig ist.

Dynamisches Linken beschreibt das “on-demand” Einfügen von Libraries, dies passiert zur Runtime.

==Vorteil== wäre dass die resultierende executable file kleiner ist.

  

# Aufgabe 7 (Shellskript)

Schreiben Sie ein Shellskript `secret-job`, das einen Benutzernamen und ein Passwort ent-  
gegennimmt. Gültige Benutzernamen/Passwort–Kombinationen sollen in der Datei `/etc/secret-job.conf` wie folgt gespeichert sein.

  

```Bash
john unZ7wx
paul Yk09v1
ringo 8jmWxa
george 3pknmA
```

  

Wenn eine richtige Passwort–Kombination eingegeben wurde, soll das Verzeichnis `/tmp/user`  
angelegt werden, wobei userder eingegebene Benutzername ist.

Falls das Verzeichnis schon existiert, soll es gelöscht und neu angelegt werden.  
Der Benutzer soll durch entsprechende Meldungen über den Ablauf des Skripts informiert  
werden.

  

```Bash
#!/bin/bash

CONF="./secret-job.conf"

echo "Bitte Username und Passwort eingeben:"
read -r user pass

if grep -q "^$user $pass$" "$CONF"; then
    echo "Login ok."
    target="./tmp/$user"
    rm -rf -- "$target"    # falls schon da
    mkdir -p -m 700 -- "$target"   # -p = rekursiv
    echo "Fertig."
else
    echo "Ungültige Kombination."
fi
```

# Aufgabe 8 (Prozess–Erzeugung)

Betrachten Sie folgendes Programmfragment, das von einem Prozess P0 durchlaufen werde:

![[Screenshot_2025-08-19_at_16.55.34.png]]

  

Nehmen Sie an, alle `fork()`–Aufrufe sind erfolgreich.

> [!important]
> 
> Verwenden Sie die Notation ==$P_i$== füur den i–ten gestarteten Prozess (i ≥ 1).  
> Geben Sie zu jedem Pi an, in welcher Zeile er erzeugt wurde und welcher  
> Prozess sein Vater ist.

Notieren Sie die Ausgaben, die bei Abarbeitung des Programmfragments auf dem Bild-  
schirm zu sehen sind, zusammen mit der Prozessbezeichung, nur als Beispiel, nicht unbe-  
dingt eine Ausgabe dieser Aufgabe