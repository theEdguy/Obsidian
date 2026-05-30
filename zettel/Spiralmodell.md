---
id: ae6544fa-3edb-4078-a486-b72ca2edfe30
title: "Spiralmodell"
date: 2026-05-30
tags:
  - software_engineering
  - prozessmodell
  - risikomanagement
  - softwareentwicklung
  - iterative_entwicklung
  - vorgehensmodell
  - software_process
  - projektmanagement
  - draft
source: "SWE Slides (Folien 376-388)"
---

# [[Spiralmodell]]

- **Kernkonzept:** Das [[Spiralmodell]] ist ein [[iteratives_Prozessmodell|iteratives]] [[Vorgehensmodell]] in der [[Softwareentwicklung]], das [[Risikomanagement]] in den Mittelpunkt stellt und aus mehreren [[Spiralzyklus|Spiralzyklen]] besteht. Jeder [[Spiralzyklus]] durchläuft vier [[Phase|Phasen]]: [[Zielbestimmung]], [[Risikoanalyse]], [[Entwicklung]] und [[Verifikation]] sowie [[Planung]] der nächsten [[Iteration]]. Dabei werden [[Ziel|Ziele]], [[Alternative|Alternativen]] und [[Risiko|Risiken]] systematisch evaluiert, um ein [[Inkrement]] des [[System|Systems]] zu liefern und [[Unsicherheit|Unsicherheiten]] frühzeitig zu adressieren.
- **Nutzen & Zweck:** Das [[Spiralmodell]] ermöglicht die frühzeitige Identifikation und Beseitigung von [[Risiko|Risiken]] in [[Projekt|Projekten]] mit hoher [[Unsicherheit]] oder [[Komplexität]]. Es löst die Starrheit [[sequenzielles_Prozessmodell|sequenzieller Prozessmodelle]] wie dem [[Wasserfallmodell]] durch iterative [[Risikobewertung]] und [[Anpassung]] der [[Anforderung|Anforderungen]]. Durch die schrittweise Verfeinerung von [[Anforderung|Anforderungen]], die Entwicklung und das Testen von [[Prototyp|Prototypen]] sowie die kontinuierliche [[Risikominimierung]] eignet es sich besonders für [[Projekt|Projekte]] mit dynamischen oder unvollständig definierten [[Anforderung|Anforderungen]]. Es ist ideal für innovative [[Projekt|Projekte]] oder solche mit hohen [[Unsicherheit|Unsicherheiten]], da es Flexibilität und systematische [[Risikoanalyse]] kombiniert, um große [[Investition|Investitionen]] erst nach erfolgreicher [[Evaluierung]] zu tätigen.
- **Abgrenzung & Grenzen:** Das [[Spiralmodell]] ist komplexer und aufwendiger als [[sequenzielles_Prozessmodell|sequenzielle Prozessmodelle]] wie das [[Wasserfallmodell]] und erfordert erfahrene [[Projektmanager|Projektmanager]] für das [[Risikomanagement]]. Es ist nicht geeignet für kleine [[Projekt|Projekte]] mit klaren [[Anforderung|Anforderungen]] oder geringem [[Risiko]], da der [[Aufwand]] für iterative [[Risikoanalyse|Risikoanalysen]] unverhältnismäßig hoch sein kann. Im Vergleich zu [[Agile_Methoden|agilen Methoden]] wie [[Scrum]] oder [[Kanban]] liegt der Fokus stärker auf der expliziten [[Risikoanalyse]] und weniger auf flexibler [[Anpassung]] an sich ändernde [[Anforderung|Anforderungen]]. Im Gegensatz zum [[Rational_Unified_Process|RUP]] ist es weniger formalisiert und bietet mehr Freiraum für projektspezifische Anpassungen, was sowohl Vor- als auch Nachteile mit sich bringen kann. Für [[Projekt|Projekte]] mit stabilen [[Kontext|Kontexten]] oder geringem [[Overhead]]-Bedarf können Alternativen wie das [[Wasserfallmodell]] oder [[Agile_Entwicklung|agile Ansätze]] besser geeignet sein.
- **Beispiel / Code:** ```plaintext
Phasen eines Spiralzyklus:
1. [[Zielbestimmung|Ziele]], [[Alternative|Alternativen]] und [[Beschränkung|Beschränkungen]] bestimmen
2. [[Alternative|Alternativen]] evaluieren, [[Risiko|Risiken]] identifizieren und beseitigen ([[Risikoanalyse]])
3. [[Produkt]] entwickeln und verifizieren ([[Entwicklung]] und [[Verifikation]])
4. Nächste [[Iteration]] planen ([[Planung]] und [[Evaluierung]])

Beispielhafter Ablauf mehrerer Iterationen:
Iteration 1:
- [[Ziel|Ziele]] definieren
- [[Risiko|Risiken]] identifizieren
- [[Prototyp]] entwickeln und testen
- Evaluieren

Iteration 2:
- [[Ziel|Ziele]] verfeinern
- [[Risiko|Risiken]] neu bewerten
- [[System]] erweitern (nächstes [[Inkrement]])
- Evaluieren und nächste [[Iteration]] planen
```
