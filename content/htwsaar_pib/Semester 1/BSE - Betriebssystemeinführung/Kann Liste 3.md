  

## 1. UID ( USer id ) und GID ( Group Id ) anzeigen lassen

```Shell
michal@mlatitude:~$ id
uid=1000(michal) gid=1000(michal) groups=1000(michal),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),136(sambashare)
michal@mlatitude:~$
```

- Group Id: Analog zur Rolle in Discord

  

## 2. Weiß, was die Umgebbungsvariableben LOGNAME und HOME enthalten, + wie Inhalte anzeigen lassen

  

- LOGNAME gibt eingelogten User aus

- HOME gibt den das home Directory von dem User

  

## 3. Weiß, wie ich mir die Umgebungsvariablen der Shell anzeigen lassen kann

```Shell

printenv -> print environment ( Umgebung ) 
```

- Gibt Systemvariabeln aus

  

  

## 4. Kann den Inhalt des root-Directory von Linux ausgeben

  

```Shell
michal@mlatitude:~$ ls /
bin   cdrom  etc   lib    lib64   lost+found  mnt  proc  run   srv       sys        tmp  var
boot  dev    home  lib32  libx32  media       opt  root  sbin  swapfile  timeshift  usr
michal@mlatitude:~$
```

  

  

## 5. root-directory vs home directory vs working directory

- Working Directory: aktueller Pfad ( pwd → print working directory )

- home directory → Benutzer Ordner ( echo $HOME )

- root directory → Wurzel des dateisystems ( ls / )

  

## 6. Absolute vs relative path

- absolute Path : Gesamte Adresse beginnend bei der Wurzel des Dateisystems

- relative : Abhängig von dem aktuellen Standort

  

## 7. weiß, ob der absolut oder relative pfad länger ist

- der absolute Pfad ist immer länger

  

## 8. Kenne drei verschiedene Arten, wie ich vom WORKING Directory PRG-SPR/ueb01 ins Verzeichnis Beispiele/c  
komme:

- mit Angabe des absoluten Pfads

- mit relativem Pfad und Sonderzeichen ".."

- mit relativem Pfad und Sonderzeichen "~"  
    Dabei liegen die beiden Verzeichnisse PRG-SPR/ueb01 und  
    Beispiele/c in meinem HOME-Directory .

  

```Shell
cd /usr/miro00009/home/Beispiele/c   -> Absoluter pfad 

cd ../Beispiele/c  -> relativer pfad 

cd ~/Beispiele/c

```

  

## 9. weiß, welche informationen die folgenden Verzeichnisse enthalten : /etc , /usr , /dev , /proc , /export , /home

  

- /etc → Konfigurationsdateien

- /usr → Nutzerdateien → home folder

- /dev → Alle Geräte und Kanäle die es im System gibt

- /proc → Alle Prozesse und deren Kanäle

- /export → Daten die im netzwerk zu verfügung gestellt werden

- /home → home Verzeichniss

  

## 10.

  

- b → Blockgeräte ( Bsp. Festplattenpartitionen )

- d → Directories ( Ordner )

- c → Zeichenorientierte Geräte ( Tastatur )

- l → Links ( Verknüpfungen )

  

  

## 11. Weiß, welche Informationen die folgenden Verzeichnisse enthalten : cd , cd ~ , cd~pauly , cd ../.. cd.

  

```Shell
cd -> home directory 
cd ~ -> home directory 
cd ~pauly -> home directory vom pauly 

cd ../.. -> zwei Ordner Höher

cd . -> aktueller Ordner +

```

  

## 12.

  

PWD → current working directory

OLDPWD → vorherige working directory

cd - → cd $OLDPWD

  

## 13.

```Shell
. -> aktueller Standort 
.. -> parent Standort 
```