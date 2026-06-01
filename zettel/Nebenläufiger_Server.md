---
id: 18f78426-b86b-4a72-8e18-f91c69f938e1
title: "Nebenläufiger Server"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - server-architektur
  - nebenläufigkeit
  - netzwerk
  - parallelisierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Nebenläufiger Server]]

- **Kernkonzept:** Ein [[nebenläufiger|Nebenläufiger]] [[Server]] nutzt einen [[Dispatcher]], um eingehende [[Request|Requests]] an separate [[Thread|Threads]] oder [[Prozess|Prozesse]] weiterzuleiten, um mehrere Anfragen gleichzeitig zu bearbeiten.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Skalierbarkeit]] und [[Effizienz]] in verteilten Systemen, indem es [[Blockierung|blockierende]] Operationen (z. B. [[Festplattenzugriff]] oder [[Netzwerkkommunikation]]) parallelisiert und die [[Auslastung]] des [[Servers]] optimiert.
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Dienst|Dienste]] mit geringer Last, da der [[Overhead]] durch [[Thread]]- oder [[Prozess]]-Verwaltung die [[Performanz]] beeinträchtigen kann. Unterscheidet sich von [[iterativen|iterativen]] [[Servern]], die [[Request|Requests]] sequenziell abarbeiten und bei blockierenden Operationen ineffizient sind.
- **Beispiel / Code:** ```python
import threading
import socket

def handle_client(client_socket):
    request = client_socket.recv(1024)
    print(f"Empfangen: {request}")
    client_socket.send(b"ACK")
    client_socket.close()

def main():
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind(('0.0.0.0', 9999))
    server.listen(5)
    print("Server lauscht auf Port 9999")
    
    while True:
        client_sock, addr = server.accept()
        print(f"Verbindung von {addr} akzeptiert")
        client_handler = threading.Thread(target=handle_client, args=(client_sock,))
        client_handler.start()

if __name__ == "__main__":
    main()
```
*Einfacher TCP-Server mit Threads für nebenläufige Request-Bearbeitung.*
