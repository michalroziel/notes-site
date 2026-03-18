  

### Changed City Class :

- City Klasse Konstruktor :

```Java
this.depot = new Depot(1500,5,5);         //TODO: this.depot = new Depot(pDepot);

public boolean expand(int space){
        double tempPZ = space * this.expandCost;
        if (tempPZ <= 100.0) {
            this.depot.takeOut((int)(this.depot.getFillLevel("")*(tempPZ/100)),"");
            this.depot.expand(space, 5 ,5 ); //TODO: changed expand method 
            return true;
        }
        return false;
    }
```

  

  

### check again

- return pAmount in remove in Harvest