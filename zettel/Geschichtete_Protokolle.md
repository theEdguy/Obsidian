---
id: 689de460-c14c-46ab-ade0-f86413f2d9a7
title: "Geschichtete Protokolle"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - architektur
  - protokoll
  - schichtenmodell
  - verteilte-systeme
  - osi-modell
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Geschichtete Protokolle]]

- **Kernkonzept:** Geschichtete Protokolle organisieren die [[Kommunikation]] in [[Verteilte Systeme|verteilten Systemen]] durch hierarchische [[Schicht|Schichten]], die jeweils spezifische [[Funktion|Funktionen]] übernehmen und so die Komplexität der [[Nachrichtenübertragung]] reduzieren.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der heterogenen und komplexen [[Kommunikation]] in [[Netzwerk|Netzwerken]], indem es durch klare [[Schnittstelle|Schnittstellen]] und [[Abstraktion]] die [[Interoperabilität]] zwischen verschiedenen [[System|Systemen]] ermöglicht und die [[Wartbarkeit]] sowie [[Erweiterbarkeit]] verbessert.
- **Abgrenzung & Grenzen:** Geschichtete Protokolle sind nicht geeignet, wenn [[Echtzeitanforderung|Echtzeitanforderungen]] oder minimale [[Latenz]] priorisiert werden, da jede [[Schicht]] zusätzlichen [[Overhead]] verursacht. Alternativen wie [[Monolithische Architektur|monolithische Protokolle]] oder [[Peer-to-Peer-Kommunikation]] können hier effizienter sein. Zudem kann die strikte [[Schichtenarchitektur]] die [[Zugriffstransparenz]] verletzen, wenn [[Middleware]] oder [[Betriebssystem]]-spezifische [[Funktion|Funktionen]] unnötig eingebunden werden.
- **Beispiel / Code:** Ein klassisches Beispiel ist das **OSI-Referenzmodell** mit sieben [[Schicht|Schichten]]:\n\n1. **Bitübertragungsschicht (Physical Layer)**: Definiert die physikalische Übertragung von Bits (z. B. Ethernet-Kabel).\n2. **Sicherungsschicht (Data Link Layer)**: Organisiert Frames und Fehlererkennung (z. B. MAC-Adressen).\n3. **Vermittlungsschicht (Network Layer)**: Routing von Paketen (z. B. IP-Protokoll).\n4. **Transportschicht (Transport Layer)**: Ende-zu-Ende-Kommunikation (z. B. TCP für verlässliche Übertragung).\n5. **Sitzungsschicht (Session Layer)**: Verwaltung von Sitzungen (z. B. RPC).\n6. **Darstellungsschicht (Presentation Layer)**: Datenkonvertierung (z. B. SSL/TLS-Verschlüsselung).\n7. **Anwendungsschicht (Application Layer)**: Anwendungsprotokolle (z. B. HTTP).\n\n**TCP/IP-Beispiel (abgewandeltes Modell)**:\n```\nAnwendung (HTTP, FTP) → Transport (TCP/UDP) → Internet (IP) → Netzwerkzugriff (Ethernet)\n```
