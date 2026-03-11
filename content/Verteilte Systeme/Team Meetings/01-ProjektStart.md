# Team-Meeting – Projektstart / Architektur & Organisation

**Datum:** 2025-12-01

**Uhrzeit:** 12:00–14:00

**Ort/Tool:** z.B. Stl Raum

**Teilnehmer:** Michal, Valentin, Xudong, Christian, Sophia

**Moderator:** Valentin

**Protokollführer:** Xudong/Sophia

---

## Agenda

1. Kommunikations- und Arbeitsstruktur

1. Rollenverteilung & Organisation

1. Architektur- und Technikentscheidungen

1. Nächste Schritte & Deadlines

---

## Besprochene Themen

### 1. Kommunikations- und Arbeitsstruktur

### Wichtige Notizen:

- Kommunikation über WhatsApp (Termine), Discord (Meetings & Austausch), sowie Vor-Ort-Meetings (Mensa/STL/Seminarräume).

- Agile Arbeitsweise mit Weekly Sprints.

- Komponenten werden auf Teammitglieder verteilt und im Sprint besprochen.

- Arbeiten mit 2–3 Branches.

- Vor jedem Push Kommunikation über die Kanäle.

### Fragen:

- Müssen weitere Tools genutzt werden?

### Entscheidung:

- WhatsApp + Discord + Vor-Ort bleiben.

- Weekly Sprints fix.

### 2. Rollenverteilung & Organisation

### Wichtige Notizen:

- Scrum Master: Valentin

- Product Owner/Manager: Sophia

### Fragen:

- Wer übernimmt Testing?  
    ###\#Entscheidung:

- Rollen bleiben wie festgelegt.

### 3. Architektur- und Technikentscheidungen

### Wichtige Notizen:

- Architektur: Client-Server.

- Warum kein Peer-to-Peer? → Vorbereitung für Slides.

Technik:

- Docker für Container/Umgebung (Diskussion: lokal vs. Docker; Server vermutlich auf einem Gerät).

- Jackson für JSON-Serialisierung.

- SQLite + jOOQ für Datenbank.

- Test: JUnit, Integration Tests, Blackbox Tests, Mockito.

- Python-Skript herunterladen.

- Clean Git-Workflow mit Personal Access Token.

- README beachten.

- Component Diagram in Draw.io erstellen.

### Fragen:

- Wird Docker verpflichtend oder optional?

- Wird der Server zentral oder verteilt laufen?

### Entscheidung:

- Client-Server wird verwendet.

- Thema „Warum nicht Peer-to-Peer?“ wird in Slides begründet.

### 4. Nächste Schritte & Deadlines

### Wichtige Notizen:

- Nächstes Meeting: 17.12. (Frist)

### Fragen:

- Was muss bis zum 17.12. final stehen?

### Entscheidung:

- Fokus: Slides & erste technische Struktur.

---

## Entscheidungen

- Architektur: Client-Server wird genutzt, Peer-to-Peer verworfen.

- Kommunikationskanäle: WhatsApp + Discord + Vor-Ort.

- Arbeitsweise: Agile mit Weekly Sprints.

- Rollen festgelegt: Valentin (Scrum Master), Sophia (PO).

---

## Action Items

|Aufgabe|Verantwortlich|Fällig bis|Status|
|---|---|---|---|
|Slides erstellen (Client-Server vs. P2P)|Sophia/ Team|2025-12-17|Offen|
|Component Diagram in Draw.io erstellen|Team|2025-12-17|In Arbeit|

---

## Offene Punkte / Risiken

- Unklar, ob Docker vollständig genutzt wird.

- Unklar, ob Server lokal oder containerisiert laufen soll.

- Risiko: kurze Frist bis zum 17.12.

- Aufgabenverteilung für Testing noch offen.