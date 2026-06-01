---
id: 1eb5bca9-598a-447c-9ebe-3f8d24f56bcf
title: "Overlay-Netzwerk"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - architektur
  - peer-to-peer
  - kommunikation
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Overlay-Netzwerk]]

- **Kernkonzept:** Ein [[Overlay-Netzwerk]] ist ein logisches oder virtuelles [[Netzwerk]], das über ein physisches [[Netzwerk]] (z. B. das Internet) gelegt wird. Die [[Knoten]] kommunizieren dabei nur mit ihren direkten [[Nachbar|Nachbarn]], die dynamisch oder implizit bekannt sein können und die [[Kommunikation]] in [[verteilten Systemen]] organisieren.
- **Nutzen & Zweck:** Es ermöglicht die effiziente Organisation und [[Kommunikation]] in [[verteilten Systemen]], ohne dass alle [[Knoten]] direkt miteinander verbunden sein müssen. Dadurch löst es das Problem der [[Skalierbarkeit]] in großen [[Netzwerk|Netzwerken]] und unterstützt flexible, dezentrale Strukturen wie [[Peer-to-Peer-System|Peer-to-Peer-Systeme]].
- **Abgrenzung & Grenzen:** Führt zu zusätzlichem Overhead bei der Verwaltung der [[Nachbarschaftsbeziehungen]] und ist nicht geeignet für Anwendungen, die direkte [[Kommunikation]] zwischen allen [[Knoten]] erfordern. Im Vergleich zu [[physischen Netzwerk|physischen Netzwerken]] kann die [[Latenz]] höher sein, da die [[Kommunikation]] über mehrere Hops erfolgen kann. Die logische Struktur unterscheidet sich grundlegend von der physischen Topologie.
- **Beispiel / Code:** Ein Beispiel für ein strukturiertes [[Overlay-Netzwerk]] ist der [[Chord-Ring]], bei dem jeder [[Knoten]] nur eine definierte Menge von [[Nachbar|Nachbarn]] kennt. Dies ermöglicht effiziente Suchoperationen:

```java
// Vereinfachte Darstellung eines Knotens im Chord-Ring
class ChordNode {
    private String nodeId;
    private Map<String, ChordNode> fingerTable; // Verweise auf Nachbarn
    
    public ChordNode findSuccessor(String key) {
        // Logik zur Suche des zuständigen Knotens
        return fingerTable.get(closestPrecedingNode(key));
    }
    
    private ChordNode closestPrecedingNode(String key) {
        // Durchsucht die Finger-Tabelle nach dem nächsten Knoten
        for (int i = fingerTable.size() - 1; i >= 0; i--) {
            if (isBetween(fingerTable.get(i).nodeId, nodeId, key)) {
                return fingerTable.get(i);
            }
        }
        return this;
    }
}
```

Ein weiteres Beispiel ist ein unstrukturiertes [[Overlay-Netzwerk]] wie in [[Peer-to-Peer-System|Peer-to-Peer-Systemen]] (z. B. BitTorrent), bei dem [[Knoten]] Dateien über zufällige oder heuristisch bestimmte [[Nachbar|Nachbarn]] austauschen.
