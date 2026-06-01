---
id: 4d7365c2-d79f-4647-a54c-86abd3882f53
title: "Endpunkt (Netzwerk)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - architektur
  - server
  - client
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Endpunkt (Netzwerk)]]

- **Kernkonzept:** Ein [[Endpunkt|Endpunkt]] (Netzwerk) bezeichnet eine eindeutige Adresse (z. B. IP-Adresse und Portnummer), über die ein [[Prozess|Prozesse]] in einem [[verteilten System|verteilten System]] mit anderen kommunizieren kann. Er dient als Schnittstelle für den [[Datenverkehr|Datenverkehr]] zwischen [[Client|Clients]] und [[Server|Servern]].
- **Nutzen & Zweck:** Endpunkte ermöglichen die [[Kommunikation|Kommunikation]] zwischen [[Prozess|Prozessen]] in [[verteilten Systemen|verteilten Systemen]], indem sie eine standardisierte Methode zur Adressierung und [[Interaktion|Interaktion]] bereitstellen. Sie lösen das Problem der [[Koordination|Koordination]] und [[Zuordnung|Zuordnung]] von [[Anfrage|Anfragen]] zu spezifischen Diensten oder [[Ressource|Ressourcen]].
- **Abgrenzung & Grenzen:** Endpunkte sollten nicht genutzt werden, wenn eine direkte [[Prozesskommunikation|Prozesskommunikation]] ohne Netzwerkschicht möglich ist (z. B. innerhalb eines einzelnen [[Betriebssystem|Betriebssystems]]). Alternativen wie [[Shared Memory|Shared Memory]] oder [[Message Passing|Message Passing]] auf lokaler Ebene können effizienter sein. Endpunkte unterscheiden sich von [[Middleware|Middleware]]-Lösungen, da sie keine zusätzliche Abstraktionsebene einführen, sondern lediglich die Adressierung ermöglichen.
- **Beispiel / Code:** Ein einfaches Beispiel für die Nutzung eines Endpunkts in einem TCP-Server (Python):

```python
import socket

# Endpunkt definieren: IP-Adresse und Port
HOST = '127.0.0.1'  # Lokale Adresse
PORT = 65432        # Portnummer

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))  # Endpunkt binden
    s.listen()
    conn, addr = s.accept()  # Auf eingehende Verbindung warten
    with conn:
        print(f'Verbunden mit {addr}')
        data = conn.recv(1024)
        conn.sendall(data)  # Echo-Antwort
```

Hier wird der Endpunkt `(127.0.0.1, 65432)` genutzt, um einen [[Echo-Server|Echo-Server]] zu implementieren.
