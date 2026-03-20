# Aufgabe 1 (Klassifizierung im CIA–Modell)

  

### Welche Sicherheitsziele des CIA–Modells sind in den folgenden drei Vorfällen verletzt?

Geben Sie einen Tipp, was der Nutzer tun kann oder was in diesen Systemen verändert wer-  
den muss, damit die Sicherheitsziele für den Nutzer trotzdem umgesetzt werden können.

  

### a) Meldung der Linux Mint Distribution am 21.02.2016

We were exposed to an intrusion today. It was brief and it shouldn’t impact many people, but if it impacts you, it’s very important you read the information below. Hackers made a modified Linux ==Mint ISO==, with a backdoor in it, and managed to hack our website to point to it

  

- `Integrity` wurde verletzt, da die Linux Mint `.iso` modifiziert wurde.

- User sollten die `Linux Mint .iso` Version nicht herunterladen, und warten bis eine gepatchte, offizielle Version veröffentlicht ist, dann mittels HashCodes die Echtheit prüfen, ggfs unter Benutzung einer Trudted Authority

### b) Meldung auf [heise.de](http://heise.de/) am 30.06.2016

Bei Vodafone/Kabel Deutschland sind derzeit Internetzugang und Telefon in "weiten Teilen von Deutschland" gestört. Das bestätigte das Unternehmen im eigenen Support-Forum. Betroffen sind nur Internetanschlüsse über das TV-Kabelnetz der ehemaligen Kabel Deutschland. Zahlreiche Nutzer beschweren sich auf Twitter über Totalausfälle, auch auf den Störungsmeldungsplattformen gehen vermehrt Hinweise ein.

  

- `Availiability` wurde hier verletzt.

- User könnten anstatt das TV-Kabelnetz und das ehemalige Kabel Deutschland auf WLAN umsteigen.

  

### c) Meldung auf [heise.de](http://heise.de/) am 18.07.2016

Kunden der Direktbank Comdirect hatten am Montagmorgen nach dem Einloggen in ihr Konto Einblick in fremde Konten. Mehrere Leser von heise online konnten das Problem nachvollziehen. Demnach konnten sich die Nutzer zwar einloggen, sahen dann aber die Kontodaten - also  
beispielsweise den Kontostand - anderer Nutzer und konnten auch das Postfach einsehen.

  

- `Confidentiality` wurde verletzt, da private Infos an dritte gelangt sind.

- Comdirect Specialists könnten auf ein funktionierendes System snapshot zurückgreifen.

- Zugriffsrechte ändern, damit jeder User nur seine Infos sehen kann.

  

  

# Aufgabe 2 (chmod)

![[Screenshot_2025-08-20_at_17.26.23.png]]

  

  

# Aufgabe 3 (Statisches vs. dynamisches Linken von Programmcode)

  

# Aufgabe 4 (Prozess–Erzeugung)

  

  

  

# Aufgabe 6 (SETUID–Bit)

  

### a) Warum kann man den Zugriﬀ auf `/etc/master.passwd` (bzw. `/etc/shadow` unter Linux/Solaris) nicht alleine mit den normalen Filezugriﬀsbits rwx realisieren?

- Würde man “normale” `rwx` benutzen, dann wäre es zu grobgrnaular. Wäre es erlaubt, dann könnte jeder Nutzer PW-Hashes kopieren und offline knacken

### b) Wie wirkt das für solche Zugriﬀe eingeführte SETUID–Bit?

Das `SETUID` Bit ermöglicht das ausführen eines Programmsi mit den Rechten des Datei-Owners.

### c) Warum ist beim Setzen eines SETUID–Bits die Gefahr einer Sicherheitslücke gegeben?

Bei einer Sicherheitlücke wie ienem Buffer Overflow / ähnliches könnte ein User `root` - Rechte erlangen, und diese ausnutzen.