  

## 1. Weiß, mit welcher Console jede Linux-VM gestartet wird

- bash, zsh, ksh

- SPICE Konsole

  

## 2. Wie speichert man einen Sychronisationsordner im STL Datenspeicher ?

  

  

## 4. habe mein Shellfenster so konfiguriert, dass es als sogenannte "Login-Shell" startet

```Shell
sudo chsh -s
```

  

> [!important] sudo → super user do

> [!important] chsh → change shell

  

### öffnen von absoluten pfad

```Shell
pwd 
```

  

## 5. Weiß, woran ich erkennen kann, dass eine Shell als "Login-  
Shell" läuft

```Shell
michal@mlatitude:~$ echo $SHLVL
1
michal@mlatitude:~$

1 -> Login Shell 
```

  

## 7. Was ist Whitespaces?

- Zeilenumbruch, Leertaste, leerer char

## 8. Der Begriff “Token”

- Kommandos, welche durch Whitespaces abgetrennt werden

  

## 9. Kann den syntaktischen Aufbau eines Linux Kommandos Aufbauen

- Kommandoname → Options

```Shell
Kommando [ [ option [w] [qualifier] ] ... [w] [filen_name ...]
				/ -option 
			/- — option 

[qualifier] beeinflusst die Option 
```

  

## 10. Weiß, wie ich die ANzahl der Zeichen Prüfe

```Shell
wc -> word count 
wc [filename]
```

  

## 11. weiß, in welchen Abschnitten (sections) der Handbuchseiten (manual pages) das Kommando time beschrieben wird und  
wozu man es verwenden kann

```Shell
man time -> Section Name , Synopsis , Description
```

  

## In Welcher Shell befinde ich mich ?

```Shell
michal@mlatitude:~/Documents/htwprog/ValMicCar$ echo $0
bash
```

  

## 12. Weiß, wie ich mir die Zeit anzeigen lassen kann, die eine Shell für die Ausführung des Kommandos von Nr.10 braucht

  

```Shell
pom.xml  README.md  src  target  text.txt
michal@mlatitude:~/Documents/htwprog/ValMicCar$ time wc README.md 
 0  2 11 README.md

real	0m0.002s
user	0m0.000s
sys	0m0.002s
```