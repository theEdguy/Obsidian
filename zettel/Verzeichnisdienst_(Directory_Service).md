---
id: 78bb6b4b-fbab-4821-ba3d-6e68e9bfa792
title: "Verzeichnisdienst (Directory Service)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - koordination
  - netzwerk
  - middleware
  - dienste_verwaltung
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Verzeichnisdienst (Directory Service)]]

- **Kernkonzept:** Ein [[Verzeichnisdienst|Verzeichnisdienst]] verwaltet zentralisierte Informationen über [[Ressource|Ressourcen]] in einem [[verteilte System|verteilten System]], wie z. B. [[Server]]-Standorte oder [[Dienst|Dienste]], und ermöglicht deren effiziente Lokalisierung und Zugriffskoordination.
- **Nutzen & Zweck:** Er löst das [[Problem]] der dynamischen [[Adressierung]] und [[Lokalisierung]] von [[Dienst|Diensten]] oder [[Knoten]] in [[verteilte System|verteilten Systemen]], indem er eine einheitliche Schnittstelle für die [[Suche]] und [[Registrierung]] von [[Ressource|Ressourcen]] bereitstellt. Dies reduziert manuelle Konfiguration und verbessert die [[Skalierbarkeit]] und [[Fehlertoleranz]].
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit statischen oder stark dezentralisierten Strukturen, wo der [[Overhead]] der [[Verwaltung]] eines zentralen [[Verzeichnis]]s die Vorteile überwiegt. Alternativen wie [[Peer-to-Peer]]-Netzwerke oder [[Broadcast]]-basierte [[Suche]]n können hier effizienter sein. Unterscheidet sich von [[Namensdienst|Namensdiensten]] durch erweiterte [[Metadaten]]-Unterstützung und [[Suchfunktion|Suchfunktionen]].
- **Beispiel / Code:** Im [[DCE RPC]]-Beispiel (Slide 20) wird ein [[Verzeichnisdienst]] genutzt, um die [[Bindung]] zwischen [[Client]] und [[Server]] zu ermöglichen:
1. Der [[Server]] registriert seinen [[Port]] beim [[DCE Daemon]].
2. Der [[Client]] fragt den [[Directory Server]] nach dem [[Server]]-Standort und [[Port]] ab.
3. Der [[Client]] führt den [[RPC]]-Aufruf mit den erhaltenen Informationen aus.

Pseudocode für die [[Registrierung]]:
```
// Server registriert sich beim Verzeichnisdienst
directoryService.register(serviceName, serverAddress, port);

// Client sucht nach dem Dienst
serverInfo = directoryService.lookup(serviceName);
```
