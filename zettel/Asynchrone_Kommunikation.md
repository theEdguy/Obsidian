---
id: 31371ac4-ad61-4dc5-91f6-fc75c01d04ea
title: "Asynchrone Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - netzwerk
  - performance
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Asynchrone Kommunikation]]

- **Kernkonzept:** Ein [[Kommunikationsmodell]] in [[verteilten Systemen]], bei dem [[Sender]] und [[Empfänger]] nicht gleichzeitig aktiv sein müssen und Nachrichten zwischengespeichert werden.
- **Nutzen & Zweck:** Reduziert die Abhängigkeit von [[Netzwerk]]-Latenzen und ermöglicht robustere Kommunikation, da [[Empfänger]] Nachrichten verarbeiten können, wenn sie verfügbar sind.
- **Abgrenzung & Grenzen:** Nicht geeignet für Anwendungen, die sofortige Antworten erfordern (z. B. Echtzeit-Systeme). Erfordert Mechanismen zur [[Pufferung]] und [[Fehlerbehandlung]].
- **Beispiel / Code:** Ein E-Mail-System, bei dem Nachrichten asynchron zwischen Servern übertragen und vom Empfänger abgerufen werden, wenn dieser online ist.
