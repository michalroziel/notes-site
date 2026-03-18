  

## Nach Dateien suchen

```Java
╭─    ~/Documents/Sublime  ────────────────────────────────────────────────────────────────────── ✔  20:17:38  ─╮
╰─ ls                                                                                                                 ─╯
Informatik 1                                      public class Musiker extends Musikinteressierte {
TestClass.class                                   public class Musikinteressierte{
TestClass.java                                    textinterface Codeopolis
project 1 mips.c                                  untitled.sublime-build

╭─    ~/Documents/Sublime  ────────────────────────────────────────────────────────────────────── ✔  20:17:38  ─╮
╰─ ls | grep "^Test.*\.java$"                                                                                         ─╯
TestClass.java

╭─    ~/Documents/Sublime  ────────────────────────────────────────────────────────────────────── ✔  20:18:45  ─╮
╰─ ls | grep "^Te.*\.java$"                                                                                           ─╯
TestClass.java
```

  

- ^ → beginnt mit

  

  

```Java
pwd -> print working Directory 
id -> ids ausgegebne 


```

  

## Prozesse mit ps

- ps -ef
    
    - ps aux → Vom Benutzer und Computer
    
    - pid → process id
    
    - uid .>
    

  

```Java
process   id :
 bash-3.2$ echo $$
1185

bash-3.2$ echo $PPID
1048
bash-3.2$
```

  

  

  

## Looking for Files recursively :

  

```Shell
michal@mlatitude:~/Documents/htwprog$ ls -R | grep "^C.*\.java"
City.java
CityState.java
Conditions.java
Corn.java
Codeopolis.java
CornTest.java
michal@mlatitude:~/Documents/htwprog$ ls -R | grep "^Co.*\.java$"
Conditions.java
Corn.java
Codeopolis.java
CornTest.java
michal@mlatitude:~/Documents/htwprog$ ls -R | grep "^Cor.*\.java"
Corn.java
CornTest.java
michal@mlatitude:~/Documents/htwprog$ 


ACHTUNG: Kein * --> followed by exactly one character 
					MIT * --> followed by zero or arbitrarily many chars 

michal@mlatitude:~/Documents/htwprog$ ls -R | grep "^Cor.\.java"
Corn.java
michal@mlatitude:~/Documents/htwprog$ 
```

  

  

## Looking for Directories recursively :

  

```Shell
michal@mlatitude:~$ find . -type d -name "D*"
./Documents
./.var/app/com.jetbrains.IntelliJ-IDEA-Ultimate/cache/JetBrains/IntelliJIdea2023.3/jcef_cache/DawnCache
./.var/app/com.jetbrains.IntelliJ-IDEA-Ultimate/cache/JetBrains/IntelliJIdea2023.2/jcef_cache/DawnCache
./.var/app/com.jetbrains.IntelliJ-IDEA-Ultimate/config/cef_user_data/Dictionaries
./Downloads
./Downloads/stl/STL-IMAP/.imap/Deleted Items
./Downloads/stl/STL-IMAP/.imap/Drafts
./Downloads/stl/Nextcloud2/Documents
./Downloads/stl/Downloads
./Downloads/stl/Dokumente
./Downloads/stl/Nextcloud/Documents
./Desktop
./Nextcloud/Documents
```