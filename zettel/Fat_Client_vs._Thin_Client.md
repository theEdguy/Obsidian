---
id: a78d73ed-0f41-48f1-9877-12b7c0f550a6
title: "Fat Client vs. Thin Client"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - client-server
  - verteilte-systeme
  - middleware
  - lastverteilung
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Fat Client vs. Thin Client]]

- **Kernkonzept:** In [[Verteilte Systeme|verteilten Systemen]] beschreibt der Begriffspaar Fat Client und Thin Client die Verteilung von [[Logik|Logiken]] und [[Datenverarbeitung|Datenverarbeitungen]] zwischen [[Client|Clients]] und [[Server|Servern]]. Ein Fat Client übernimmt dabei einen Großteil der [[Verarbeitung|Verarbeitungen]], während ein Thin Client primär die [[Benutzeroberfläche|Benutzeroberflächen]] darstellt und die [[Verarbeitung|Verarbeitungen]] dem [[Server]] überlässt.
- **Nutzen & Zweck:** Das Konzept löst das Problem der [[Skalierbarkeit|Skalierbarkeiten]] und [[Lastverteilung|Lastverteilungen]] in [[Client-Server-Architekturen|Client-Server-Architekturen]]. Fat Clients reduzieren die [[Serverlast|Serverlasten]], indem sie lokale [[Verarbeitung|Verarbeitungen]] durchführen, während Thin Clients die [[Wartbarkeit|Wartbarkeiten]] und [[Zentralisierung|Zentralisierungen]] von [[Logik|Logiken]] erleichtern, da Änderungen nur auf dem [[Server]] vorgenommen werden müssen.
- **Abgrenzung & Grenzen:** Fat Clients sind weniger geeignet für [[Umgebungen|Umgebungen]] mit begrenzten [[Client-Ressourcen|Client-Ressourcen]] (z. B. mobile Geräte) oder wenn eine hohe [[Synchronisation|Synchronisation]] mit zentralen [[Daten|Daten]] erforderlich ist. Thin Clients eignen sich nicht für [[Anwendungen|Anwendungen]] mit hohen [[Offline-Anforderungen|Offline-Anforderungen]] oder wenn die [[Netzwerkverbindung|Netzwerkverbindungen]] unzuverlässig sind. Alternativen wie [[Peer-to-Peer-Systeme|Peer-to-Peer-Systeme]] oder [[hybride Architekturen|hybride Architekturen]] können hier besser passen.
- **Beispiel / Code:** Beispiel für eine Telefonauskunft als verteiltes System:

**Variante 1 (Fat Client, Zweischicht-Architektur):**
- R1 (Smartphone): [[Benutzeroberfläche|Benutzeroberfläche]] + [[Anwendung|Anwendung]] (z. B. Suche und Filterung)
- R4 (Datenbankserver): [[Datenbank|Datenbank]]

**Variante 2 (Thin Client, Dreischicht-Architektur):**
- R1 (Smartphone): [[Benutzeroberfläche|Benutzeroberfläche]]
- R3 (Webserver): [[Anwendung|Anwendung]] (z. B. Suche und Filterung)
- R4 (Datenbankserver): [[Datenbank|Datenbank]]
