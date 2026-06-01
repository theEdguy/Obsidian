---
id: 141ef123-4788-4888-add2-29715cc7ba22
title: "Nachrichtenrouting"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - nachrichtenorientierte-middleware
  - routing
  - message-queuing
  - netzwerkprotokolle
  - skalierbarkeit
  - fehlertoleranz
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Nachrichtenrouting]]

- **Kernkonzept:** Nachrichtenrouting bezeichnet den Prozess, [[Nachricht|Nachrichten]] in verteilten Systemen zielgerichtet durch [[Netzwerk|Netzwerke]] oder [[Middleware]]-Komponenten wie [[Queue-Manager]] oder [[Message-Broker]] zu leiten. Es ermöglicht die effiziente und zuverlässige Zustellung von [[Datenpaket|Datenpaketen]] zwischen [[Sender|Sendern]] und [[Empfänger|Empfängern]], selbst bei komplexen Topologien.
- **Nutzen & Zweck:** Nachrichtenrouting löst das [[Problem]] der [[Kommunikation]] in verteilten Systemen, indem es [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Entkopplung]] von [[Komponente|Komponenten]] ermöglicht. Es sorgt dafür, dass [[Nachricht|Nachrichten]] auch bei heterogenen [[Netzwerk|Netzwerken]], unterschiedlichen [[Protokoll|Protokollen]] oder temporären [[Verbindung|Verbindungsabbrüchen]] ihr Ziel erreichen. Besonders nützlich ist es in [[Message-Queuing-System|Message-Queuing-Systemen]] oder [[Publish-Subscribe-Architektur|Publish-Subscribe-Architekturen]].
- **Abgrenzung & Grenzen:** Nachrichtenrouting sollte nicht genutzt werden, wenn direkte [[Punkt-zu-Punkt-Kommunikation]] ausreicht (z. B. in einfachen [[Client-Server-Architektur|Client-Server-Systemen]]). Es ist oft überdimensioniert für [[Echtzeitanwendung|Echtzeitanwendungen]] mit strengen [[Latenz|Latenzanforderungen]], da [[Middleware]]-Schichten zusätzliche [[Overhead|Overheads]] verursachen. Alternativen wie [[RPC]] oder [[Multicast]] auf [[Netzwerkebene]] können in solchen Fällen effizienter sein. Zudem erfordert Routing manuelle [[Konfiguration]] (z. B. in [[IBM-MQ]]), was bei dynamischen [[Netzwerk|Netzwerken]] nachteilig sein kann.
- **Beispiel / Code:** ```
// Beispiel: Routing in IBM MQ (pseudocode)
// Sender legt Nachricht in lokale Queue mit logischem Zielnamen
MQPUT(Hconn, Hobj, "LA1", message, MQMD, MQPMO, CompCode, Reason);

// Queue-Manager QMA löst logischen Namen "LA1" über Alias-Tabelle auf
Alias-Tabelle (QMA):
  LA1 → QMC
Routing-Tabelle (QMA):
  QMC → SQ1 (über QMB)

// Nachricht wird über Channel an QMB weitergeleitet
// QMB leitet an QMC weiter, wo sie in SQ1 landet
```

**Erläuterung**: Die Nachricht wird zunächst in die lokale Queue des Senders gestellt. Der [[Queue-Manager]] nutzt [[Alias-Tabelle|Alias-Tabellen]] und [[Routing-Tabelle|Routing-Tabellen]], um den physischen Pfad zum Ziel zu bestimmen. [[Message-Channel-Agent|MCAs]] verpacken die Nachricht für die [[Transportschicht]] und leiten sie über [[Channel|Channels]] weiter. Bei Fehlern landet die Nachricht in der [[Dead-Letter-Queue]].
