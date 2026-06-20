---
id: 32d6ff41-c4d1-566d-b6b1-4825476f0468
title: "Chord (Verteilte Hash-Tabelle)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Architekturen"
---

# [[Chord (Verteilte Hash-Tabelle)]]

- **Kernkonzept:** Ein strukturiertes P2P-System, bei dem Knoten und Schlüssel in einem m-Bit Ring angeordnet sind. Ein Schlüssel k wird auf dem Successor (erster Knoten mit ID >= k) gespeichert. Logarithmisches Routing wird durch Finger-Tabellen realisiert, bei denen der i-te Eintrag auf successor((n + 2^(i-1)) mod 2^m) verweist.
- **Nutzen & Zweck:** Ein strukturiertes P2P-System, bei dem Knoten und Schlüssel in einem m-Bit Ring angeordnet sind. Ein Schlüssel k wird auf dem Successor (erster Knoten mit ID >= k) gespeichert. Logarithmisches Routing wird durch Finger-Tabellen realisiert, bei denen der i-te Eintrag auf successor((n + 2^(i-1)) mod 2^m) verweist.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# Finger-Tabelle für Knoten 6 in 4-Bit Ring (m=4, 16 Positionen):
# i=1: successor((6 + 1) mod 16) = successor(7) -> 9
# i=2: successor((6 + 2) mod 16) = successor(8) -> 9
# i=3: successor((6 + 4) mod 16) = successor(10) -> 12
# i=4: successor((6 + 8) mod 16) = successor(14) -> 14
```
