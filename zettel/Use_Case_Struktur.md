---
id: 9eca06ed-976c-4c4b-b02a-553ed34b4359
title: "Use Case Struktur"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - struktur
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Struktur]]

- **Kernkonzept:** Die 'Use Case Struktur' ist ein zentrales Konzept der objektorientierten Analyse und Modellierung, das Abläufe und Interaktionen zwischen Akteuren und einem System in Form von Use Cases systematisch beschreibt. Sie definiert Aufbau, Beziehungen und Priorisierungen von Use Cases, um Anforderungen strukturiert zu erfassen und zu dokumentieren.
- **Nutzen & Zweck:** Dieses Konzept existiert, um komplexe Anforderungen an Softwaresysteme übersichtlich und nachvollziehbar zu gliedern. Es löst das Problem, dass unstrukturierte Anforderungen zu Missverständnissen, unvollständigen Implementierungen oder architekturellen Fehlentscheidungen führen können. Durch die klare Strukturierung von Use Cases wird die Kommunikation zwischen Stakeholdern verbessert, die Architekturplanung unterstützt und die Grundlage für Tests, Implementierung und Evaluation geschaffen.
- **Abgrenzung & Grenzen:** Die Use Case Struktur sollte nicht genutzt werden, wenn es um die detaillierte Modellierung von Algorithmen, Datenstrukturen oder technischen Implementierungsdetails geht. Sie eignet sich nicht für die Darstellung zeitlicher Abfolgen von Prozessen (hierfür sind Aktivitäts- oder Sequenzdiagramme besser geeignet). Zudem ist sie keine Alternative zu User Stories im agilen Kontext, da diese oft weniger formal und flexibler sind. Use Cases sind auch ungeeignet, wenn Anforderungen extrem dynamisch oder unklar sind, da sie eine gewisse Stabilität der Anforderungen voraussetzen.
- **Beispiel / Code:** ```java
// Beispiel für die Struktur eines Use Case in textueller Form (kein Code, aber als Markdown-Format)
UseCase: "Mitglieder verwalten"
- Systemgrenze: MyClub
- Akteure: Vereinsmanager, Mail Client
- Priorität: 1 (hoch)
- Vorbedingung: MyClub ist installiert, Vereinsmanager ist authentisiert.
- Beschreibung: 
  Der Vereinsmanager kann Mitglieder anlegen, bearbeiten oder löschen.
  Bei Abteilungsänderungen werden betroffene Akteure per Mail informiert.
- Referenzen: F1.1, F1.2, F2.1
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b
- **Vorgänger / Parent:** [[Use_Case]]
- **Folgezettel / Unterzettel:**
  - [[Use_Case_Name]]
  - [[Use_Case_Akteure]]
  - [[Use_Case_Systemgrenze]]
  - [[Use_Case_Priorität]]
  - [[Use_Case_Beschreibung]]
  - [[Use_Case_Vorbedingungen]]
  - [[Use_Case_Referenzen]]
- **Querverweise:**
  - [[Use_Case]]
  - [[Modellierung]]
