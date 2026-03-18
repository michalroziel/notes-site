  

### Multiple Choice Questions

- 30-40% der Klausur

- entweder eins oder mehrere richtige

- man muss alles richtig ankreuzen → sonst 0 punkte

- keine minuspunkte ( Gerichtsurteil)

  

### Klausur

- 120 Minuten ?

- ein Programm entwickeln, anfangend am Niveau von _Hello World_ bis hin zu Exceptions.

- wahrscheinlich eine Rückmeldung per Email wenn man die Zulassung nicht bekommt.

### Vorbereitung

- Vor-Ort-Übungen

- Pair-Programming Tasks in der Klausur

- Aufgaben aus dem Buch

- Experience durch Codeopolis

  

### Verschiedenes - Exceptions mit dem keyword _throws_

  

```Java

public class Main {

				public static double division(int a , int b){

						if(b==0){
										throw new IllegalArgumentException("b cannot be 0 to avoid div error");

									}
								return a / b ; 

				}

	public static void main(String[] args){

					try {
							division(10,0);
						
							}

						catch(RuntimeException e {
								
										System.out.println("unchecked exception occured at RT ! " ) ;							
									//	e.printStackTrace();
									}



						catch(Exception e {
								
										System.out.println("echecked exception ocurred at RT " ) ;							
										e.printStackTrace();
									}

		
					}


}
```

```Java
public class DivisionException extends Exception{


}

public class DivisionException1 extends RuntimeException{


}

```

  

> [!important] Arten von Exceptions — checked vs. unchecked exceptions

> [!important] Runtime vs not Runtime exceptions

- Wissen das eine IllegalArgumentExpetion eine RuntimeEXception

- IOException, etc.