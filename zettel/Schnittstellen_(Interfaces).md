---
id: 7d920e8a-c7be-466d-861a-3431d6c69d87
title: "Schnittstellen (Interfaces)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - schnittstellen
  - verteilte-systeme
  - kommunikation
  - entkopplung
  - protokolle
  - software-engineering
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Schnittstellen (Interfaces)]]

- **Kernkonzept:** Eine [[Schnittstelle|Schnittstelle]] definiert einen Vertrag zwischen [[Komponente|Komponenten]] in [[Verteilte Systeme|verteilten Systemen]], der [[Funktionalität|Funktionalitäten]] und [[Datenformat|Datenformate]] für die [[Interaktion]] festlegt, ohne die interne [[Implementierung]] offenzulegen.
- **Nutzen & Zweck:** [[Schnittstellen|Schnittstellen]] ermöglichen die [[Entkopplung]] von [[Komponente|Komponenten]], indem sie klare [[Vereinbarung|Vereinbarungen]] über [[Kommunikation]] und [[Datenfluss]] treffen. Sie lösen das [[Problem]] der [[Abhängigkeit]] zwischen [[Systemteil|Systemteilen]] und fördern [[Wiederverwendbarkeit]], [[Erweiterbarkeit]] und [[Standardisierung]] in [[Architektur|Architekturen]].
- **Abgrenzung & Grenzen:** [[Schnittstellen|Schnittstellen]] sind ungeeignet, wenn [[Flexibilität]] in der [[Datenübertragung]] oder [[Protokoll]]-Anpassung priorisiert wird (z. B. in [[REST]]-Systemen mit dynamischen [[Ressource|Ressourcen]]). Alternativen wie [[Protokoll]]-basierte [[Kommunikation]] (z. B. [[HTTP]]) oder [[Ereignisbus|Ereignisbusse]] bieten mehr [[Anpassungsfähigkeit]], erfordern aber höhere [[Komplexität]] in der [[Koordination]].
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer [[Schnittstelle]] in einer geschichteten [[Architektur]] (Kommunikationsprotokoll):', 'code': {'server': ['from socket import *', 's = socket(AF_INET, SOCK_STREAM)', "s.bind(('', 8080))", 's.listen(1)', '(conn, addr) = s.accept()', 'while True:', '    data = conn.recv(1024)', '    if not data: break', '    conn.send(data.upper())  # Schnittstelle: Daten empfangen/verarbeiten/senden', 'conn.close()'], 'client': ['from socket import *', 's = socket(AF_INET, SOCK_STREAM)', "s.connect(('localhost', 8080))", "s.send(b'Hello')", 'data = s.recv(1024)', 'print(data.decode())', 's.close()']}, 'erlaeuterung': 'Die [[Socket]]-Schnittstelle definiert hier die [[Methode|Methoden]] `send()` und `recv()`, die [[Datenformat|Datenformate]] (Bytes) und [[Aufrufkonvention|Aufrufkonventionen]] für die [[Kommunikation]] festlegen.'}
