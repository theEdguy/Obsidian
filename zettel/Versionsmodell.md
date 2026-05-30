---
id: 76c403fd-6a29-4557-bac1-f86228ea8068
title: "Versionsmodell"
date: 2026-05-30
tags:
  - software_engineering
  - prozessmodell
  - softwareentwicklung
  - iterative_entwicklung
  - draft
source: "SWE Slides (Folien 31-45)"
---

# [[Versionsmodell]]

- **Kernkonzept:** Das [[Versionsmodell]] ist ein [[iteratives_Prozessmodell|iteratives Prozessmodell]], das das [[Wasserfallmodell]] in mehreren [[Version|Versionen]] durchläuft. Jede [[Version]] stellt ein funktionsfähiges [[Teilsystem]] dar, das auf dem vorherigen aufbaut und schrittweise das [[Gesamtsystem]] bildet.
- **Nutzen & Zweck:** Es ermöglicht die frühzeitige Auslieferung eines [[Kernsystem|Kernsystems]] und die Integration neuer [[Anforderung|Anforderungen]] basierend auf Feedback. [[Stakeholder]] können in die Entscheidung über die [[Versionsreihenfolge]] einbezogen werden, um kritische [[Funktionalität|Funktionalitäten]] priorisieren.
- **Abgrenzung & Grenzen:** Die Aufteilung in [[Version|Versionen]] und deren Umfang ist oft schwer zu definieren. Es erfordert eine sorgfältige Planung, um Abhängigkeiten zwischen [[Teilsystem|Teilsystemen]] zu managen. Nicht geeignet für [[Projekt|Projekte]] mit extrem kurzen [[Iteration|Iterationen]] oder hoher Dynamik in den [[Anforderung|Anforderungen]].
- **Beispiel / Code:** ```plaintext
Ablauf des Versionsmodells:
1. Planung und Analyse
2. Entwurf Version i
3. Implementierung Version i
4. Bewertung Version i
   - Wenn nicht okay: Anpassung und Wiederholung
   - Wenn okay: Nächste Version oder Auslieferung
```
