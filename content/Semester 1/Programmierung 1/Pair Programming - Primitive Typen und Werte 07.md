  

```Java
import java.util.*;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
      
      Random rand = new Random();
      
      int x = rand.nextInt(0,11);
      int y = rand.nextInt(0,11);
      
      System.out.println("value of x: " + x );
      System.out.println("value of y: " + y );
      
      int sum = x + y ;
      
      if ( sum <= 10){
        
        System.out.println(" The Sum is less than or equal to 10 !  ");
        
      }
      
      else { 
        
        System.out.println("Thes Sum is greater than 10 ! ");
        
      }
      
  }
}
```