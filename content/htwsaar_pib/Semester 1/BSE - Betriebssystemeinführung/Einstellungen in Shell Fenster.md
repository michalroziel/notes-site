## Aufbau von Kommandos

- Die Unix - Kommandos haben eine eindeutige Syntax ( mit vielen Ausnahmen )

- Die Kommandos bestehen aus „ Tokens“ getrennt durch Whitespace → Leerzeichen / Tab
    
    - zeichen die wir nicht sehen, aber da sind
    
      
    

### IFS

- Shell Variable → enthält den aktuell definierten Whitespace

> [!important] IFS →
> 
> ==I==nternal ==F==ile ==S==eperator

```Shell
echo "$IFS" 

```

- echo gibt den inhalt der variable wieder

```Shell
echo "$IFS" | od -abc


0000000   sp  ht  nl nul  nl                                            
          040 011 012 000 012                                            
              \t  \n  \0  \n                                            
0000005
```

→ schaut nach was geliefert wird und gibt uns die information in bits oder bytes wieder

- sp → space nl → new line

  

### Ascii

```Shell
man ascii 
```

```Shell
ASCII(7)               Miscellaneous Information Manual               ASCII(7)

NAME
     ascii – octal, hexadecimal and decimal ASCII character sets

DESCRIPTION
     The octal set:

     000 nul  001 soh  002 stx  003 etx  004 eot  005 enq  006 ack  007 bel
     010 bs   011 ht   012 nl   013 vt   014 np   015 cr   016 so   017 si
     020 dle  021 dc1  022 dc2  023 dc3  024 dc4  025 nak  026 syn  027 etb
     030 can  031 em   032 sub  033 esc  034 fs   035 gs   036 rs   037 us
     040 sp   041  !   042  "   043  #   044  $   045  %   046  &   047  '
     050  (   051  )   052  *   053  +   054  ,   055  -   056  .   057  /
     060  0   061  1   062  2   063  3   064  4   065  5   066  6   067  7
     070  8   071  9   072  :   073  ;   074  <   075  =   076  >   077  ?
     100  @   101  A   102  B   103  C   104  D   105  E   106  F   107  G
     110  H   111  I   112  J   113  K   114  L   115  M   116  N   117  O
     120  P   121  Q   122  R   123  S   124  T   125  U   126  V   127  W
     130  X   131  Y   132  Z   133  [   134  \   135  ]   136  ^   137  _
     140  `   141  a   142  b   143  c   144  d   145  e   146  f   147  g
     150  h   151  i   152  j   153  k   154  l   155  m   156  n   157  o
     160  p   161  q   162  r   163  s   164  t   165  u   166  v   167  w
     170  x   171  y   172  z   173  {   174  |   175  }   176  ~   177 del

     The decimal set:

       0 nul    1 soh    2 stx    3 etx    4 eot    5 enq    6 ack    7 bel
       8 bs     9 ht    10 nl    11 vt    12 np    13 cr    14 so    15 si
      16 dle   17 dc1   18 dc2   19 dc3   20 dc4   21 nak   22 syn   23 etb
      24 can   25 em    26 sub   27 esc   28 fs    29 gs    30 rs    31 us
      32 sp    33  !    34  "    35  #    36  $    37  %    38  &    39  '
      40  (    41  )    42  *    43  +    44  ,    45  -    46  .    47  /
      48  0    49  1    50  2    51  3    52  4    53  5    54  6    55  7
      56  8    57  9    58  :    59  ;    60  <    61  =    62  >    63  ?
      64  @    65  A    66  B    67  C    68  D    69  E    70  F    71  G
      72  H    73  I    74  J    75  K    76  L    77  M    78  N    79  O
      80  P    81  Q    82  R    83  S    84  T    85  U    86  V    87  W
      88  X    89  Y    90  Z    91  [    92  \    93  ]    94  ^    95  _
      96  `    97  a    98  b    99  c   100  d   101  e   102  f   103  g
     104  h   105  i   106  j   107  k   108  l   109  m   110  n   111  o
     112  p   113  q   114  r   115  s   116  t   117  u   118  v   119  w
     120  x   121  y   122  z   123  {   124  |   125  }   126  ~   127 del

FILES
     /usr/share/misc/ascii

HISTORY
     An ascii manual page appeared in Version 7 AT&T UNIX.

macOS 14.0                       June 5, 1993                       macOS 14.0
(END)
```

  

- liefert manual für ascii Zeichen

  

## Zeichensatz ansehen → man ascii

  

- zum Beispiel ;

```Shell
echo "$IFS" | od -abc
						
							od -t x1 
```

  

- Groß / Kleinbuchstaben werden unterschieden → CASE SENSITIVE

- z.B : LS → command not found
    
    - deshalb : ls
    

  

## Syntax von Kommandos

  

```Shell
Kommando [ [ option [w] [qualifier] ] ... [w] [filen_name ...]
				/ -option 
			/- — option 

[qualifier] beeinflusst die Option 
```

- Kommando : oft igendwie klare Abkürzung der Funktion

  

- z.B wc → ==w==ord ==[[C]]==ount

- cp → ==[[C]]==o==p==y

- tar → ==ta==pe ==ar==chive

- t → [[table of contents]] leffiurei

- d → destination

  

- option : beginnen mit [ ] , [ - ] , [ - - ]
    
    - dies beeinflusst die Arbeitsweise
    
    - Reihenfolge mehrerer optionen ist nciht von Bedeutung
    

```Shell
wc -l -c | wc -c -l | wc -lc | wc -cl 
```

- filename : relativer / absoluter Pfadname [[Files]]

  

## Beispiele

```Shell
tar tvf ooo.tar 
tar -t -v -f ooo.tar
tar - - list - - verbose - - file ooo.tar 
```

- Bei WIndows gibt es .zip archiv, bei unix .tar

  

```Shell
lp -d R8209-Laser ooo.tar 
```

  

# Linux auf einem Blatt → Blatt anschauen

  

## Manual pages

  

- man ls

- apropos drucken | apropos print