[[ARM7]]
## Größtes Element im Array Finden 

```
	AREA MyCode, CODE, READONLY   ; Definiere den Codebereich
    EXPORT _start                  ; Exportiere _start als Einstiegspunkt

_start
    LDR R2, =myArray               ; Lade die Adresse von myArray in R2
    LDR R3, =Anzahl                ; Lade die Adresse von Anzahl
    LDRH R0, [R3]                  ; Lade die Anzahl der Elemente in R0 (Wert von Anzahl)

    MOV R1, #0                     ; Setze R1 auf 0, um den größten Wert zu finden

loop
    LDR R3, [R2], #4               ; Lade einen 32-Bit-Wert von [R2] und inkrementiere R2 um 4
    CMP R3, R1                      ; Vergleiche R3 mit R1
    MOVGT R1, R3                    ; Wenn R3 > R1, setze R1 auf R3
    SUBS R0, R0, #1                 ; Subtrahiere 1 von R0 (Anzahl der verbleibenden Elemente)
    BNE loop                        ; Wenn noch Elemente übrig sind, springe zurück zu "loop"

    MOV R0, R1                      ; Setze R0 auf den größten Wert
    BX LR                           ; Rücksprung zum Link-Register

    AREA MyData, DATA, READONLY    ; Definiere den Datensektor
myArray  DCD 0x67, 0x79, 0x15, 0xE3, 0x72  ; Beispielarray mit 32-Bit-Werten
Anzahl   DCW 5                      ; Anzahl der Elemente im Array
    END

```


