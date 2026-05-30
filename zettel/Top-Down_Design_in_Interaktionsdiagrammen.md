---
id: 84a9e98f-2989-4027-8ba2-fa1853f269ef
title: "Top-Down_Design_in_Interaktionsdiagrammen"
date: 2026-05-30
tags:
  - software_engineering
  - design_prinzip
  - modellierung
  - software_architektur
  - draft
source: "SWE Slides (Folien 301-315)"
---

# [[Top-Down_Design_in_Interaktionsdiagrammen]]

- **Kernkonzept:** [[Top-Down_Design_in_Interaktionsdiagrammen|Top-Down-Design]] in [[Interaktionsdiagramm|Interaktionsdiagrammen]] beschreibt die schrittweise Verfeinerung von [[System|Systemoperationen]] von der [[Schnittstelle]] zu internen [[Komponente|Komponenten]].
- **Nutzen & Zweck:** Ermöglicht die systematische Zerlegung von [[Anforderung|Anforderungen]] in kleinere [[Teilproblem|Teilprobleme]], um die [[Komplexität]] zu reduzieren und [[Verantwortlichkeit|Verantwortlichkeiten]] klar zuzuweisen.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Bottom-Up_Design|Bottom-Up-Ansätze]], bei denen zunächst [[Komponente|Komponenten]] entwickelt und dann integriert werden. Kann zu übermäßiger [[Abstraktion]] führen, wenn zu früh verfeinert wird.
- **Beispiel / Code:** ```text
// Schritt 1: System-Sequenz-Diagramm
:Akteur -> System: executeOrder(ord)

// Schritt 2: Verfeinerung in Sequenzdiagramm
:Shop -> Order: sizeOf()
:Shop -> Order: getItem(i)
```
