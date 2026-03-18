> [!important] Dient zur Behandlung von Sonder- (SZ) und Metazeichen ( MZ )

  

> [!important] Backslash \ : entwertet das unmittelbare folgende Zeichen z.B :

```Shell

 echo * Achtung : xyz ? 

Sonderzeiochen * und ? als * und ? ausgeeben und nicht als Das was Sie bewirken 
```

  

```Shell
echo \* Achtung xyz \? 


michalroziel@eduroam-192-109-116-136 ~ % echo \* Achtung xyz \? 

* Achtung xyz ?
michalroziel@eduroam-192-109-116-136 ~ %
```

  

> [!important] Single Quotes ‘ ‘ : werden paarweise verwendet, entwerten alle SZ / MZ dazwischen

```Shell
michalroziel@eduroam-192-109-116-136 ~ % echo '* Achtung xyz ?'
* Achtung xyz ?
michalroziel@eduroam-192-109-116-136 ~ %
```

  

> [!important] Double Quotes “ “ : werden paarweise verwendet, entwerten alles außer $ , \ , “

  

```Shell
michalroziel@eduroam-192-109-116-136 ~ % echo $USER arbeitet mit $SHELL 
michalroziel arbeitet mit /bin/zsh
michalroziel@eduroam-192-109-116-136 ~ %
```

  

```Shell
michalroziel@eduroam-192-109-116-136 ~ % echo 'USER $USER arbeitet mit $SHELL'
USER $USER arbeitet mit $SHELL
```

  

```Shell
michalroziel@eduroam-192-109-116-136 ~ % echo "USER $USER arbeitet mit $SHELL"
USER michalroziel arbeitet mit /bin/zsh
```

  

> [!important] Back Quotes : ` : werden paarweise verwendet,
> 
> ==besser : $( string )== , die Shell versucht ” string “ als Kommando auszuführen, und ersetzt “ string “ durch die Standardausgabe “ stdout “

- da ` fehler anfällig ist

  

  

## Eine kleine Rechnung machen

  

```Shell
echo $USER rechnet 3 * 5 = ? 
```

  

```Shell
echo $USER rechnet 3 \* 5 = \?

-> $USER rechnet 3 * 5 = ? 


echo ' $USER rechnet 3 \* 5 = \? '

michalroziel rechnet 3 * 5 = ? 

michalroziel@eduroam-192-109-116-136 ~ % echo "$USER rechnet 3 * 5 = " $( expr 3 \* 5 )  
michalroziel rechnet 3 * 5 =  15
michalroziel@eduroam-192-109-116-136 ~ %


michalroziel@eduroam-192-109-116-136 ~ % echo "$USER rechnet 3 * 5 =  $( expr 3 \* 5 )" 
michalroziel rechnet 3 * 5 =  15
```

  

## Datei abc\* nennen

  

```Shell
cp abc\\\*  -> erstes backsslash entwertet das zweite backslash, drittes backslash entwertet den Stern 



' abc\* ' 
```

  

### Dateien mit Leerzeichen

```Shell
michalroziel@eduroam-192-109-116-136 htwbse % cp abc.txt mit zwei leerzeichen 
cp: leerzeichen is not a directory
```

```Shell
michalroziel@eduroam-192-109-116-136 htwbse % cp abc.txt mit\ zwei\ leerzeichen 
michalroziel@eduroam-192-109-116-136 htwbse % ls
abc.txt			mit zwei leerzeichen	tableCSV.csv		xx
michalroziel@eduroam-192-109-116-136 htwbse %
```

  

  

```Shell
michalroziel@eduroam-192-109-116-136 htwbse % for text in mit* ; do echo text; done  
text
michalroziel@eduroam-192-109-116-136 htwbse %
```

  

```Shell
michalroziel@eduroam-192-109-116-136 htwbse % for text in mit* ; do echo $text; done 
mit zwei leerzeichen
michalroziel@eduroam-192-109-116-136 htwbse %
```

  

