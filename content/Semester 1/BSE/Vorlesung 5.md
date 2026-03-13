```TOML
v5 - Units, Logging:
--------------------
- systemctl
- Unit Typen
- Benutzereigene und systemweite Units
- Unit anlegen
- Logdateien
- Ort von Logdateien
- Anzeige von Logdateien
- Logfiles rotieren
```

---

## Systemctl

ist das Kommando zur Steuerung von Systemd, dem init System, das alles laufende [[UNINTS|Units]] aud einem System verwaltet. die [[Vorlesung 4|Prozesse]] laufen auch parallel, um den Bootvorgang zu beschleunigen

```SQL
Systemctl[<optionen><Komando><unit>]
```

---

## Units Typen

- Service Units (.service)

- TimerUnit (.timer)

- Path U. ( .path)

- Mount (.mount)

---

## Systemweite und benutzereigene Units

Man unterscheidet 2 Arten von Units:

- **Systemweite** Units können nur von [[Vorlesung 12|root]] angelegt und bearbeitet werden

- **Benutzereigene** Units können vom Benutzer fur sich selbst  
    angelegt und geändert werden

---

## Units anlegen

![[/image 11.png|image 11.png]]

## Siehe auch

- [[UNINTS]]
- [[Vorlesung 4]]
- [[Prozess in Betriebssystemen]]
- [[Klausur]]
