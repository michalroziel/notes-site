
### Was ist Mini CDN ?

Das Mini CDN der Gruppe 8 in Verteilte Systeme stellt ein Implementiertes Konzept eines Content Delivery Networks da. In einem  In userem Verteilten System gibt es einen Origin Server und mehrere Edge Server. User können mittels CLI Eingaben Dateien herunterladen. Mini-CDN Admins können Dateien auf den Origin Server hochladen, die Infrastruktur verwalten, sowie Statistiken bezüglich der Anwendung einsehen. 

Im weiteren sind mit der Bezeichnung *Server* einzelne ```HTTP``` Ports gemeint.

Die Anwendung beruht auf einer ```Client-Server``` Architektur und wurde durch ein 
```multi maven``` Projekt implementiert. 


### Vorraussetzungen / Prerequisities  : Linux / OSX
```shell
java -version     # sollte Java 21 sein
mvn -version
cp .env.example .env
export MINICDN_ADMIN_TOKEN=secret-token
export MINICDN_ROUTER_URL=http://localhost:8082
```

## CLI Befehle 

#### Kompilieren der Anwendung und das Erstellen von Sources
```
mvn clean verify 
mvn clean package
```


#### Maven Spotless Code Formatierung
```
mvn spotless:apply
```
#### Maven Spotless Check 
```
mvn spotbugs:check
```

## Start der Anwendung
```shell
cd cli
mvn exec:java
```

#### Den health Endpunkt des 8080 Server prüfen  
```
curl http://localhost:8080/api/origin/health
```
#### Im neuen Terminal Prüfen ob Anfangs-Server funktionieren
```shell
❯ lsof -i:8080 -i:8081 -i:8082
```

#### Upload von Dateien als Admin - Lebenslauf.pdf
```
admin file upload --router http://localhost:8082 --region EU --path a.pdf --file /Users/xudongzhang/Downloads/Lebenslauf.pdf

# -file : your local file path
```


## admin resource list / show
```
admin file list --router http://localhost:8082
admin file show --origin http://localhost:8080 --path htwsaar.jpg
