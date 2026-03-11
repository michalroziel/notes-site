 
## Wie viele UART-Schnittstellen hat der MP ?
- 2

Wie berechnet man die Baudrate? 

- Frequenzteiler  ( Divisor ) = P-Clock / (16 * Baudrate)

- Baudrate = P-Clock / 16  * Divisor 

## Welche Baudraten sind üblich? 
- 110
- 300
- 600
- 1200
- 2400
- 4800
- 9600
- 19200
- 38400
-  57600 
- 115200

## Wie viele Stoppbits kann der MP haben? 
- 1  - Standard, hohe Effizienz 
- 1.5 - üblich bei 5 Bits 
- 2   - Bessere Sicherheit und Fehlererkennung 

## Kann der MP Paritätsprüfung betreiben und wenn ja welche? 
- Ja !
	- Gerade
	- Ungerade
	- Markierung
	- Leerzeichen

## Welche Register werden benutzt um die UART-Schnittstellen zu programmieren? 

	U1THR Transmit Holding -Register (Senden) 0xE0010010

	U1RBR Receive Buffer -Register (Empfangen) 0xE0010000

	U1LSR Line Status -Register (Status prüfen) 0xE0010014

	U1LCR Line Control -Register (Konfiguration) 0xE001000C

	U1DLL Divisor Latch LSB - (Baudrate einstellen) 0xE0010000

	U1DLM Divisor Latch MSB - (Baudrate einstellen) 0xE0010004

	U1FCR FIFO Control Register - (Puffersteuerung) 0xE0010008

	U1IER Interrupt Enable Register -  (Interrupts) 0xE0010004

## In welchem Register wird angezeigt, ob ein Character empfangen wurde? 

	Das relevante Register ist das U1LSR (Line Status Register).

	• Adresse für UART1: 0xE0010014

	• Adresse für UART0: 0xE000C014

## Welche Anschlüsse (Pins in GPIO0 und 1) 

**UART** **Funktion** **Pin** **Port** **Pin-Nummer**

UART0 TxD (Senden) P0.0 GPIO0 Pin 0

UART0 RxD (Empfangen) P0.1 GPIO0 Pin 1michu


UART1 TxD (Senden) P0.8 GPIO0 Pin 8

UART1 RxD (Empfangen) P0.9 GPIO0 Pin 9

• **TxD** = Übertragungsleitung (Transmit Data)

• **RxD** = Empfangsleitung (Receive Data)

## In welchen Registern wird der Frequenzteiler gespeichert? 

Der **Frequenzteiler** für die UART-Baudrate wird im LPC21xx-Mikrocontroller in den folgenden **Divisor Latch Registers** gespeichert:

1. U0DLL **/** U1DLL **(Divisor Latch LSB - Low Byte)**

2. U0DLM **/** U1DLM **(Divisor Latch MSB - High Byte)**

Der **Divisor** wird in zwei 8-Bit-Register aufgeteilt:

• **Lower Byte (LSB)** → Register DLL

• **Upper Byte (MSB)** → Register DLM

  

**Beispiel:**

Wenn der berechnete Divisor 40 beträgt (dezimal):

• **Low Byte (LSB):** 40 % 256 = 40 → Wert in U1DLL

• **High Byte (MSB):** 40 / 256 = 0 → Wert in U1DLM


## Wozu wird PINSELx gebraucht?
Die **PINSELx-Register** werden verwendet, um:

• **Einen Pin für eine bestimmte Peripherie-Funktion zu konfigurieren.**

Beispiel: Ein Pin kann als GPIO, UART Tx, PWM oder SPI genutzt werden.

Jedes Pin in **Port 0 und Port 1** kann durch **2 Bits** im entsprechenden PINSEL-Register konfiguriert werden.

*Bits** **Funktion**
00 GPIO (Standard)
01 Alternative Funktion 1
10 Alternative Funktion 2
11 Alternative Funktion 3



## Wieviele bits kann ein wort haben ?
- Wortgröße : 32 Bits, 4 Bytes 

## Welches Bit wird zuerst gesendet ?

Die Reihenfolge der Übertragung eines 8-Bit-Datenpakets (z.B. 0b10110011) ist:
**MSB (Bit 7)** **Bit 6** **Bit 5** **Bit 4** **Bit 3** **Bit 2** **Bit 1** **LSB (Bit 0)**

	1 0 1 1 0 0 1 1

## Auf welchem GPIO port ist UART ? 

**UART-Pinzuordnung auf GPIO-Ports:**
**UART** **Funktion** **GPIO-Port** **Pin** **Alternative Funktion** **PINSEL-Register**

UART0 TxD0 GPIO0 P0.0 UART0 Senden PINSEL0 (Bits 1:0)

UART0 RxD0 GPIO0 P0.1 UART0 Empfangen PINSEL0 (Bits 3:2)

UART1 TxD1 GPIO0 P0.8 UART1 Senden PINSEL0 (Bits 17:16)

UART1 RxD1 GPIO0 P0.9 UART1 Empfangen PINSEL0 (Bits 19:18)

## Welche register steuern UART ?
	a) UxDLL UxTHR etc. (✅ Richtig)
	b) TxMCR TxTCR 
	c) R0, R1, R2 
	d) EXTINT EXTPOLAR 



## In welchen registern wird die baudrate gespeichert ? 

Die Baudrate wird in den Registern UxDLL und UxDLM gespeichert.

1. UxDLL **(Divisor Latch LSB – Low Byte)**

• Speichert das **niedrigere Byte** des Baudratenteilers.

• Adresse für UART0: 0xE000C000, für UART1: 0xE0010000

2. UxDLM **(Divisor Latch MSB – High Byte)**

• Speichert das **höhere Byte** des Baudratenteilers.

• Adresse für UART0: 0xE000C004, für UART1: 0xE0010004


	# Questions :

1. Formel für BAUDRATE angeben : PCLOCK / (16 * Divisor)
2. Welche Stopp bits kann man einstellen ? : 1 , 2
3. Welches Register wird zum senden verwendet ? : UxTHR
4. Welches Reg zur Einstellung der UART ? : PINSELx, UxDLM, UxDLL, UxLCR, UxFCR, UxERR UxIER (x = 0 oder 1 )
5. Welches Bit wird zuerst gesendet ? : Least Significant Bit ( LSB )
6. Welches Register wird zum speichern des Frequenz teilers verwendet ? : U0DLL, U1DLM, U1DLL und/- oder U1DLM
7. Was ist PINSELx ? : SteuerRegister zum Konfiguration von der UART
