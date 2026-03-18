  

## Kapitel 2

Dinge die ein objekt über sich weiß heißen Instanzvariablen

  

  

# Types

```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
      
      
      int i = 14;
      double d = 13.8;
      
      System.out.println(i/d < 1);   // false 

			System.out.println( i - (i/3)*3 ); // 2 

			
	
      
      
  }
}
```

  

  

```Java
public class FormattingExample {
    public static void main(String[] args) {
        String name = "John";
        int age = 30;
        double salary = 2500.50;

        // Using %s for string, %d for integer, and %,.2f for floating point with thousand separators and 2 decimal places
        System.out.printf("Name: %s, Age: %d, Salary: $%,.2f\n", name, age, salary);
    }
}
```

  

  

public [[class]] Main{

public [[Static]] void main(String[] args){

System.out.println( isPalindrome( "H ! A?N ? . NA.!H") ) ;

}

```Plain
  public static boolean isPalindrome(String a ){


    String cleanedStr = a.replaceAll("[^a-zA-Z0-9]", "");


    String myString = cleanedStr;

  for (int i = 0; i < myString.length(); i++){

    if(myString.charAt(i) != myString.charAt(myString.length() - 1 - i) ){

      return false ;

    }

  }

  return true ;

}
```

}