
## Aufgabe 1) – Allgemeines


### **a) Warum werden die OSI-Schichten 5–7 gerne zusammengefasst dargestellt?**
Die Schichten 5 bis 7 (Sitzungsschicht, Darstellungsschicht, Anwendungsschicht) werden oft zusammengefasst, weil sie eng miteinander zusammenarbeiten und meist direkt von Anwendungen genutzt werden.


### **b) Erklären Sie den Begriff „Protokoll-Overhead“.**

Der Protokoll-Overhead bezeichnet den zusätzlichen Datenaufwand, der entsteht, weil Protokolle neben den eigentlichen Nutzdaten auch Steuerinformationen (z. B. Header) übertragen müssen


### **c) Wie werden Anwendungen auf einem Host adressiert und unterschieden?**

Anwendungen auf einem Host werden durch sogenannte **Portnummern** unterschieden. Diese Ports sind zusammen mit der IP-Adresse Teil der vollständigen Netzwerkadresse


### **d) Warum werden private IP-Adressen im öffentlichen Netz üblicherweise nicht geroutet?**

Private IP-Adressen sind laut Standard (z. B. RFC 1918) nur für den internen Gebrauch in lokalen Netzwerken gedacht. Damit es im Internet keine Adresskonflikte gibt, werden diese Adressen von Routern im öffentlichen Netz ignoriert und nicht weitergeleitet.


### **e) NAT/PAT-Gateways in Heimnetzen implementieren häufig eine Firewall. Warum ist das sinnvoll?**

Eine Firewall im NAT/PAT-Gateway schützt das Heimnetz vor ungewollten Zugriffen aus dem Internet. Da NAT/PAT die Kommunikation von innen nach außen kontrolliert, kann die Firewall verhindern, dass fremde Systeme von außen ohne Erlaubnis Daten ins Heimnetz senden.


### **f) Was ist der Unterschied zwischen „Forward-Lookup-Zones“ und „Reverse-Lookup-Zone“ in Bezug auf DNS?**

- **Forward-Lookup-Zone**: Hierbei wird ein Domainname (z. B. „google.com“) in eine IP-Adresse übersetzt. Das ist die **übliche** Richtung bei DNS-Anfragen.
    
- **Reverse-Lookup-Zone**: Hier wird der umgekehrte Weg genutzt – eine IP-Adresse wird in einen Domainnamen aufgelöst. Dies wird z. B. für Diagnosezwecke oder bei sicherheitsrelevanten Prüfungen.



# Aufgabe 2) – Geben Sie für folgende Aussagen an, ob diese korrekt, oder falsch sind

###### **a) Das DHCP-Protokoll versorgt Hosts eigenständig mit notwendigen Informationen, um in einem Computer-Netzwerk arbeiten zu können.**

Richtig 

DHCP (Dynamic Host [[configuration]] Protocol) weist Geräten automatisch IP-Adressen sowie weitere Netzwerkinformationen (z. B. Gateway, Subnetzmaske) zu, sodass diese im Netzwerk kommunizieren können.

##### **b) Neben der IP-Konfiguration können über das DHCP-Protokoll auch weitere relevante Informationen wie z. B. ein Zeitserver oder DNS-Server verteilt werden.**

 Richtig

DHCP kann nicht nur IP-Adressen, sondern auch zusätzliche Informationen wie Standard-Gateway, DNS-Server, Zeitserver oder sogar Domainnamen bereitstellen.

##### **c) Nahezu alle Heim-Router implementieren die Funktion von DHCP- und DNS-Server.**

RIchtig 

Typische Heim-Router enthalten integrierte DHCP- und DNS-Server, um lokalen Geräten automatisch IP-Adressen zuzuweisen und DNS-Anfragen weiterzuleiten oder selbst zu verarbeiten.


##### **d) Ohne DNS-Server können wir das Internet nicht benutzen.

Falsch 

Das Internet ist _theoretisch_ auch ohne DNS nutzbar – man müsste jedoch IP-Adressen manuell eingeben. DNS ist also nicht zwingend erforderlich, aber es ist in der Praxis unerlässlich für komfortable Nutzung, da sich niemand alle IP-Adressen merken kann.



# Aufgabe 3) – Adressübersetzung

## **Vorteile:**

1. **IP-Adressersparnis:**
NAT/PAT ermöglicht vielen Geräten in einem privaten Netzwerk den Zugang zum Internet 
über eine einzige öffentliche IP-Adresse. Das spart öffentliche IP-Adressen.

2. **Schutz vor Zugriffen von außen:**
Geräte im privaten Netzwerk sind von außen nicht direkt erreichbar. Das bietet eine gewisse Sicherheitsbarriere gegen unerwünschte Zugriffe.

### **Nachteile:**

1. **Erschwerte direkte Kommunikation:**
Dienste wie z. B. Peer-to-Peer, Online-Gaming oder Serverbetrieb im Heimnetz sind schwieriger umzusetzen, da eingehende Verbindungen blockiert oder umgeleitet werden müssen.

2. **Zusätzliche Komplexität und Verzögerung:**
NAT/PAT müssen Datenpakete umschreiben (IP- und Port-Adressen anpassen), was den Netzwerkverkehr leicht verlangsamen und die Fehleranalyse erschweren kann.


# Aufgabe 4) – Domain-Name-Service

###### **Zuständigen Nameserver für kil-s-01.htwsaar.de finden**
```
dig kil-s-01.htwsaar.de NS

dig - DNS lookup utility
```

###### **P-Adresse von moodle.htwsaar.de ermitteln**
```
dig moodle.htwsaar.de +short
```

###### **Einen bestimmten DNS-Server direkt fragen (z. B. Google DNS: 8.8.8.8)**
```
dig @8.8.8.8 htwsaar.de
```

##### **DNS-Verkehr mit tcpdump mitschneiden**
```
sudo tcpdump -i any port 53 -nn

Zeigt alle DNS-Anfragen und -Antworten (Port 53, TCP/UDP) auf allen Interfaces, IPs und Ports im Klartext.
```


