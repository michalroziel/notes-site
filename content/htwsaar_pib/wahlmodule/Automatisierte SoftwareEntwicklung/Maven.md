

## Früher : Make - Files 
- Verwendung von MakeFiles zur Definition von [[build]]-Prozessen 
- [[C]] Programme werden heutzutage teilweise immer noch damit gebaut 
- Komplexität und Unübersichtkeit bei größeren Projekten 

```
CC = gcc

CFLAGS = -Wall -g 

all : helloworld 

helloworld : main.o helper.o 
	$(CC) $(CLAGS) -o helloworld main.o helper.o 

main.o : main.c
	$(CC) $(CLAGS) 
	
	[---]

```

> [!CAUTION]
> Bei MakeFiles sind whitespaces sehr wichtig.

## Ant Build Tool 

- Ant ist ein [[build]] Tool für [[Java]] Projekten
## Ant Beispiel : 

```xml
<project name="helloworld" default="run">
    <target name="compile">
        <javac srcdir="src" destdir="bin"/>
    </target>
    <target name="run" depends="compile">
        <java classname="helloworld.HelloWorld" fork="true">
            <classpath>
                <pathelement path="bin"/>
            </classpath>
        </java>
    </target>

```


## Maven
- Maven ist ein [[build]] Tool für [[Java]] Projekte

- Automatisches Dependency Management

### Maven Beispeil : 

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>helloworld</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
            <version>1.7.30</version>
        </dependency>
    </dependencies>

```




