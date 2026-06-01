---
id: 5b3086a0-df6a-48b1-bd6f-86ae0ba071a8
title: "Protokoll (in Kommunikationssystemen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - verteilte-systeme
  - netzwerk
  - architektur
  - schichtenmodell
  - schnittstelle
  - standardisierung
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Protokoll (in Kommunikationssystemen)]]

- **Kernkonzept:** Ein [[Protokoll|Protokoll]] definiert Regeln und Formate für den [[Datenaustausch|Datenaustausch]] zwischen [[Komponente|Komponenten]] in [[Kommunikationssystem|Kommunikationssystemen]], um eine standardisierte und fehlerfreie [[Kommunikation]] zu ermöglichen.
- **Nutzen & Zweck:** Protokolle lösen das [[Problem]] der [[Interoperabilität]] in [[verteilte Systeme|verteilten Systemen]], indem sie einheitliche [[Schnittstelle|Schnittstellen]] und [[Verhalten|Verhaltensregeln]] für die [[Kommunikation]] zwischen heterogenen [[System|Systemen]] oder [[Komponente|Komponenten]] bereitstellen. Sie ermöglichen [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Modularität]] durch klare Trennung von [[Verantwortung|Verantwortlichkeiten]] in [[Schicht|Schichten]].
- **Abgrenzung & Grenzen:** Protokolle sind nicht geeignet, wenn [[Echtzeitanforderung|Echtzeitanforderungen]] oder extrem niedrige [[Latenz]] priorisiert werden, da sie oft [[Overhead]] durch [[Header]], [[Handshake]] oder [[Fehlerbehandlung]] verursachen. Alternativen wie [[direkte Kommunikation]] (z. B. [[Shared Memory]]) oder [[ereignisbasierte Systeme]] (ohne feste Protokollregeln) können hier effizienter sein. Zudem sind Protokolle oft [[unflexibel]] gegenüber dynamischen [[Anforderung|Anforderungen]], die sich zur [[Laufzeit]] ändern.
- **Beispiel / Code:** Beispiel: TCP/IP-basierte [[Socket-Kommunikation]] zwischen [[Client]] und [[Server]] (vereinfacht):

**Server (Python):**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.bind(('localhost', 12345))
s.listen(1)
conn, addr = s.accept()
data = conn.recv(1024)
conn.send(data.upper().encode())
conn.close()
```

**Client (Python):**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.connect(('localhost', 12345))
s.send(b'Hello')
data = s.recv(1024)
print(data.decode())
s.close()
```

Das [[Protokoll]] definiert hier: [[Port]], [[Datenformat]] (Bytes), [[Ablauf]] (Verbindung aufbauen → Daten senden/empfangen → Verbindung schließen).
