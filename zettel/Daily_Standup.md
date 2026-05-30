---
id: 84ededc1-330b-4551-986f-39056ba5b609
title: "Daily_Standup"
date: 2026-05-30
tags:
  - software_engineering
  - agile_methoden
  - scrum
  - teamkoordination
  - projektmanagement
  - draft
source: "Klausur_Referenz"
---

# [[Daily_Standup]]

- **Kernkonzept:** Das **Daily_Standup** (auch *Daily Scrum* genannt) ist ein kurzes, tägliches Synchronisationsmeeting im Rahmen agiler Softwareentwicklung, insbesondere in [[Scrum]]. Es dient dazu, den Fortschritt des Teams zu koordinieren, Hindernisse frühzeitig zu identifizieren und die Zusammenarbeit zu fördern. Typischerweise dauert es maximal 15 Minuten und folgt einer strukturierten Form: Jedes Teammitglied beantwortet drei Fragen: 1) Was habe ich seit dem letzten Standup erreicht? 2) Was plane ich bis zum nächsten Standup zu tun? 3) Welche Hindernisse blockieren mich?
- **Nutzen & Zweck:** Der Hauptzweck des **Daily_Standups** ist die Transparenz über den Projektfortschritt und die schnelle Erkennung von Blockaden. Es fördert die Selbstorganisation des Teams, reduziert Kommunikationslücken und ermöglicht eine flexible Anpassung der [[Sprint_Planung]]. Durch die tägliche Kürze bleibt der Fokus auf wesentlichen Punkten, ohne den Arbeitsfluss zu unterbrechen. Zudem stärkt es die Teamdynamik, da alle Mitglieder regelmäßig über den Stand der anderen informiert sind.
- **Abgrenzung & Grenzen:** Das **Daily_Standup** ist **kein** Statusmeeting für Vorgesetzte oder ein Forum zur Problemlösung. Es sollte nicht für detaillierte Diskussionen genutzt werden – diese werden separat geführt. Typische Stolpersteine sind: 1) Zu lange Dauer durch Abschweifungen, 2) Fehlende Vorbereitung der Teilnehmer, 3) Fokus auf Einzelpersonen statt auf Teamzielen. Im Gegensatz zu klassischen [[Projektmeetings]] ist es zeitlich strikt begrenzt und folgt einem festen Ablauf. Es ersetzt keine [[Retrospektive]] oder [[Refinement_Session]], die tiefergehende Analysen ermöglichen.
- **Beispiel / Code:** ```mermaid
sequenceDiagram
    participant Teammitglied_A
    participant Teammitglied_B
    participant Scrum_Master
    
    Teammitglied_A->>Scrum_Master: Gestern: API-Endpoint implementiert. Heute: Tests schreiben. Blockade: Keine.
    Teammitglied_B->>Scrum_Master: Gestern: UI-Design finalisiert. Heute: Integration mit Backend. Blockade: Fehlende Dokumentation.
    Scrum_Master->>Teammitglied_B: Dokumentation wird nach dem Standup geklärt.
```
