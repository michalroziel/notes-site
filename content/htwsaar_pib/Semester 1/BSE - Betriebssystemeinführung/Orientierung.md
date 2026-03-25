- Kann - Listen bearbeiten !

  

### Wer bin ich ?

  

- [[Login]] / Realer User

- Effektiver User
    
    - User wechseln in der Shell
    

  

```Shell
logname -> wie lautet der Name des Benutzers der sich angemeldet hat 


echo $LOGNAME -> in der variable LOGNAME nachschauen 

su - pickpi22 -> mit su den benutzer wechseln ( -> switch user ? ) 

echo $LOGNAME -> ein anderer benutzer meldet sich 

logname <-> echo $LOGNAME liefert andere benutzer 


whoami - Kommando 

wer benutzer -> logname 

wer ist der effektiver benutzer -> whoami 


" id " -> michalroziel@MBP-michal-5 htwbse % id
uid=501(michalroziel) gid=20(staff) groups=20(staff),12(everyone),61(localaccounts),79(_appserverusr),80(admin),81(_appserveradm),98(_lpadmin),33(_appstore),100(_lpoperator),204(_developer),250(_analyticsusers),395(com.apple.access_ftp),398(com.apple.access_screensharing),399(com.apple.access_ssh),400(com.apple.access_remote_ae),701(com.apple.sharepoint.group.1)
michalroziel@MBP-michal-5 htwbse %


			gid -> gruppen id 



```

  

## Wo bin ich im Dateisystem ?

- Immer in “ Working Directory “ → Arbeitsverzeichnis

```Shell
pwd ->  print working directory 
michalroziel@MBP-michal-5 htwbse % pwd
/Users/michalroziel/Documents/htwbse


" cd " -> change to home directory 

echo $HOME
michalroziel@MBP-michal-5 htwbse % echo $HOME
/Users/michalroziel
michalroziel@MBP-michal-5 htwbse %
```

- Als besonderes Directory → Home Directory

- Im Home Directory unmittelbar nach dem [[Login]]

  

## Was gibt es ?

```Shell
ls 

ls -l -> ausführliche variante 

ls -lR -> ausführliche variante Rekursiv 

```

  

## Root Verzeichnis

![[Untitled 3.png]]

  

  

- Belegung von verschiedener Anzahl von Bits in einem Rechner, entweder 16, 32, oder 64 Bit System

  

### Character Divises / Block divises

- Block Größe von [[Speicher]] Bits an verschiedenen Festplatten / verschiedenen Bit Systemen

  

### Wie werden CDs geschrieben ?

→ Von innen nach außen

  

- auf einer Schallplatte haben die äußeren Stücke bessere Qualität → außen läuft die Schallplatte den selben Weg viel schneller

  

```Shell
ls -l null -> Papierkorb in Unix 

ls -lR > /dev/null 

/dev /null -> Mülleimer, man kann es nicht mehr zurückholen 

	> -> lenke die Ausgabe um 


utree -> Unix Tree | tree on mac 

baobab 
```

  

![[Untitled 1.png]]

  

## Sonderverzeichnisse

```Shell
/ -> root Directory 

. -> Working Directory 
.. -> dem W.D übergeordnet 

~  (tilde) -> Abkürzung für Home Verzeichnis 

pwd 

michalroziel@MBP-michal-5 ~ % pwd
/Users/michalroziel
michalroziel@MBP-michal-5 ~ %


```

  

### Wie bewege ich mich im Baum ?

```Shell
cd -> immer ins Home Directory 

cd ~ -> H.D

cd $HOME -> H.D 

cd /export/home_23/pickpi23

cd ~pickpi23 -> H.D von pickpi23 

cd .. -> ein Verzeichnis höher 

cd . -> man bleibt im Working Directory 

cd - -> ins vorherige Working Directory 
```

  

## Manual Pages

```Shell
michalroziel@MBP-michal-5 ~ % man cd
Unknown locale, assuming C
michalroziel@MBP-michal-5 ~ % man zsh | wc -l
Unknown locale, assuming C
     392
michalroziel@MBP-michal-5 ~ % man bash | wc -l
Unknown locale, assuming C
    4908
michalroziel@MBP-michal-5 ~ % man ksh 
```

  

```Shell
apro ls 

apro ls > x-apro-ls 

cat -> catalog  

tac ls > x-apro-ls 

selbes kommando, sortiert nur umgekehrt 

stty -a 

cat ls > x-apro-ls | more 

more x-apro      -> es wird nicht alles auf einmal angezeigt 

					mit leerzeichen mehr anzeigen lassen, mit b ( back ) zurück gehen 

" tail " -> zeigt die letzten 21 Zeilen an 
```

  

```Shell
nl -> number lines aber leerzeilen nicht mitgezählt 

nl -ba -> mit leerzeilen 

michalroziel@eduroam-192-109-116-132 htwbse % nl tableCSV.csv 

     1	Username; Identifier;First name;Last name
     2	booker12;9012;Rachel;Booker
     3	grey07;2070;Laura;Grey
     4	johnson81;4081;Craig;Johnson
     5	jenkins46;9346;Mary;Jenkins
     6	smith79;5079;Jamie;Smith
      	
michalroziel@eduroam-192-109-116-132 htwbse % nl -ba  tableCSV.csv

     1	Username; Identifier;First name;Last name
     2	booker12;9012;Rachel;Booker
     3	grey07;2070;Laura;Grey
     4	johnson81;4081;Craig;Johnson
     5	jenkins46;9346;Mary;Jenkins
     6	smith79;5079;Jamie;Smith
     7	
michalroziel@eduroam-192-109-116-132 htwbse %


nl -ba  tableCSV.csv | lp -d R8203-Laser 

			-> Drucker benutzen 
```

  

  

