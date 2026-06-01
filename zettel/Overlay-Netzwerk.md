---
id: 298ac0ba-608f-4b65-ba51-02be46d9b7f9
title: "Overlay-Netzwerk"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - architektur
  - peer-to-peer
  - kommunikation
  - overlay
  - suche
  - koordination
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Overlay-Netzwerk]]

- **Kernkonzept:** Ein [[Overlay-Netzwerk]] ist eine logische oder virtuelle [[Netzwerk|Netzwerkstruktur]], die über ein bestehendes [[physisches_Netzwerk|physisches Netzwerk]] (z. B. das Internet) gelegt wird, um spezifische [[Kommunikationsmuster|Kommunikationsmuster]] oder [[Dienst|Dienste]] in [[verteilten_Systemen|verteilten Systemen]] effizienter zu realisieren. Die [[Knoten]] kommunizieren dabei nur mit ihren direkten [[Nachbar|Nachbarn]], die dynamisch oder implizit bekannt sein können und die [[Kommunikation]] organisieren, unabhängig von der physischen [[Anordnung]].
- **Nutzen & Zweck:** Ein [[Overlay-Netzwerk]] ermöglicht die effiziente Organisation und [[Kommunikation]] in [[verteilten_Systemen|verteilten Systemen]], ohne dass alle [[Knoten]] direkt miteinander verbunden sein müssen. Dadurch löst es das Problem der [[Skalierbarkeit]] in großen [[Netzwerk|Netzwerken]] und unterstützt flexible, dezentrale Strukturen wie [[Peer-to-Peer-System|Peer-to-Peer-Systeme]]. Es bietet eine anpassbare [[Infrastruktur]] für [[Datenverteilung]], [[Suche]] oder [[Koordination]], verbessert die [[Ressourcennutzung]] und ermöglicht [[Lastverteilung]] in [[Content-Delivery-Netzwerken]]. Zudem fördert es die [[Fehlertoleranz]] durch redundante [[Kommunikationspfade|Pfade]] und entkoppelt logische [[Topologie|Topologien]] von physischen Gegebenheiten.
- **Abgrenzung & Grenzen:** Ein [[Overlay-Netzwerk]] ist nicht geeignet für [[Anwendungsfälle]], die direkte physische [[Netzwerksteuerung]] oder strenge [[Konsistenzanforderungen]] erfordern, wie z. B. in klassischen [[Datenbank|Datenbanken]]. Der zusätzliche [[Overhead]] durch die Verwaltung der [[Nachbarschaftsbeziehungen]] und die virtuelle Schicht kann die [[Performance]] beeinträchtigen, insbesondere wenn die [[Latenz]] durch mehrere [[Hop|Hops]] erhöht wird. Im Vergleich zu [[Client-Server-Architekturen]] sind komplexere [[Fehlertoleranzmechanismen]] und [[Synchronisation]] erforderlich. Zudem eignen sich hochstrukturierte [[Overlay-Netzwerke]] wie [[Verteilte_Hash-Tabellen]] nicht für alle [[Anwendungsfälle]], insbesondere wenn unstrukturierte oder zufällige [[Kommunikationsmuster]] bevorzugt werden.
- **Beispiel / Code:** Ein strukturiertes [[Overlay-Netzwerk]] ist der [[Chord-Ring]], bei dem jeder [[Knoten]] eine definierte Menge von [[Nachbar|Nachbarn]] kennt und effiziente Suchoperationen ermöglicht:

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

Ein Beispiel für ein unstrukturiertes [[Overlay-Netzwerk]] ist ein [[Peer-to-Peer-System]] mit Flooding-Suche:

1. Ein [[Knoten]] sendet eine Suchanfrage an alle [[Nachbar|Nachbarn]].
2. Jeder [[Nachbar]] prüft lokal, ob er die gesuchte Ressource besitzt.
3. Falls nicht, leitet er die Anfrage weiter (rekursiv), bis ein [[Time-To-Live]]-Wert (TTL) erreicht ist.

Pseudocode für Flooding:

```
function search(node, query, ttl):
    if ttl <= 0 or query in node.cache:
        return
    if node.has_file(query):
        return node.address
    for neighbor in node.neighbors:
        search(neighbor, query, ttl - 1)
```
