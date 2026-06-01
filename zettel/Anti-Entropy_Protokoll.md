---
id: 66a2da9d-8305-4eec-a06c-24c0d8479921
title: "Anti-Entropy Protokoll"
date: 2026-06-01
tags:
  - verteilte_systeme
  - replikation
  - konsistenz
  - epidemische_protokolle
  - skalierbarkeit
  - fehlertoleranz
  - datenverteilung
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Anti-Entropy Protokoll]]

- **Kernkonzept:** Ein [[epidemisches_Protokoll|epidemisches Protokoll]], das in [[verteilte_Systeme|verteilten Systemen]] zur Konsistenzsicherung von [[Replikat|Replikaten]] dient, indem [[Knoten|Knoten]] regelmäßig Zustandsänderungen mit zufällig ausgewählten [[Nachbar|Nachbarn]] austauschen, um schlussendlich identische Zustände zu erreichen.
- **Nutzen & Zweck:** Löst das Problem der [[Datenkonsistenz|Dateninkonsistenz]] in [[verteilte_Systeme|verteilten Systemen]] mit vielen [[Replikat|Replikaten]], indem es eine skalierbare und fehlertolerante Methode zur schlussendlichen Synchronisation bietet, ohne auf zentrale Koordination oder sofortige Propagierung angewiesen zu sein.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit strikten [[Konsistenzanforderung|Konsistenzanforderungen]] (z. B. [[ACID-Transaktion|ACID-Transaktionen]]), da es nur [[eventuelle_Konsistenz|eventuelle Konsistenz]] garantiert. Unterscheidet sich von [[Gossip-Protokoll|Gossip-Protokollen]] durch den bidirektionalen Austausch (Push-Pull) statt unidirektionaler Propagierung. Alternativen wie [[2-Phasen-Commit|2-Phasen-Commit]] oder [[Paxos]] bieten stärkere Konsistenzgarantien, sind aber weniger skalierbar.
- **Beispiel / Code:** Pseudocode für Anti-Entropy-Austausch zwischen zwei Knoten A und B:

```
// Knoten A initiiert Anti-Entropy mit Knoten B
function antiEntropy(A, B):
    // A sendet seinen aktuellen Zustand (z. B. Versionsvektor) an B
    state_A = A.getState()
    B.receiveState(state_A)
    
    // B vergleicht und sendet Differenzen zurück
    diff_B = B.computeDifferences(state_A)
    A.receiveDifferences(diff_B)
    
    // A aktualisiert seinen Zustand
    A.applyDifferences(diff_B)
    
    // B aktualisiert seinen Zustand mit A's Differenzen
    diff_A = A.computeDifferences(B.getState())
    B.applyDifferences(diff_A)
```

*Anmerkung: In der Praxis werden oft [[Merkle-Baum|Merkle-Bäume]] zur effizienten Erkennung von Differenzen genutzt.*
