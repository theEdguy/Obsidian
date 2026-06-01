---
id: 511a0932-1635-4dd4-af85-6f588af0ed48
title: "Schwache Mobilität"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - code-migration
  - mobilität
  - prozessverwaltung
  - heterogenität
  - software-architektur
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Schwache Mobilität]]

- **Kernkonzept:** Bei der [[schwache Mobilität|schwachen Mobilität]] werden lediglich das [[Code-Segment|Code-Segment]] und das [[Daten-Segment]] eines [[Prozess|Prozesses]] migriert, während der [[Ausführungszustand]] verworfen wird. Der [[Prozess]] startet nach der Migration neu.
- **Nutzen & Zweck:** Dieses Konzept ermöglicht die flexible Verteilung von [[Berechnung|Berechnungen]] in [[verteilte Systeme|verteilten Systemen]], ohne den komplexen [[Ausführungszustand]] übertragen zu müssen. Es löst das [[Problem]] der effizienten [[Code-Migration]] in heterogenen oder dynamischen Umgebungen, indem es [[Portabilität]] und einfache Implementierung priorisiert.
- **Abgrenzung & Grenzen:** Schwache Mobilität sollte nicht genutzt werden, wenn der [[Ausführungszustand]] eines [[Prozess|Prozesses]] erhalten bleiben muss, z. B. bei unterbrechungsfreien [[Dienst|Diensten]]. Im Gegensatz zur [[starke Mobilität|starken Mobilität]] ist sie ungeeignet für Szenarien, die [[Zustandskonsistenz]] oder [[Unterbrechungsfreiheit]] erfordern. Zudem ist sie in [[heterogene Systeme|heterogenen Systemen]] nur mit [[abstrakte Maschine|abstrakten Maschinen]] (z. B. [[Java-VM]]) praktikabel.
- **Beispiel / Code:** Ein einfaches Beispiel für schwache Mobilität ist ein [[Java-Applet]], das vom [[Server]] zum [[Client]] übertragen wird. Der [[Client]] lädt den [[Code]] (z. B. eine `.class`-Datei) und die initialen [[Daten]] (z. B. Konfigurationsparameter), führt den [[Code]] jedoch ohne vorherigen [[Ausführungszustand]] aus:

```java
// Client-seitiger Code (Code-on-Demand)
URL appletURL = new URL("http://server.example.com/Applet.class");
Applet applet = (Applet) new AppletClassLoader().loadClass(appletURL).newInstance();
applet.init(); // Neustart ohne vorherigen Zustand
```
