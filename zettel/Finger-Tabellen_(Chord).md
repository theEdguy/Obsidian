---
id: 1a69615d-c4a3-4a46-b45d-b36f1bb5395d
title: "Finger-Tabellen (Chord)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - benennung
  - dht
  - chord
  - peer-to-peer
  - skalierbarkeit
  - algorithmus
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Finger-Tabellen (Chord)]]

- **Kernkonzept:** Finger-Tabellen sind eine Datenstruktur im [[Chord-Protokoll|Chord-Protokoll]], die die effiziente [[Auflösung|Auflösung]] von [[Bezeichner|Bezeichnern]] in einem verteilten [[Hash-Tabelle|Hash-Tabellen]]-System ermöglicht. Jeder [[Knoten]] speichert Referenzen auf andere Knoten in exponentiell wachsenden Abständen, um die Suche zu beschleunigen.
- **Nutzen & Zweck:** Finger-Tabellen lösen das Problem der skalierbaren [[Namensauflösung]] in verteilten Systemen mit flachen [[Bezeichner|Bezeichnern]]. Sie reduzieren die Suchkomplexität von O(N) auf O(log N) in einem [[Chord-Ring|Chord-Ring]] mit N Knoten, indem sie gezielte Sprünge im [[Adressraum]] ermöglichen.
- **Abgrenzung & Grenzen:** Finger-Tabellen sind ungeeignet für Systeme mit häufigen Knotenausfällen oder dynamischen Topologien ohne zusätzliche Stabilisierungsmechanismen. Alternativen wie [[Broadcasting]] oder [[heima|heimatbasierte]] Ansätze skalieren schlechter, während hierarchische Systeme (z. B. [[DNS]]) besser für strukturierte [[Namen]] geeignet sind. Chord eignet sich primär für [[P2P-Systeme|P2P-Systeme]] mit stabilen Knoten.
- **Beispiel / Code:** Gegeben ein Chord-Ring mit m=5 Bit (Adressraum 0–31) und Knoten 1:
Finger-Tabelle für Knoten 1 (FT₁[i] = succ(1 + 2⁽ⁱ⁻¹⁾)):
- FT₁[1] = succ(1 + 1) = 3
- FT₁[2] = succ(1 + 2) = 4
- FT₁[3] = succ(1 + 4) = 9
- FT₁[4] = succ(1 + 8) = 18
- FT₁[5] = succ(1 + 16) = 1

Suche nach Schlüssel 26:
1. Knoten 1 leitet Anfrage an FT₁[5] = 1 weiter (da 1 ≤ 26 < 1 + 16).
2. Knoten 1 erkennt, dass 26 > FT₁[1] = 3, leitet an Knoten 3 weiter.
3. Knoten 3 leitet an FT₃[4] = 20 weiter (da 20 ≤ 26 < 28).
4. Knoten 20 leitet an FT₂₀[2] = 28 weiter (da 26 < 28).
5. Knoten 28 erkennt, dass succ(26) = 30 ist und gibt diesen zurück.
