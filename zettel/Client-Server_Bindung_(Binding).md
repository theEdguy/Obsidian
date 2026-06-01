---
id: e51afcf3-3efd-4786-bfe1-5cb5500e8815
title: "Client-Server Bindung (Binding)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - rpc
  - netzwerk
  - kommunikation
  - koordination
  - dynamische_zuordnung
  - dce
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Client-Server Bindung (Binding)]]

- **Kernkonzept:** Die [[Client-Server Bindung|Client-Server-Bindung]] (Binding) beschreibt den Prozess, bei dem ein [[Client]] einen [[Server]] lokalisiert und eine Verbindung zu dessen [[Dienst|Diensten]] herstellt, um [[Remote Procedure Call|RPCs]] oder [[Nachrichten]] auszutauschen. Dies umfasst die Auflösung von [[Adresse|Adressen]] und [[Port]]-Informationen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der dynamischen [[Lokalisierung]] und [[Zuordnung]] von [[Server]]-Instanzen in verteilten Systemen. Ohne [[Binding]] müssten [[Client]]s manuell [[Adresse|Adressen]] und [[Port]]s verwalten, was die [[Skalierbarkeit]] und [[Flexibilität]] des Systems stark einschränken würde. Es ermöglicht [[Zugriffstransparenz]] und vereinfacht die [[Kommunikation]] zwischen verteilten Komponenten.
- **Abgrenzung & Grenzen:** Binding sollte nicht genutzt werden, wenn [[Statische Adressierung]] ausreicht (z. B. in kleinen, unveränderlichen Systemen) oder wenn der [[Overhead]] der [[Dynamischen Auflösung]] die [[Performance]] unnötig beeinträchtigt. Alternativen wie [[Service Discovery]]-Protokolle (z. B. DNS, Consul) oder [[Message Broker]] (z. B. RabbitMQ) können in komplexeren Szenarien besser geeignet sein, da sie zusätzliche Funktionen wie [[Lastverteilung]] oder [[Fehlertoleranz]] bieten.
- **Beispiel / Code:** Im DCE-RPC-Beispiel erfolgt das Binding in folgenden Schritten:
1. Der [[Server]] registriert seinen [[Dienst]] und [[Port]] beim lokalen DCE-Daemon.
2. Der [[Client]] fragt einen [[Directory Server]] nach der [[Adresse]] des [[Server]]-Rechners.
3. Der [[Client]] kontaktiert den [[Server]]-Rechner und fragt den [[Port]] des [[Dienst|Dienstes]] ab.
4. Der [[Client]] stellt eine Verbindung zum [[Server]] her und führt den RPC aus.

Python-ähnliches Pseudocode-Beispiel:
```
# Server
server_socket.bind((HOST, PORT))
server_socket.listen(1)
directory_server.register_service(service_name, HOST, PORT)

# Client
server_address = directory_server.lookup(service_name)
client_socket.connect(server_address)
```
