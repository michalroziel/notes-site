[[Semester 4]]


## Code snippets : 

```Javascript 
const center = board.create('point', [0, 0], { name: 'Center' });  
const pointOnCircle = board.create('point', [3, 0], { name: 'Radius Point' });  
  
board.create('circle', [center, pointOnCircle], { strokeColor: 'blue' });

```


## Dynamic Projecting of Compass Labels 
```JavaScript

const compassLabels = [  
    { label: 'N', azimuth: 0 },  
    { label: 'E', azimuth: 90 },  
    { label: 'S', azimuth: 180 },  
    { label: 'W', azimuth: 270 }  
];


for (const dir of compassLabels) {  
    const { x, y } = convertCoordination({ azimuth: dir.azimuth, altitude: 0 }); // Altitude 0 = horizon  
    const r = 1.3;  
    board.create('text', [x * r, y * r, dir.label], {  
        fontSize: 18,  
        cssStyle: 'font-weight: bold;',  
        anchorX: 'middle',  
        anchorY: 'middle'  
    });  
}
```



```JavaScript

// Create points on the circle
for (const data of sampleDaten) {
    const {x, y} = convertCoordination({azimuth: data[0], altitude: data[1]});
    
    // Create point without a label
    const point = board.create('point', [x, y], { 
        name: '', // Remove the default label
        fixed: true
    });
    sunPositions.push(point);
    
    // Calculate position for label (extend 20% further from center)
    const labelX = x * 1.2;
    const labelY = y * 1.2;
    
    // Create text label at the extended position
    board.create('text', [labelX, labelY, data[2]], {
        fontSize: 12,
        fixed: true,
        anchorX: 'middle',
        anchorY: 'middle'
    });
}
```