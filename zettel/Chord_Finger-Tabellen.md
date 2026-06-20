---
id: 7b0e40fa-787b-561c-a6fb-24020f7ae243
title: "Chord Finger-Tabellen"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_5
  - draft
source: "Kapitel 5: Benennung"
---

# [[Chord Finger-Tabellen]]

- **Kernkonzept:** Um lineare Namen in einem Chord P2P-Ring effizient in O(log N) Schritten nachzuschlagen, hält jeder Knoten p eine Finger-Tabelle FT_p mit maximal m Einträgen: FT_p[i] = successor((p + 2^(i-1)) mod 2^m). Der Successor ist der kleinste Knoten-ID >= dem berechneten Wert.
- **Nutzen & Zweck:** Um lineare Namen in einem Chord P2P-Ring effizient in O(log N) Schritten nachzuschlagen, hält jeder Knoten p eine Finger-Tabelle FT_p mit maximal m Einträgen: FT_p[i] = successor((p + 2^(i-1)) mod 2^m). Der Successor ist der kleinste Knoten-ID >= dem berechneten Wert.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# i-ter Eintrag für Knoten p bei m-Bit Bezeichner:
# FT_p[i] = successor((p + 2**(i-1)) % (2**m))
```
