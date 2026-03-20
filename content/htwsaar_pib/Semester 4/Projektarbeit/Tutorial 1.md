[[content/htwsaar_pib/Semester 4/Projektarbeit/Projektarbeit]]

DOCUMENT OBJECT MODEL

```
classfile 



const fahrrad = {
    mark: "AUDI",
    leistung: "250 Watt",
    farbe_varianten: ["Silver", "Gunpowder Black", "Skyblue"]
};

const auto = {
    ...fahrrad,
    leistung: "300 kW",
};

//console.log(auto)

const dada = {
    room: "0815",
    begin: "08:00",
    end: "09:30",
    subject: "Defence Against the Dark Arts",
    speaker: "Severus Snape",
    students: ["Ron", "Harry", "Pansy", "Draco", "Hermione"]
};

const dada2 = {

    ...dada,
    speaker: "Gilderoy Lockhart"

}

dada.students.shift()
console.log(dada,dada2);


const sortedMark = [...globalMark].sort();



```


## Dieses Project 
DOM



vergeliche tailwind 


