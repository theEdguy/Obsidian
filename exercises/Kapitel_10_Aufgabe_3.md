---
id: fe21224a-db3d-579d-a245-98ed1aaf733e
title: "Kapitel_10_Aufgabe_3"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - komponentendiagramm
  - ports
  - assembly
  - exercise
  - draft
source: "Kapitel 10 Übung"
---

# Kapitel 10 Aufgabe 3

- **Aufgabenstellung:** Skizzieren Sie ein Komponentendiagramm zu folgender Beschreibung:
Eine Komponente A verfügt über zwei Ports B und C. Am Port B stellt sie die Interfaces D und E bereit. Am Port C benötigt sie das Interface F, welches von einer Komponente G am Port H bereitgestellt wird.
- **Lösungsweg / Musterlösung:** Das Diagramm besteht aus:
1. Einer Komponente `A` mit zwei quadratischen Ports `B` und `C` an den Rändern.
2. Am Port `B` sind zwei Lollipops (Kreise) angebracht, beschriftet mit den bereitgestellten Schnittstellen (interfaces) `D` und `E`.
3. Am Port `C` ist eine Halbschale (Socket) für das benötigte Interface `F` angebracht.
4. Einer Komponente `G` mit einem Port `H` und einem Lollipop für `F`.
5. Einem Assembly Connector (Zusammenführung von Lollipop und Halbschale) zwischen Port `C` (A) und Port `H` (G).
- **Theoretischer Bezug:** [[Kapitel_10__Von_der_Analyse_zur_Systemarchitektur]]
- **Stolpersteine / Fehlerquellen:** Verwechslung von Lollipop (bereitgestellt / provided) und Socket (benötigt / required). Falsche Darstellung von Ports (sie müssen als kleine Quadrate auf der Systemgrenze der Komponente gezeichnet werden).
