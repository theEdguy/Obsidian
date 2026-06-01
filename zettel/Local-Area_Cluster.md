---
id: e7fb75c1-0b9c-48d7-83b8-f529124773b7
title: "Local-Area Cluster"
date: 2026-06-01
tags:
  - verteilte_systeme
  - server_architektur
  - lastverteilung
  - netzwerk
  - skalierbarkeit
  - hochverfügbarkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Local-Area Cluster]]

- **Kernkonzept:** Ein [[Local-Area Cluster|Local-Area-Cluster]] ist eine Gruppe eng verbundener [[Server|Server]], die in einem lokalen [[Netzwerk|Netzwerk]] (z. B. einem Rechenzentrum) zusammenarbeiten, um [[Anfrage|Anfragen]] effizient zu verteilen und [[Skalierbarkeit|skalierbare]] [[Dienst|Dienste]] bereitzustellen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Lastverteilung]] und [[Ausfallsicherheit]] in verteilten Systemen, indem es [[Ressource|Ressourcen]] bündelt und [[Anfrage|Anfragen]] dynamisch auf mehrere [[Server]] verteilt. Es ermöglicht [[Hochverfügbarkeit]] und [[Skalierbarkeit]] ohne zentrale [[Engstelle|Engpässe]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]] mit extrem niedriger [[Latenz]] oder stark zustandsbehafteten [[Dienst|Diensten]], die keine [[Replikation]] erlauben. Unterscheidet sich von [[Grid-Computing]] durch die lokale Begrenzung und von [[Cloud-Computing]] durch die physische Kontrolle über die [[Infrastruktur]].
- **Beispiel / Code:** Ein typisches Dreischicht-Modell eines [[Local-Area Cluster|Local-Area-Clusters]]:
1. **Logischer Schalter (Load Balancer)**: Verteilt [[Anfrage|Anfragen]] an verfügbare [[Server]].
2. **Application Server**: Führt die [[Berechnung|Berechnungen]] aus (z. B. Webserver).
3. **Datenbankserver**: Speichert und verwaltet [[Daten]].

Beispiel für TCP-Handoff zur Vermeidung von [[Engstelle|Engpässen]]:
```
Client → (TCP-Verbindung) → Switch → (Request-Weiterleitung) → Server A
```
Der Switch übergibt die TCP-Verbindung direkt an den [[Server]], um die Last zu verteilen.
