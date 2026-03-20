
## An welche Pins kann man externe Interrupts anschließen?
	- Mit PINSEL umschalten ergibt folgende Liste: 
		- EINT0 -> P0.1 | P0.16 
		- EINT1 -> P0.3 | P0.14
		- EINT2 -> P0.7 | P0.15 
		- EINT3 -> P0.9 | P0.20 | P0.30 

## Wie viele Externe Interrupts kann man an den Mikroprozessor anschließen?
Man kann 4 anschließen  : EINT0, EINT1, EINT2, EINT3

## welche pins können als ExtInt eingestellt werden? 
 - Einzelne pins auf Port 0 und 1 

## An welchem Register kann man einstellen, ob der Interrupt pegelgesteuert oder flankengesteuert anschlagen soll?

    EXTMODE (flanken- oder pegelgesteuert)
    EXTPOLAR (steigende oder fallende Flanke bzw. High-/Low-Pegel)​

## Welche Register braucht man, um externe Interrupts zu initialisieren?

    PINSEL (zum Umschalten der Pin-Funktionen)
    EXTMODE (Flanken-/Pegelsteuerung)
    EXTPOLAR (Flankenrichtung/Pegel)
    EXTINT (zum Quittieren des Interrupts)
    VICIntEnable (um den Interrupt zu aktivieren)
    VICVectCntl & VICVectAddr (für die vektorisierte Interruptverarbeitung)​

## Mit welchem Register schaltet man die Pin-Funktionen um?

    PINSEL0, PINSEL1, PINSEL2​

## Mit welchen Registern initialisiert man den Vektor-Interrupt-Controller (VIC)?

    VICIntEnable (Interrupt erlauben)
    VICIntSelect (IRQ oder FIQ wählen)
    VICVectCntlX (Priorität setzen)
    VICVectAddrX (ISR-Adresse setzen)​

## Wo im Code kann man ISRs hinschreiben?

    Interrupt-Service-Routinen (ISR) müssen als void ISR(void) __irq deklariert werden​

## Warum gibt es das Paritätsbit?

    Zur Fehlererkennung bei der seriellen Übertragung​

## Wie viele Bits können die Datenworte des Mikroprozessors haben?

    Der Prozessor arbeitet mit 32-Bit​

    
## Welche Register benötigt man, um den Timer zu initialisieren?

    TxPR (Prescaler)
    TxTCR (Start/Stop/Reset)
    TxMCR (Match-Funktion)
    TxMR0-TxMR3 (Match-Register)
    TxEMR (Match-Ausgabe)
    TxCCR (Capture-Steuerung)
    TxIR (Interrupt-Quittierung)​



## Wie lautet die Baudrate Formel ? 

    Baudrate-Formel:
        Frequenzteiler = P-Clock / (16 * Baudrate)
        Dann:
            UxDLL = Frequenzteiler % 256 (Low-Byte)
            UxDLM = Frequenzteiler / 256 (High-Byte)​
            
## Welche Register für UART?

    PINSEL0/PINSEL1 (Pin-Funktion)
    UxLCR (Datenbits, Stopbits, Parität)
    UxDLL, UxDLM (Baudrate)
    UxIER (Interrupts aktivieren)
    UxLSR (Status)
    UxTHR (Senden)
    UxRBR (Empfangen)
    UxFCR (FIFO-Steuerung)​

## Welche Register zum Senden in UART?

    UxTHR (Transmit Holding Register)​

## Welche Arten von Interrupts gibt es?

    Spannungspegelabhängig: LOW oder HIGH aktiv
    Flankenabhängig: Steigende oder fallende Flanke​

## Womit schaltet man die Pin-Funktionen um?

    PINSEL0, PINSEL1, PINSEL2




 Wozu wird der Prescaler verwendet ? -> Herunterteilen des **Peripherie** Taktes 
 
 Baudrate Formel 
 
Wo kann die isr im Programmspeicher stehen ? -> Kann frei im Programmspeicehr stehen, adresse muss aber im Register gespeichert werden 

Welche gängige Baudraten gibt es ? -> 300 ,600,....4800, 9600, 19200

2 Fragen zu IODIR : 
	Was es macht -> Pins als Input / Output deklarieren 
		und wie kann man Output an Pin 0.1 einstellen 

Wie können Interrupts eingestellt werden ? -> Flankengesteuert , 

Wie kann mein eine steigende Flanke eines Interrupts einstellen -> 	EXTMODE & EXTPOLAR 

In welches Register des Vector-Interrupt-Controlers beinhaltet die Startadresse der Inerrupt-Service Routine vom Kanal 5? ->VicVectAddr5


