  

  

## 1. Accumulate Data :

- Pressure Sensor instead of UltraSonic

- Humidity Sensor

- Actuator Rain Water Pipe

- ESP32 MicroController

## 2. Share Data :

- ESP32 sends Data to home DataBase

- Possibly over WiFI or [[LoRaWAN]] → `THE THINGS NETWORK`

## 3. Process Data :

- Water Level Warning

- If Humidity Low → Water Garden

- If Tank is full → Close Rain Water Pipe

- Converts measured pressure into fill level

## 4. Analyze Data :

- Visualize Rainfall periods using External weather data + our measurements

- Grafana for visualization

  

> [!important]
> 
> DO NOT Analyze Data on Site, first Transfer, → Stay Modular