---
id: 29bac7b6-96ad-46a6-93a7-56f0ea7f3f18
title: "Modelle für Code Migration"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - mobilität
  - architektur
  - heterogenität
  - prozessverwaltung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Modelle für Code Migration]]

- **Kernkonzept:** Verschiedene [[Modell|Modelle]] zur [[Migration|Migration]] von [[Prozess|Prozessen]] oder [[Komponente|Komponenten]] in [[Verteiltes System|verteilten Systemen]], die bestimmen, wie [[Code-Segment|Code-Segmente]], [[Daten-Segment|Daten-Segmente]] und [[Ausführungszustand|Ausführungszustände]] zwischen [[Knoten|Knoten]] übertragen werden.
- **Nutzen & Zweck:** Ermöglicht die dynamische Verteilung von [[Berechnung|Berechnungen]] und [[Ressource|Ressourcen]] in [[Verteiltes System|verteilten Systemen]], um [[Lastverteilung|Lastverteilung]], [[Fehlertoleranz]] oder [[Latenzreduktion]] zu verbessern. Löst das [[Problem]] der statischen [[Platzierung|Platzierung]] von [[Code]] und [[Daten]] in heterogenen Umgebungen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Zielplattform|Zielplattformen]] keine kompatible [[Laufzeitumgebung]] bieten (z. B. fehlende [[Virtuelle Maschine|virtuelle Maschinen]]). Starke [[Mobilität]] ist komplex und erfordert [[Mechanismus|Mechanismen]] zur [[Serialisierung]] des [[Ausführungszustand|Ausführungszustands]]. Alternativen wie [[Remote Procedure Call|RPC]] oder [[Nachrichtenaustausch]] sind einfacher, aber weniger flexibel.
- **Beispiel / Code:** 1. **Code-on-Demand (CoD)**: Ein [[Client]] fordert [[Code]] vom [[Server]] an und führt ihn lokal aus (z. B. JavaScript in Webbrowsern).
2. **Mobile Agents (MA)**: Ein [[Agent]] migriert mit [[Code]], [[Daten]] und [[Ausführungszustand]] zum [[Server]], führt dort [[Berechnung|Berechnungen]] durch und kehrt mit [[Ergebnis|Ergebnissen]] zurück.
3. **Schwache Mobilität**: Ein [[Prozess]] wird neu gestartet, nachdem [[Code]] und [[Daten]] übertragen wurden (z. B. Java-Applets).
4. **Starke Mobilität**: Ein [[Thread]] wird inkl. [[Stack]] und [[Registerzustand]] migriert (z. B. in [[Java Aglets]] oder [[Erlang]]-Prozessen).
