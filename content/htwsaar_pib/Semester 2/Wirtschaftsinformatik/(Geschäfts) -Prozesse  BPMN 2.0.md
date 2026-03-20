  

### Was ist ein Prozess?

  

Ein Prozess ist eine -inhaltlich abgeschlossene..

..Abfolge von [[Funktionen]]..

..die aus einen oder mehreren Inputs..

..aber nur einen Output hat

  

  

### Wie lässt sich ein Geschäftsprozess von einem Prozess abgrenzen?

==Geschäftsprozess ist eine Abfolge von Aktivitäten, die verschiedene Inputs benötigen und ein Ergebnis mit Wert für den Kunden erzeugen.== ==Und Prozess ist eine Abfolge von schritten.==

  

  

### Welche Kategorien lassen sich Geschäftsprozesse einteilen? Welche Kategorie gibt es in der Praxis häufig?

Kategorien **„Primäre Geschäftsprozesse“** und **„Sekundäre Geschäftsprozesse“**

==**„Primäre Geschäftsprozesse“**== konzentrieren sich auf externe Kunden als Leistungsempfänger und erstellen und vermarkten ein Produkt bzw. eine Dienstleistung. (Auch Kern oder Schlüsselprozesse genannt.)

==**„Sekundäre Geschäftsprozesse“**== konzentrieren sich auf interne Kunden als Leistungsempfänger und unterstützen dabei entweder primäre Geschäftsprozesse oder andere sekundäre Geschäftsprozesse. (Auch Unterstützungsprozesse genannt.)  

Zusätzlich gibt es in der Praxis in der Regel auch noch==**Führungsprozesse**== als dritte Kategorie

  

# BPMN 2.0

- Business Process Model and Notation

- Fokus: Zeitlich-logische Abhängigkeiten der Prozess-Schritte

### Graph aus Grunsätzlich 4 Elementen :

![[Screenshot_2024-08-07_at_14.51.19.png]]

### Namenskonventionen :

- Generell : < 6 Wörter
    
    - Activities : Verb(Infinitiv), Nomen, z.B : Approve Order, Issue Drivers [[my-notes-site/node_modules/source-map-support/LICENSE|LICENSE]]
    
    - Events : Nomen, Verb(past participle), z.B : Invoice Emitted, Urgent order sent
    
      
    
    ### Gateways :
    
    - Verzweigung des Kontrollflusses
    
    - Gateway ist keine Aufgabe oder Aktivität
        
        - Nur Entscheidung
        
        - Grundlage für Entscheidung muss vorher herausgefunden werden
        
    
    - Zwei Arten jewils :
        
        - Split : EIn Eingang, mehrere Ausgänge
        
        - Join : Mehrere EIngänge, ein Ausgang
        
        - Split anschließend durch Join wieder zusammen fügen
        
        ![[Screenshot_2024-08-07_at_15.18.30.png]]