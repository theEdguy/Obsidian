---
id: 3dac2f8d-085d-40f4-9c05-30c7848a9831
title: "Migration (von Objekten)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - mobilitaet
  - code-migration
  - lastverteilung
  - heterogenitaet
  - abstrakte-maschine
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Migration (von Objekten)]]

- **Kernkonzept:** Die [[Migration|Migration]] (von [[Objekt|Objekten]]) bezeichnet das Verschieben eines [[Ausführungszustand|ausführbaren]] [[Komponente|Komponenten]]-Segments – bestehend aus [[Code-Segment|Code]], [[Daten-Segment|Daten]] und ggf. [[Ausführungszustand|Ausführungszustand]] – zwischen [[Knoten|Knoten]] in [[Verteiltes System|verteilten Systemen]]. Sie ermöglicht dynamische Lastverteilung oder [[Ressourcen|Ressourcen]]-Optimierung.
- **Nutzen & Zweck:** Das Konzept löst [[Problem|Probleme]] der [[Skalierbarkeit]], [[Lastverteilung]] und [[Effizienz]] in [[Verteiltes System|verteilten Systemen]], indem es [[Berechnung|Berechnungen]] näher an [[Daten]] oder [[Ressource|Ressourcen]] verlagert. Es reduziert [[Netzwerk]]-Latenz und ermöglicht [[Adaption|adaptive]] Systeme, z. B. durch [[Code-on-Demand]] oder [[Mobile Agent|mobile Agenten]].
- **Abgrenzung & Grenzen:** Nicht geeignet bei [[Heterogenität|heterogenen]] Systemen ohne [[Abstrakte Maschine|abstrakte Maschinen]] (z. B. [[VM]]), da [[Ausführungszustand|Ausführungszustände]] plattformabhängig sind. Alternativen wie [[Remote Procedure Call|RPC]] oder [[Nachricht|nachrichtenbasierte]] Kommunikation sind einfacher, aber weniger flexibel. [[Starke Mobilität]] erfordert komplexe [[Synchronisation]], während [[Schwache Mobilität]] nur [[Neustart|Neustarts]] erlaubt.
- **Beispiel / Code:** // Beispiel: Schwache Mobilität in Java (Code-on-Demand)
// Client lädt Code dynamisch vom Server und führt ihn lokal aus.
Class<?> remoteClass = RMIClassLoader.loadClass("http://server/code.jar", "RemoteTask");
Runnable task = (Runnable) remoteClass.newInstance();
task.run(); // Ausführung mit lokalem Daten-Segment, aber ohne Ausführungszustand.

// Beispiel: Starke Mobilität (hypothetisch)
// Migration eines mobilen Agenten mit gespeichertem Stack und Programmzähler.
Agent agent = new Agent();
agent.migrateTo("targetNode"); // Überträgt Code, Daten *und* Ausführungszustand.
