[[Übungsblätter]]


# IPv6 bietet einige Vorteile gegenüber IPv4.

#### Adressen

- IPv4 : 32 Bit Adressen : 4,3 Milliarden eindeutige IP-Adressen
- IPv6 : 128 Bit Adressen : 340 Sextillionen eindeutige Adressen 

#### Einfacheres Routing 
Durch eine mögliche Hierarchie können Adressen besser strukturiert werden 


#### Sicherheit 
IPSec ist bei IPv6 standard, bei IPv4 ist es optional. 


#### NAT 
Durch große Adressräume können Peer-to-Peer Anwendungen einfacher gestaltet werden


#### SLAAC (Automatische Konfiguration)
Hierbei können sich Geräte in IPv6 Netzwerken selbst zuweisen, ein DHCP server ist nicht notwendig erforderlich 



# Aufgabe 2) – IPv6-Adressen


### a) Kürzen sie folgenden IPv6 Adresse:

i. 2002:4711:0000:0000:0c04:546b:000c:00a6
>  2002:4711::c04:546b:[[C]]:a6

ii. 2001:c38e:52a2:4895:826a:959a:ac78:4b23
> 2001:c38e:52a2:4895:826a:959a:ac78:4b23

iii. 2000:0250::0000:32b8:0000:0000:46c6
> 2000:250::32b8:0:0:46c6 BLOCK VERLOREN ? 


### b) Prüfen Sie die folgenden Adressen auf ihre Gültigkeit

i. 2000::5369:4b:3a::2c56
> Ungültig, :: darf nur **einmal** vorkommen

ii. 2000:ab63:5cfe::4
> Gültig

iii. 2001:c38e:52a2:4895:86a:959a:ac78:4b23:8e6f
> Ungültig, 9 Blöcke und nicht 8 



### c) Sind die folgenden Adressen vollständig korrekt gekürzt?

i. 2000::
> Korrekt gekürzt.

ii. 2001:c38e:52a2:4895:086a:959a:ac78:4b23
> Nicht Korrekt, 086a enthält eine Führende Null

iii. 2000::68ba:89ad:1
> Korrekt gekürzt.



# Aufgabe 3) – Address-Scopes
IPv6-Adressen sind in verschiedene Scopes aufgeteilt.
Verbinden Sie sich mit einem Rechner im KIL und überprüfen dessen IP-Konfiguration.
Lösen Sie folgende Aufgaben:

### a)  Welche IPv6 Adresse hat der Rechner auf dem Interface?
*ifconfig* eingeben

### b) In welchem Scope liegt diese?

##### IPv6 Scopes : 
- Link-Local (fe80::/10): Gültig nur im lokalen Netzwerksegment.
- Unique Local (fc00::/7): Gültig im lokalen Netzwerk, nicht im Internet.
- Global Unicast (2000::/3): Weltweit eindeutig, im Internet geroutet.
- Multicast und weitere spezielle Scopes gibt es ebenfalls.

### c) Was können Sie über die Gültigkeit dieser sagen?

- LinkLocal: Nur innerhalb desselben Netzwerksegments gültig, keine Weiterleitung über Router.
- Unique Local: Gültig innerhalb einer Organisation, nicht im Internet routbar.
- Global Unicast: Weltweit eindeutig und im Internet routbar.
### d) Pingen Sie einen anderen Rechner im KI-Labor an.

```shell
ping <IPv6-Adresse des Zielrechners>
```

