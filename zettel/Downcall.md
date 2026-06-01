---
id: 02b8e0e5-5c16-4648-821c-fb0d3d47c564
title: "Downcall"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - schichtenmodell
  - kommunikation
  - verteilte-systeme
  - software-design
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Downcall]]

- **Kernkonzept:** Ein [[Downcall]] bezeichnet in [[geschichtete Architektur|geschichteten Architekturen]] einen [[Aufruf]] von einer höheren [[Schicht]] an eine darunterliegende [[Schicht]], um [[Dienst|Dienste]] oder [[Funktionalität|Funktionalitäten]] der tieferen [[Schicht]] zu nutzen.
- **Nutzen & Zweck:** Der [[Downcall]] ermöglicht die [[Trennung von Verantwortlichkeiten]] in [[geschichtete Systeme|geschichteten Systemen]], indem höhere [[Schicht|Schichten]] auf standardisierte [[Schnittstelle|Schnittstellen]] tieferer [[Schicht|Schichten]] zugreifen. Dies fördert [[Modularität]], [[Wiederverwendbarkeit]] und [[Abstraktion]] in [[verteilte Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Ein [[Downcall]] sollte nicht genutzt werden, wenn [[bidirektionale Kommunikation]] zwischen [[Schicht|Schichten]] erforderlich ist, da er nur [[unidirektionale Aufrufe]] von oben nach unten unterstützt. Alternativen wie [[Upcall]] oder [[Event-basierte Kommunikation]] eignen sich besser für [[asynchrone]] oder [[rückwärtsgerichtete]] [[Interaktion|Interaktionen]]. In [[monolithische Systeme|monolithischen Systemen]] ohne klare [[Schichtenbildung]] ist der Einsatz ebenfalls unnötig.
- **Beispiel / Code:** In einem [[Netzwerkprotokoll]]-Stack ruft die [[Anwendungsschicht]] (z. B. HTTP) via [[Downcall]] die [[Transportschicht]] (z. B. TCP) auf, um Daten zu senden:

```
// Anwendungsschicht (HTTP)
socket.send(data); // Downcall an Transportschicht (TCP)
```

Hierbei kapselt die [[Transportschicht]] die Details des [[Datenversand|Datenversands]] und stellt eine einfache [[Schnittstelle]] bereit.
