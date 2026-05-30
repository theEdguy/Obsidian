---
id: 2687a9b1-2e8f-4e6d-895f-5a096acb483d
title: "Objektidentität"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - datenmodellierung
  - draft
source: "SWE Slides (Folien 61-75)"
---

# [[Objektidentität]]

- **Kernkonzept:** [[Objektidentität]] bezeichnet die eindeutige Existenz eines [[Objekt|Objekts]] unabhängig von seinen [[Attribut|Attributwerten]]. Zwei [[Objekt|Objekte]] mit identischen [[Attribut|Attributwerten]] sind nicht dasselbe [[Objekt]], solange sie unterschiedliche [[Identität|Identitäten]] besitzen.
- **Nutzen & Zweck:** Sie löst das Problem der [[Referenzierung]] und [[Vergleichbarkeit]] von [[Objekt|Objekten]] in [[Objektorientierte_Programmierung|objektorientierten Systemen]], insbesondere bei [[Datenbank]]-Anbindungen oder [[Verteilte_Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Nicht relevant in [[Funktionale_Programmierung|funktionalen Programmiersprachen]], wo [[Objekt|Objekte]] unveränderlich sind. Kann zu [[Performance]]-Problemen führen, wenn [[Identität|Identitätsvergleiche]] häufig durchgeführt werden (z. B. in [[Schleifen]]).
- **Beispiel / Code:** ```java
String x = new String("Hallo");
String y = new String("Hallo");

// Identitätsvergleich (false)
System.out.println(x == y);

// Wertevergleich (true)
System.out.println(x.equals(y));
```
