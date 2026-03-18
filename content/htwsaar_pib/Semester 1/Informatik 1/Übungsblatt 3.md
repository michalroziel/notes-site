  

## Afgabe 1 :

  

  

  

## Aufgabe 3 - _reverse_ :

```Java
public static void main(String args[]){



	int[] a = new int[]{1, 2, 3, 4, 5};



System.out.println(" the array BEFORE reversal :  " ) ;

			for (int num  : a ) {

				System.out.print( num + " ") ; 
				
			}



			InfoSheet1.reverse(a);

			System.out.println(" " ) ;
			System.out.println(" " ) ;


System.out.println(" the aray AFTER reversal :  " ) ;

			for (int num  : a ) {

				System.out.print( num + " " ) ; 
				
			}



}



public static  int[] reverse (int[] a ){

 		  for (int i = 0 ; i < a.length  / 2  ; i++ ) {
 		
 			int copy_left = a[i] ; 

 			int copy_right = a[a.length - (i+1) ] ;

 			a[i] = copy_right ; 

 			a[a.length -  (i+1)] = copy_left ; 
    	}

    	return a ;

	}
```

  

  

## Aufgabe 4 - absence in $n$

  

```Java
public static void main(String args[]){


int[] c = new int[]{1,5,2,3} ; 


	for ( int loop  : c ) {
		
		System.out.print(" " + loop) ; 

	}


 	System.out.println("   " ) ;
 	System.out.println("   " ) ;

	InfoSheet1.absence(c) ; 


	System.out.println("   " ) ;
 	System.out.println("   " ) ;

	InfoSheet1.absence2(c) ; 



	}

```