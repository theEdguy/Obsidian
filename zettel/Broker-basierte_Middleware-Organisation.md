---
id: 0bdbb3ff-0899-4a01-bf08-269d9880420d
title: "Broker-basierte Middleware-Organisation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - middleware
  - verteilte-systeme
  - architektur
  - schnittstellen
  - koordination
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Broker-basierte Middleware-Organisation]]

- **Kernkonzept:** Die broker-basierte [[Middleware-Organisation|Middleware-Organisation]] nutzt einen zentralen [[Broker]], um die Kommunikation zwischen [[Anwendung|Anwendungen]] und [[Wrapper|Wrappern]] zu koordinieren. Sie reduziert die Komplexität der [[Schnittstellen|Schnittstellen]]-Verwaltung in verteilten [[System|Systemen]].
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der hohen Anzahl benötigter [[Wrapper]] in 1-zu-1-Architekturen (O(N²)). Durch den [[Broker]] sinkt der Aufwand auf O(N), da jede [[Anwendung]] nur mit dem [[Broker]] kommuniziert, statt direkt mit allen anderen [[Anwendung|Anwendungen]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Latenz]] kritisch ist (der [[Broker]] wird zum Flaschenhals) oder bei hochspezialisierten [[Schnittstellen]], die keine Standardisierung erlauben. Alternativen sind [[Peer-to-Peer-Systeme]] (dezentral) oder direkte 1-zu-1-[[Wrapper]] (bei wenigen [[Anwendung|Anwendungen]]).
- **Beispiel / Code:** ```python
# Pseudocode: Broker-basierte Kommunikation
broker = Broker()

# Anwendung A sendet Daten via Broker
wrapper_A = Wrapper(app_A, broker)
wrapper_A.send("Daten für B")

# Anwendung B empfängt Daten via Broker
wrapper_B = Wrapper(app_B, broker)
data = wrapper_B.receive()
```

*Erläuterung*: Der [[Broker]] leitet Nachrichten zwischen [[Wrapper|Wrappern]] weiter, ohne dass [[Anwendung|Anwendungen]] direkt verbunden sein müssen.
