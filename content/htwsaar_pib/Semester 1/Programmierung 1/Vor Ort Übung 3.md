  

```Java
public class Main {
    public static void main(String[] args) {
      

      Car myCar = new Car("VW", "Golf", "White", 235); 
      
      ElectricCar myElectricCar = new ElectricCar( "Audi", "80");
      
        System.out.println(myCar);
        System.out.println(myElectricCar);
        
        
      }
      
      
      
      
      
      
      
      
  }



```

  

  

```Java

public class Car {

        String brand;
        String model;
        String color;
        int maxSpeed;
      
      public Car(String pBrand, String pModel, String pColor, int pMaxSpeed){
        
        this.brand = pBrand;
        this.model = pModel;
        this.color = pColor;
        this.maxSpeed = pMaxSpeed;

}
    public Car(){}
    public Car(String pBrand, String pModel ){
    this.brand = pBrand;
    this.model = pModel;
    this.color = "black";
    this.maxSpeed = 130;
    
      }
    

public String toString(){
  
 return " the car:" + " " + this.brand + " " + this.model + " " + this.color +  " " + "with Vmax : " + this.maxSpeed;
} 

}
```

  

  

```Java
public class ElectricCar extends Car {

private int batteryCapacity ;

public ElectricCar(String pBrand, String pModel, String pColor, 
int pMaxSpeed, int pBatteryCapacity){
  
  super(pBrand, pModel, pColor, pMaxSpeed);
  this.batteryCapacity = pBatteryCapacity ;
  
  }
  
  public ElectricCar( String pBrand, String pModel ){
    
    this.brand = pBrand;
    this.model = pModel;
    this.color = "White";
    this.maxSpeed = 100;
    this.batteryCapacity = 60;
  }


}
```