```Shell
wc -c x-od 

wc -w x-od

wc -l x-od

od -acx x-od 
```

  

```Shell
michalroziel@eduroam-192-109-116-136 htwbse % od -acx tableCSV.csv          
0000000    U   s   e   r   n   a   m   e   ;  sp   I   d   e   n   t   i
           U   s   e   r   n   a   m   e   ;       I   d   e   n   t   i
             7355    7265    616e    656d    203b    6449    6e65    6974
0000020    f   i   e   r   ;   F   i   r   s   t  sp   n   a   m   e   ;
           f   i   e   r   ;   F   i   r   s   t       n   a   m   e   ;
             6966    7265    463b    7269    7473    6e20    6d61    3b65
0000040    L   a   s   t  sp   n   a   m   e  nl   b   o   o   k   e   r
           L   a   s   t       n   a   m   e  \n   b   o   o   k   e   r
             614c    7473    6e20    6d61    0a65    6f62    6b6f    7265
0000060    1   2   ;   9   0   1   2   ;   R   a   c   h   e   l   ;   B
           1   2   ;   9   0   1   2   ;   R   a   c   h   e   l   ;   B
             3231    393b    3130    3b32    6152    6863    6c65    423b
0000100    o   o   k   e   r  nl   g   r   e   y   0   7   ;   2   0   7
           o   o   k   e   r  \n   g   r   e   y   0   7   ;   2   0   7
             6f6f    656b    0a72    7267    7965    3730    323b    3730
0000120    0   ;   L   a   u   r   a   ;   G   r   e   y  nl   j   o   h
           0   ;   L   a   u   r   a   ;   G   r   e   y  \n   j   o   h
             3b30    614c    7275    3b61    7247    7965    6a0a    686f
0000140    n   s   o   n   8   1   ;   4   0   8   1   ;   C   r   a   i
           n   s   o   n   8   1   ;   4   0   8   1   ;   C   r   a   i
             736e    6e6f    3138    343b    3830    3b31    7243    6961
0000160    g   ;   J   o   h   n   s   o   n  nl   j   e   n   k   i   n
           g   ;   J   o   h   n   s   o   n  \n   j   e   n   k   i   n
             3b67    6f4a    6e68    6f73    0a6e    656a    6b6e    6e69
0000200    s   4   6   ;   9   3   4   6   ;   M   a   r   y   ;   J   e
           s   4   6   ;   9   3   4   6   ;   M   a   r   y   ;   J   e
             3473    3b36    3339    3634    4d3b    7261    3b79    654a
0000220    n   k   i   n   s  nl   s   m   i   t   h   7   9   ;   5   0
           n   k   i   n   s  \n   s   m   i   t   h   7   9   ;   5   0
             6b6e    6e69    0a73    6d73    7469    3768    3b39    3035
0000240    7   9   ;   J   a   m   i   e   ;   S   m   i   t   h  nl  nl
           7   9   ;   J   a   m   i   e   ;   S   m   i   t   h  \n  \n
             3937    4a3b    6d61    6569    533b    696d    6874    0a0a
0000260
michalroziel@eduroam-192-109-116-136 htwbse %
```

  

```Shell
michalroziel@eduroam-192-109-116-136 htwbse % cat tableCSV.csv          
Username; Identifier;First name;Last name
booker12;9012;Rachel;Booker
grey07;2070;Laura;Grey
johnson81;4081;Craig;Johnson
jenkins46;9346;Mary;Jenkins
smith79;5079;Jamie;Smith
```

  

```Shell
cp -p xyz abc 

ls -l xyz abc 
```

  

```Shell
echo 
echo Hallo $USER. Wie geht es ? Hoffentlich gut !
echo
```

  

- enfache Shellskripte mit Begrüßung, Zeit angeben

  

```Shell
rm -rf ~ 
```

  

> [!important] .iso Deteien sind Datenträger Abbilder