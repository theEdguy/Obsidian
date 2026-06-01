---
id: 9a7adce9-7a3a-40ea-86d1-c6baca581326
title: "Daemon"
date: 2026-06-01
tags:
  - verteilte_systeme
  - betriebssystem
  - netzwerk
  - server
  - hintergrundprozess
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Daemon]]

- **Kernkonzept:** Ein [[Daemon|Daemon]] ist ein Hintergrundprozess in einem [[Betriebssystem|Betriebssystem]], der kontinuierlich läuft und [[Dienst|Dienste]] für andere [[Prozess|Prozesse]] oder [[System|Systeme]] bereitstellt, ohne direkte Benutzerinteraktion.
- **Nutzen & Zweck:** Ein [[Daemon|Daemon]] löst das Problem der persistenten Bereitstellung von [[Dienst|Diensten]] wie Netzwerkkommunikation, [[Ressource|Ressourcen]]-Verwaltung oder Systemüberwachung. Er ermöglicht die Entkopplung von [[Client|Clients]] und [[Server|Servern]], indem er als Vermittler für [[Anfrage|Anfragen]] fungiert und [[Endpunkt|Endpunkte]] dynamisch verwaltet.
- **Abgrenzung & Grenzen:** Ein [[Daemon|Daemon]] sollte nicht genutzt werden, wenn kurzlebige oder benutzerinteraktive [[Prozess|Prozesse]] benötigt werden. Alternativen wie [[Thread|Threads]] oder [[Cron-Job|Cron-Jobs]] sind besser geeignet für temporäre oder zeitgesteuerte Aufgaben. Im Gegensatz zu [[Anwendung|Anwendungen]] mit grafischer Oberfläche läuft ein [[Daemon|Daemon]] unsichtbar im Hintergrund.
- **Beispiel / Code:** Ein klassisches Beispiel ist der `sshd`-Daemon (Secure Shell Daemon), der auf einem [[Server|Server]] läuft und eingehende SSH-Verbindungen verwaltet:

```
# Starten des SSH-Daemons (Linux)
sudo systemctl start sshd
# Überprüfen des Status
sudo systemctl status sshd
```

Der `sshd` lauscht standardmäßig auf Port 22 und leitet [[Anfrage|Anfragen]] an den entsprechenden [[Prozess|Prozess]] weiter.
