---
id: e81f5bc5-36b2-4ae1-8f06-7600220b6c25
title: "Server Cluster"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - server-architektur
  - lastverteilung
  - skalierbarkeit
  - hochverfuegbarkeit
  - netzwerk
  - koordination
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Server Cluster]]

- **Kernkonzept:** Ein [[Server Cluster|Server-Cluster]] ist eine Gruppe von [[Server|Servern]], die zusammenarbeiten, um hohe Verfügbarkeit, Skalierbarkeit und Lastverteilung in [[verteilte Systeme|verteilten Systemen]] zu gewährleisten. Die [[Anfrage|Anfragen]] werden durch einen logischen [[Schalter]] an die passenden [[Server]] weitergeleitet.
- **Nutzen & Zweck:** Ein [[Server Cluster|Server-Cluster]] löst das Problem der [[Skalierbarkeit]] und [[Ausfallsicherheit]] in [[verteilte Systeme|verteilten Systemen]], indem er [[Lastverteilung]] ermöglicht und [[Engpässe]] reduziert. Er sorgt für [[Verfügbarkeit]] auch bei [[Ausfall|Ausfällen]] einzelner [[Komponente|Komponenten]] und verbessert die [[Performanz]] durch parallele [[Anfrage|Anfrageverarbeitung]].
- **Abgrenzung & Grenzen:** Ein [[Server Cluster|Server-Cluster]] sollte nicht genutzt werden, wenn die [[Anwendung]] keine hohe [[Verfügbarkeit]] oder [[Skalierbarkeit]] benötigt, da der [[Aufwand]] für [[Koordination]] und [[Verwaltung]] unnötig hoch wäre. Alternativen wie einzelne [[Server]] oder [[Load Balancer]] ohne Cluster-Struktur sind einfacher zu implementieren, bieten aber keine [[Fehlertoleranz]] oder [[Lastverteilung]] auf gleichem Niveau. Bei [[zustandsbehaftete Server|zustandsbehafteten Servern]] kann die [[Komplexität]] der [[Synchronisation]] problematisch sein.
- **Beispiel / Code:** Ein typisches Dreischicht-Modell eines [[Server Cluster|Server-Clusters]] besteht aus:
1. **Logischer Schalter (Load Balancer)**: Verteilt [[Anfrage|Anfragen]] an die [[Server]] der zweiten Schicht.
2. **Application/Compute Server**: Führt die [[Berechnung|Berechnungen]] durch und leitet [[Datenbankanfrage|Datenbankanfragen]] an die dritte Schicht weiter.
3. **Datenbank/Datei-Server**: Verwaltet persistente [[Daten]].

Beispiel für TCP-Handoff zur Vermeidung von [[Engpässe|Engpässen]]:
```
Client → [Request] → Logischer Schalter → [TCP-Handoff] → Application Server → [Response] → Client
```
Hierbei wird die TCP-Verbindung direkt an den [[Server]] übergeben, der die [[Anfrage]] bearbeitet, um den [[Schalter]] zu entlasten.
