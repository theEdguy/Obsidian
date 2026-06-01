---
id: c2fe5d36-ae0a-4469-9dbc-85a02243c3e1
title: "Port-Tabelle"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - rpc
  - kommunikation
  - adressierung
  - dce
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Port-Tabelle]]

- **Kernkonzept:** Eine [[Port-Tabelle|Port-Tabellen]] verwaltet die Zuordnung von [[Netzwerkdienst|Netzwerkdiensten]] zu spezifischen [[Port|Ports]] auf einem [[Server|Server]], um [[Kommunikation|Kommunikations]]-Endpunkte in [[Verteilte Systeme|verteilten Systemen]] eindeutig zu identifizieren.
- **Nutzen & Zweck:** Sie löst das [[Problem]] der dynamischen [[Adressierung]] und [[Lokalisierung]] von [[Server-Prozess|Server-Prozessen]] in [[RPC|RPCs]] oder [[Socket|Sockets]], indem sie [[Client|Clients]] ermöglicht, den korrekten [[Port]] für die [[Kommunikation]] mit einem [[Dienst]] zu finden, ohne statische Konfigurationen vorauszusetzen.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit statischen [[Port]]-Zuweisungen oder wenn [[Sicherheit]] durch feste [[Firewall]]-Regeln priorisiert wird. Unterscheidet sich von [[DNS]] durch die Fokussierung auf [[Prozess]]-Ebene statt [[Host]]-Ebene. Alternativen wie [[Service Discovery]]-Protokolle (z. B. [[Consul]]) bieten erweiterte Funktionen wie [[Lastverteilung]] oder [[Ausfallsicherheit]].
- **Beispiel / Code:** Im [[DCE RPC]]-Beispiel registriert ein [[Server]] seinen [[Dienst]] mit einem [[Port]] in der [[Port-Tabelle]] des lokalen [[DCE Daemon|DCE-Daemons]]. Ein [[Client]] fragt den [[Directory Server]] nach dem [[Server]]-Rechner und anschließend den [[DCE Daemon]] nach dem [[Port]], um die [[Bindung]] herzustellen:

1. Server: `register_service(port=5000)` → [[Port-Tabelle]]
2. Client: `query_directory_server(server_name)` → [[Host]]-Adresse
3. Client: `query_dce_daemon(host, service_name)` → [[Port]] 5000
4. Client: `connect(host, port=5000)` → [[RPC]]-Aufruf.