```Shell
michalroziel@eduroam-192-109-116-132 htwbse % od -abc tableCSV.csv 



0000000    U   s   e   r   n   a   m   e   ;  sp   I   d   e   n   t   i
          125 163 145 162 156 141 155 145 073 040 111 144 145 156 164 151
           U   s   e   r   n   a   m   e   ;       I   d   e   n   t   i
0000020    f   i   e   r   ;   F   i   r   s   t  sp   n   a   m   e   ;
          146 151 145 162 073 106 151 162 163 164 040 156 141 155 145 073
           f   i   e   r   ;   F   i   r   s   t       n   a   m   e   ;
0000040    L   a   s   t  sp   n   a   m   e  nl   b   o   o   k   e   r
          114 141 163 164 040 156 141 155 145 012 142 157 157 153 145 162
           L   a   s   t       n   a   m   e  \n   b   o   o   k   e   r
0000060    1   2   ;   9   0   1   2   ;   R   a   c   h   e   l   ;   B
          061 062 073 071 060 061 062 073 122 141 143 150 145 154 073 102
           1   2   ;   9   0   1   2   ;   R   a   c   h   e   l   ;   B
0000100    o   o   k   e   r  nl   g   r   e   y   0   7   ;   2   0   7
          157 157 153 145 162 012 147 162 145 171 060 067 073 062 060 067
           o   o   k   e   r  \n   g   r   e   y   0   7   ;   2   0   7
0000120    0   ;   L   a   u   r   a   ;   G   r   e   y  nl   j   o   h
          060 073 114 141 165 162 141 073 107 162 145 171 012 152 157 150
           0   ;   L   a   u   r   a   ;   G   r   e   y  \n   j   o   h
0000140    n   s   o   n   8   1   ;   4   0   8   1   ;   C   r   a   i
          156 163 157 156 070 061 073 064 060 070 061 073 103 162 141 151
           n   s   o   n   8   1   ;   4   0   8   1   ;   C   r   a   i
0000160    g   ;   J   o   h   n   s   o   n  nl   j   e   n   k   i   n
          147 073 112 157 150 156 163 157 156 012 152 145 156 153 151 156
           g   ;   J   o   h   n   s   o   n  \n   j   e   n   k   i   n
0000200    s   4   6   ;   9   3   4   6   ;   M   a   r   y   ;   J   e
          163 064 066 073 071 063 064 066 073 115 141 162 171 073 112 145
           s   4   6   ;   9   3   4   6   ;   M   a   r   y   ;   J   e
0000220    n   k   i   n   s  nl   s   m   i   t   h   7   9   ;   5   0
          156 153 151 156 163 012 163 155 151 164 150 067 071 073 065 060
           n   k   i   n   s  \n   s   m   i   t   h   7   9   ;   5   0
0000240    7   9   ;   J   a   m   i   e   ;   S   m   i   t   h  nl  nl
          067 071 073 112 141 155 151 145 073 123 155 151 164 150 012 012
           7   9   ;   J   a   m   i   e   ;   S   m   i   t   h  \n  \n
0000260
michalroziel@eduroam-192-109-116-132 htwbse %
```

  

```Shell
echo -e "ks.rgrgd\rtgtgrhrthjtrtf\dthtfhdrg\c"
```

  

```Shell
od -t xlz x-od 

michalroziel@eduroam-192-109-116-132 htwbse % od -t x tableCSV.csv 


0000000          72657355        656d616e        6449203b        69746e65
0000020          72656966        7269463b        6e207473        3b656d61
0000040          7473614c        6d616e20        6f620a65        72656b6f
0000060          393b3231        3b323130        68636152        423b6c65
0000100          656b6f6f        72670a72        37307965        3730323b
0000120          614c3b30        3b617275        79657247        686f6a0a
0000140          6e6f736e        343b3138        3b313830        69617243
0000160          6f4a3b67        6f736e68        656a0a6e        6e696b6e
0000200          3b363473        36343339        72614d3b        654a3b79
0000220          6e696b6e        6d730a73        37687469        30353b39
0000240          4a3b3937        65696d61        696d533b        0a0a6874
0000260
michalroziel@eduroam-192-109-116-132 htwbse %
```

  

```Shell
michalroziel@eduroam-192-109-116-132 ~ % ls -a 

.			.gitconfig		.viminfo		Downloads
..			.ipython		.vpn			IdeaProjects
.CFUserTextEncoding	.jupyter		.vscode			Library
.DS_Store		.lesshst		.zprofile		Movies
.Trash			.local			.zsh_history		Music
.android		.m2			.zsh_sessions		Pictures
.anyconnect		.matplotlib		.zshrc			Public
.cache			.mono			Applications		VirtualBox VMs
.cisco			.redhat			Creative Cloud Files
.config			.ssh			Desktop
.cups			.vagrant.d		Documents
michalroziel@eduroam-192-109-116-132 ~ %

ls -A -> hier sind die Dateien mit .. dabei 




	
```

- Versteckte Dateien fangen mit einem Punkt an
    
    - Konfigurationen
    

  

- bei zeitstempel wird die Zeit bis ungefähr ein halbes Jahr in die Vergangenheit gehaltemn
