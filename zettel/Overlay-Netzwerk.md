---
id: 2fdc3851-ed08-4e38-925d-c370c56cc46c
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
  - multicast
  - routing
  - middleware
  - nachrichtenorientierte-kommunikation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Overlay-Netzwerk]]

- **Kernkonzept:** Ein [[Overlay-Netzwerk]] ist eine logische oder virtuelle [[Netzwerk|Netzwerkstruktur]], die über ein bestehendes [[physisches_Netzwerk|physisches Netzwerk]] (z. B. das Internet) gelegt wird, um spezifische [[Kommunikationsmuster|Kommunikationsmuster]] wie [[Multicast|Multicasts]], [[Routing|Routings]] oder [[Dienst|Dienste]] in [[verteilten_Systemen|verteilten Systemen]] effizienter zu realisieren. Die [[Knoten]] kommunizieren dabei nur mit ihren direkten [[Nachbar|Nachbarn]], die dynamisch oder implizit bekannt sein können, und organisieren die [[Kommunikation]] unabhängig von der physischen [[Anordnung]].
- **Nutzen & Zweck:** Ein [[Overlay-Netzwerk]] ermöglicht die effiziente Organisation und [[Kommunikation]] in [[verteilten_Systemen|verteilten Systemen]], ohne dass alle [[Knoten]] direkt miteinander verbunden sein müssen. Es löst das [[Problem]] der [[Skalierbarkeit]] in großen [[Netzwerk|Netzwerken]] und unterstützt flexible, dezentrale Strukturen wie [[Peer-to-Peer-System|Peer-to-Peer-Systeme]]. Durch die Abstraktion der logischen [[Topologie|Topologie]] von der physischen Infrastruktur ermöglicht es anwendungsspezifische [[Datenverteilung|Datenverbreitungen]], verbessert die [[Ressourcennutzung]] und fördert [[Lastverteilung]] in [[Content-Delivery-Netzwerken]]. Zudem unterstützt es komplexe [[Kommunikationsmuster|Kommunikationsmuster]] wie [[Multicast|Multicasting]] oder [[Publish-Subscribe-Systeme|Publish-Subscribe-Mechanismen]], die in physischen [[Netzwerk|Netzwerken]] oft ineffizient oder nicht nativ unterstützt werden. Overlay-Netzwerke sind besonders nützlich in [[Message-Queuing-System|nachrichtenorientierten Systemen]] oder [[Middleware|Middleware-Lösungen]], wo sie [[Fehlertoleranz]] durch redundante [[Kommunikationspfade|Pfade]] und [[Entkopplung]] von logischen und physischen Strukturen bieten.
- **Abgrenzung & Grenzen:** Ein [[Overlay-Netzwerk]] ist nicht geeignet für [[Anwendungsfälle]], die direkte physische [[Netzwerksteuerung]], niedrige [[Latenz]] oder strenge [[Konsistenzanforderungen]] erfordern, wie z. B. in klassischen [[Datenbank|Datenbanken]] oder [[Echtzeit-Systemen]]. Der zusätzliche [[Overhead]] durch die Verwaltung der [[Nachbarschaftsbeziehungen]] und die virtuelle Schicht kann die [[Performance]] beeinträchtigen, insbesondere wenn die [[Latenz]] durch mehrere [[Hop|Hops]] erhöht wird oder [[Link Stress]] und [[Stretch]] auftreten. Im Vergleich zu [[Client-Server-Architekturen]] oder nativen [[IP-Multicast|Multicast-Lösungen]] sind komplexere [[Fehlertoleranzmechanismen]] und [[Synchronisation]] erforderlich. Hochstrukturierte [[Overlay-Netzwerke]] wie [[Verteilte_Hash-Tabellen]] eignen sich nicht für alle [[Anwendungsfälle]], insbesondere wenn unstrukturierte oder zufällige [[Kommunikationsmuster]] bevorzugt werden. Zudem erfordern Overlay-Netzwerke oft manuelle Konfiguration (z. B. [[Routing-Tabelle|Routing-Tabellen]] in [[IBM MQ]]) und sind schwieriger zu verwalten als physische [[Netzwerk|Netzwerkinfrastrukturen]].
- **Beispiel / Code:** ```java
// Beispiel 1: Vereinfachte Darstellung eines Knotens im Chord-Ring (strukturiertes Overlay-Netzwerk)
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

// Beispiel 2: Baum-basiertes Multicasting in einem Overlay-Netzwerk (ALM mit Chord-ähnlichem Ansatz)
function joinMulticastTree(mid, nodeId) {
  const root = findSuccessor(mid); // Wurzel des Baums finden
  const path = routeToRoot(nodeId, root); // Pfad zur Wurzel bestimmen
  
  for (const q of path) {
    if (!q.hasSeenJoinRequest(mid)) {
      q.setParent(nodeId); // Aktueller Knoten wird Elternknoten
      nodeId.setParent(q);   // Beitrittsknoten wird Kind
      forwardJoinRequest(q, mid); // Weiterleitung zur Wurzel
      break;
    }
  }
}
```

```
// Beispiel 3: Flooding-Suche in einem unstrukturierten Overlay-Netzwerk (Peer-to-Peer-System)
function search(node, query, ttl) {
    if (ttl <= 0 || query in node.cache) {
        return;
    }
    if (node.has_file(query)) {
        return node.address;
    }
    for (neighbor in node.neighbors) {
        search(neighbor, query, ttl - 1);
    }
}
```

*Erläuterung zu Beispiel 2*: Der Code zeigt, wie ein [[Knoten]] einem [[Multicast-Baum]] beitritt. Der Beitrittswunsch wird entlang des Pfads zur Wurzel weitergeleitet, bis ein [[Knoten]] gefunden wird, der den Baum bereits kennt oder als Hilfsknoten fungiert. Dies ist ein typisches [[Anwendungsbeispiel]] für [[Application-Level_Multicasting|Application-Level Multicasting (ALM)]] in Overlay-Netzwerken.
