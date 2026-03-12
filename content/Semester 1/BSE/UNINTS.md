---

## Zur Erinnerung: Was sind Daemons?

**Daemons** sind wie unsichtbare Helfer im Computuer, die im Hintergrund arbeiten. Sie starten oft automatisch, wenn der Computer hochfährt und warten darauf, ihre Aufgaben zu erledigen.  
  
Es gibt zwei Arten :

- **Systemdienste:** Dinge, die das System braucht (z. B. Netzwerk starten).

- **Serverdienste:** Dinge, die der Benutzer installiert (z. B. ein Webserver)

---

## Steuerung von Units mit systemctl

Mit “systemctl” stuerst du, welche Helfer (Daemons oder andere “Units”) laufen.

Befehle die du kennen solltest sind:

```SQL
Starten: systemctl starten <units>

Stoppen: systemctl stop <units>

Status prüfen: systemctl status <units>
```

---

  

## Units-Typen

  

Units sind wie verschiedene Werkzeuge. Es gibt viele Typen, z.B.:

1. Service Unit (.servie):  
    - Startet Programme oder Daemons  
    - Beispiel: Dein Webserver starten mit einer Service Units.  
    

1. Timer Units (.timer):  
    - Führt etwas regelmäßig oder zu einem bestimmten Zeitpunkt aus.  
    - Beispiel: Automatisches Backup  
    

1. Path Units (.path)  
    - Starten etwas, wenn sich eine Daten oder ein Ordner ändert.  
    - Beispiel: Ein Ordner wird Überwacht.  
    

1. Mount Units (.mount):  
    - Bindet Dateisystem ein.  
    - Beispiel: Automatische Einbinden eines USB-Sticks.  
    

1. Target Unit (.target)  
    - Bestimmt Zustände des Systems (z. B. Mehrbenutzermodus oder Neustart)

---

## Systemweite und benutzereigene Units

Systemweite Units:  
- Können nur von einem Admin (root) erstellen und geändert werden.  
- Speicherorte: /etc/systemd/system  
  
Benutzereigene Units:  
- Jeder Benutzer kann eigene Units für sich selbst erstellen.  
- Speicherorte: ~/.config/systemd/user oder ~/.local/share/systemd/user.

---

## Units anlegen

Eine Unit-Datei besteht aus drei Abschnitten:

1. **[Units]** Allgemeine Infos (z. B. Beschreibung, Abhängigkeiten).

1. [Service] Einstellungen für den Service ( z. B. welches Skript ausgeführt wird)

1. [Install] Wann und wie die Unit gestartet wird.  
      
    Beispiel für eine einfache Unit:

```Bash
[Unit]
Description=Beispielservice
After=network.target

[Service]
ExecStart=/path/zu/deinem/skript.sh
Type=simple

[Install]
WantedBy=multi-user.target
```

---

## Arbeiten mit Units

- **Units aktivieren:** sudo systemctl enable <units>

- **Units deaktivieren:** sudo systemctl disable <units>

- Unit neu laden: sudo systemctl deamon-reload

---

## Logdateien

Logdateien sind wie ein Tagebuch deines Systems. Sie protokollieren, was passiert ist.  
Speichertort: /var/ loq/.  
  
Wichtige Logdateien:  
auth.log: Anmeldeversuche.  
syslog: Allgemeine Systemmeldungen.  
kern.log: Meldungen vom Kernel.

---

## Übung 5

  
Aufgabe 5.1

1. Was sind Units?  
    Units sind verschiedene Werkzeugen, um Prozesse , Timer, Mounts usw. zu steuern.  
    

1. Wie werden Units angelegt?  
    

  

1. Nennen Sie 3 Unit-Typen.

1. Was sind Target Units? Nennen Sie 4 Beispiele.

1. Worin unterscheiden sich systemweite und benutzereigene Units?