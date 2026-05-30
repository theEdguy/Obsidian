---
id: 34149d92-c23b-4256-a48d-9845ebffdb71
title: "Risikomanagement"
date: 2026-05-30
tags:
  - software_engineering
  - projektmanagement
  - qualitätssicherung
  - risikoanalyse
  - softwareentwicklung
  - draft
source: "SWE Slides (Folien 31-45)"
---

# [[Risikomanagement]]

- **Kernkonzept:** [[Risikomanagement]] ist ein systematischer [[Prozess]], um [[Risiko|Risiken]] in [[Software-Projekt|Software-Projekten]] zu identifizieren, zu bewerten und zu steuern. Es ist ein zentraler Bestandteil des [[Spiralmodell|Spiralmodells]] und anderer [[iterativer_Prozessmodell|iterativer Prozessmodelle]], um [[Projektfehler|Projektfehler]] und [[Kostenüberschreitung|Kostenüberschreitungen]] zu vermeiden.
- **Nutzen & Zweck:** [[Risikomanagement]] minimiert die Wahrscheinlichkeit von [[Projektmisserfolg|Projektmisserfolgen]] und [[Fehlentwicklung|Fehlentwicklungen]] durch frühzeitige Erkennung von [[Risikofaktor|Risikofaktoren]] wie [[Komplexität]], [[Personalengpass|Personalengpässen]] oder [[Technologie-Risiko|Technologie-Risiken]]. Es ermöglicht eine fundierte [[Entscheidungsfindung]] und Priorisierung von [[Aufgabe|Aufgaben]], unterstützt die [[Qualitätssicherung]] und trägt zur Stabilität des [[Projekt|Projekts]] bei.
- **Abgrenzung & Grenzen:** [[Risikomanagement]] ist kein Ersatz für [[Qualitätssicherung]], sondern ergänzt diese durch kontinuierliche Überwachung und Anpassung. Es erfordert zusätzlichen Aufwand und ist nicht für [[Projekt|Projekte]] mit geringem [[Risiko]] oder klaren [[Anforderung|Anforderungen]] notwendig. In [[Agile_Methodik|agilen Projekten]] wird es oft durch [[Sprint_Planung|Sprint-Planung]] und [[Daily_Standup|Daily Standups]] unterstützt, kann jedoch ohne erfahrene [[Projektmanager|Projektmanager]] zu Überbewertung oder Vernachlässigung von [[Risiko|Risiken]] führen.
- **Beispiel / Code:** ```markdown
# Beispiel: Risikomanagement-Matrix
| Risiko                     | Eintrittswahrscheinlichkeit | Auswirkung | Maßnahme                          |
|----------------------------|----------------------------|------------|-----------------------------------|
| Unklare [[Anforderung|Anforderungen]]     | Hoch                       | Kritisch   | [[Prototyping]]                  |
| [[Technologie-Risiko|Technologie]] nicht beherrscht | Mittel                    | Hoch       | Schulung, [[Spike]]              |
| [[Personalengpass|Personalengpässe]]      | Niedrig                    | Mittel     | [[Ressourcenplanung]]            |

# Schritte des Risikomanagements:
1. [[Risiko|Risiken]] identifizieren
2. [[Risiko|Risiken]] bewerten (Eintrittswahrscheinlichkeit und Auswirkung)
3. Maßnahmen zur Risikobeseitigung oder -minderung planen
4. [[Risiko|Risiken]] überwachen und kontrollieren
```
