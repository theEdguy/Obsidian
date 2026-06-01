---
id: 020385cd-e878-4d67-be76-84e450e35d29
title: "Partitionierung eines Namensraums"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensauflösung
  - skalierbarkeit
  - dns
  - hierarchische-benennung
  - netzwerk-architektur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Partitionierung eines Namensraums]]

- **Kernkonzept:** Die Partitionierung eines [[Namensraum|Namensraums]] teilt einen hierarchischen [[Benennungsgraph|Benennungsgraphen]] in logische Ebenen (globale, administrative, managementbezogene Schichten) auf, um die [[Namensauflösung]] und Verwaltung in [[Verteilte Systeme|verteilten Systemen]] zu skalieren.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] in großen [[Namensraum|Namensräumen]], indem es die Last auf mehrere [[Server]] verteilt, die Reaktionszeiten verbessert und die [[Administration]] durch klare Verantwortungsbereiche vereinfacht. Es ermöglicht effiziente [[Namensauflösung]] in globalen Systemen wie DNS.
- **Abgrenzung & Grenzen:** Nicht geeignet für kleine, lokale Systeme mit geringer Komplexität, da der Overhead der Partitionierung und Koordination den Nutzen übersteigt. Alternativen wie flache [[Benennung]] oder zentrale [[Namensauflösung]] sind hier effizienter. Zudem erfordert die Partitionierung zusätzliche Mechanismen zur Synchronisation und Replikation, was die Komplexität erhöht.
- **Beispiel / Code:** Ein DNS-Beispiel zeigt die Partitionierung:
- **Globale Schicht**: Root-Server (z. B. `.com`, `.org`).
- **Administrationsschicht**: Organisationsebene (z. B. `example.com`).
- **Managementschicht**: Lokale Server (z. B. `ftp.example.com`).

Iterative Auflösung:
1. Client fragt Root-Server nach `ftp.example.com`.
2. Root verweist auf `.com`-Server.
3. `.com`-Server verweist auf `example.com`-Server.
4. `example.com`-Server liefert IP-Adresse von `ftp.example.com`.
