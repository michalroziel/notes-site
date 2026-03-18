


# Problematic Issues : 

Ja. Kurz zusammengefasst waren vor allem diese Punkte **nicht ganz sauber**:

**Problematisch**

- **NFA-S2 Rollen**
    
    - Token-Schutz ist umgesetzt.
    - Die **serverseitige Rollenprüfung** ist aber nicht vollständig aktiv.
    - Der vorbereitete Rollenfilter AdminRoleAuthorizationFilter.[[Java]] ist aktuell nicht registriert.
    - Deshalb ist „falsche Rolle wird abgelehnt“ nicht sauber nachgewiesen.
- **NFA-S4 Duplikate**
    
    - Nur **teilweise idempotent**.
    - Routing, TTL-Policies und Datei-PUT sind okay.
    - **User-Anlage ist nicht idempotent**: gleicher Name kann mehrfach angelegt werden in RouterUserService.[[Java]].
    - Deshalb nicht als vollständig generelle “at least once”-Semantik verkaufen.
- **TS-M2 Serialisierungsmodul**
    
    - JacksonCodec ist da und funktioniert.
    - Aber es ist **nicht überall die einzige zentrale Quelle**.
    - Einige Teile nutzen weiterhin eigene ObjectMapper.
    - Also: weitgehend gut, aber nicht komplett vereinheitlicht.

**Mit Einschränkung, aber akzeptabel**

- **US-S2 Recovery**
    
    - Funktional gut nachgewiesen.
    - Aber es wird ein **definierter persistierter Zustand** wiederhergestellt, kein kompletter Laufzeitsnapshot aller transienten Zustände.
- **NFA-S5 Recovery**
    
    - Am Ende sauber nachgewiesen.
    - Problematisch war nur, dass die **alten Skripte veraltet** waren und erst ein neues JAR-basiertes Skript gebraucht wurde.
- **NFA-C2 Recovery nach Crash**
    
    - Ebenfalls sauber nachgewiesen.
    - Einschränkung: [[test]] zeigt **Edge-Crash-Recovery**, nicht vollständigen Totalcrash aller Services.

**Unkritisch / weitgehend sauber**

- **TS-M3 [[Maven]] Projekt einrichten**
- **TS-M4 CI/CD Pipeline**
- **TS-M3 Spotless [[plugin]]**
- **TS-M3 Edge Server Shell Script**
- **Backlog anlegen**

**Kurzfazit**  
Die wirklich heiklen Issues waren:

1. **NFA-S2 Rollen**
2. **NFA-S4 Duplikate**
3. **TS-M2 Serialisierungsmodul**

Die beiden Recovery-Issues waren eher **technisch okay, aber mit klaren Abgrenzungen**.

Wenn du willst, mache ich dir daraus noch eine **1:1 präsentationsfertige Liste mit “Done / Teilweise / Caveat”**.




