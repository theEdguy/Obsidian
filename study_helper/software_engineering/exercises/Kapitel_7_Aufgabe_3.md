---
id: f266df43-5c9b-593e-9781-a53bf6e63762
title: "Kapitel_7_Aufgabe_3"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - use_cases
  - include
  - extend
  - extension_point
  - exercise
  - draft
source: "Kapitel 7 Übung"
---

# Kapitel 7 Aufgabe 3

- **Aufgabenstellung:** Wann spricht man bei Use Cases von einer Extend-Beziehung und wann von einer Include-Beziehung? Was versteht man unter einem Extension Point? (6 Punkte)
- **Lösungsweg / Musterlösung:** - Include-Beziehung (2 P): Wird verwendet, wenn die Aktionen eines Use Cases (B) im Wesentlichen komplett in einen anderen Use Case (A) eingebunden werden (Wiederverwendung von Abläufen). Der aufgerufene Use Case ist zwingend erforderlich für den Ablauf des aufrufenden Use Cases.
- Extend-Beziehung (2 P): Beschreibt eine optionale Erweiterung eines Basis-Use-Cases. Der erweiternde Use Case wird nur unter bestimmten Bedingungen ausgeführt.
- Extension Point (2 P): Der konkret definierte Punkt im Ablauf des Basis-Use-Cases, an dem die Erweiterung stattfinden darf (z. B. 'nach Eingabe der PIN').
- **Theoretischer Bezug:** [[Kapitel_7__Use_Cases_erstellen_und_beschreiben]]
- **Stolpersteine / Fehlerquellen:** Verwechslung der Pfeilrichtungen: Bei <<include>> zeigt der Pfeil vom Basis-Use-Case auf den inkludierten Use Case (A -> B). Bei <<extend>> zeigt der Pfeil vom erweiternden Use Case auf den Basis-Use-Case (B -> A).
