---
id: 2dd4f393-e6e4-409b-8465-993896d86624
title: "Strukturiertes Overlay-Netzwerk"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - peer-to-peer
  - routing
  - architektur
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Strukturiertes Overlay-Netzwerk]]

- **Kernkonzept:** Ein [[strukturiertes_Overlay-Netzwerk|strukturiertes Overlay-Netzwerk]] ist ein [[Overlay-Netzwerk]], das [[Knoten]] in einer definierten [[Topologie]] (z. B. Ring, Baum) organisiert, um effizientes [[Routing]] und deterministische [[Suche|Suchvorgänge]] zu ermöglichen. Im Gegensatz dazu basiert ein [[unstrukturiertes_Overlay-Netzwerk|unstrukturiertes Overlay-Netzwerk]] auf zufälligen [[Nachbar|Nachbarschaftsbeziehungen]] ohne feste [[Struktur]], was flexible, aber ineffiziente [[Kommunikation]] zur Folge hat.
- **Nutzen & Zweck:** Strukturierte [[Overlay-Netzwerk|Overlay-Netzwerke]] lösen das Problem unkontrollierter [[Kommunikation]] in [[verteilten_Systemen|verteilten Systemen]], indem sie effizientes [[Routing]] und skalierbare [[Suche|Suchmechanismen]] durch vordefinierte [[Topologie|Topologien]] ermöglichen. Sie eignen sich besonders für Anwendungen mit hohen Anforderungen an [[Skalierbarkeit]], deterministische Antwortzeiten und [[Lastverteilung]], wie z. B. [[Verteilte_Hash-Tabelle|verteilte Hash-Tabellen]] oder [[Content-Delivery-Netzwerk|Content-Delivery-Netzwerke]]. [[Unstrukturierte_Overlay-Netzwerk|Unstrukturierte Overlay-Netzwerke]] bieten dagegen Vorteile in dynamischen Umgebungen mit häufigen [[Knoten]]-Ein- und Austritten, da sie keine starre [[Topologie]] erfordern und sich schnell an Veränderungen anpassen können. Sie sind jedoch weniger effizient bei [[Suche|Suchvorgängen]] und [[Routing]]-Entscheidungen.
- **Abgrenzung & Grenzen:** Strukturierte [[Overlay-Netzwerk|Overlay-Netzwerke]] sind weniger flexibel als [[unstrukturierte_Overlay-Netzwerk|unstrukturierte Overlay-Netzwerke]] bei stark variierenden [[Netzwerk|Netzwerkbedingungen]] oder häufigen [[Knoten]]-Ausfällen, da die feste [[Topologie]] Anpassungen erschwert und zusätzlichen Verwaltungsaufwand erfordert. Sie sind ungeeignet für Szenarien mit hoher Dynamik, wie z. B. mobile Ad-hoc-Netzwerke, wo [[Knoten]] häufig wechseln. Zudem können sie bei ungleichmäßiger [[Lastverteilung]] zu Engpässen führen, wenn bestimmte [[Knoten]] überlastet werden. [[Unstrukturierte_Overlay-Netzwerk|Unstrukturierte Overlay-Netzwerke]] bieten hier Vorteile durch ihre einfache Implementierung und schnelle Anpassungsfähigkeit, allerdings auf Kosten ineffizienter [[Suche|Suchvorgänge]] (z. B. durch [[Flooding]]) und unvorhersehbarer [[Routing]]-Pfade. Beide Ansätze haben somit spezifische Einsatzgebiete, die von den Anforderungen an [[Skalierbarkeit]], Dynamik und Effizienz abhängen.
- **Beispiel / Code:** ### Strukturiertes Overlay-Netzwerk: [[Chord-Protokoll]]
Ein Beispiel für ein strukturiertes Overlay-Netzwerk mit [[Verteilte_Hash-Tabelle|verteilter Hash-Tabelle]] (DHT) und logarithmischer [[Routing]]-Komplexität.

```java
// Vereinfachte Darstellung des Chord-Rings mit DHT-basiertem Routing
public class ChordNode {
    private String nodeId;
    private Map<String, String> fingerTable; // Verteilte Hash-Tabelle für effizientes Routing
    private String successor;
    private String predecessor;

    public ChordNode(String nodeId) {
        this.nodeId = nodeId;
        this.fingerTable = new HashMap<>();
    }
    
    // Aktualisiert die Finger-Tabelle für effizientes Routing
    public void updateFingerTable(Map<String, String> networkNodes) {
        for (Map.Entry<String, String> entry : networkNodes.entrySet()) {
            if (isInRange(entry.getKey(), nodeId, successor)) {
                fingerTable.put(entry.getKey(), entry.getValue());
            }
        }
    }
    
    // Sucht nach einem Schlüssel im Chord-Ring mit logarithmischer Komplexität
    public String findSuccessor(String key) {
        if (isInRange(key, nodeId, successor)) {
            return successor;
        } else {
            // Nächster Knoten in der Finger-Tabelle wird kontaktiert
            String nextNode = closestPrecedingNode(key);
            return requestSuccessorFromNode(nextNode, key);
        }
    }

    private boolean isInRange(String key, String start, String end) {
        // Logik zur Überprüfung, ob der Schlüssel im Bereich liegt
        return true;
    }

    private String closestPrecedingNode(String key) {
        // Logik zur Bestimmung des nächsten Knotens in der Finger-Tabelle
        return fingerTable.getOrDefault(key, successor);
    }

    private String requestSuccessorFromNode(String node, String key) {
        // Kommunikation mit einem anderen Knoten zur Weiterleitung der Anfrage
        return "Successor found via " + node;
    }
}
```

### Unstrukturiertes Overlay-Netzwerk: [[Gnutella-Protokoll]]
Ein Beispiel für ein unstrukturiertes Overlay-Netzwerk mit [[Flooding]]-basiertem [[Routing]].

```java
// Vereinfachte Darstellung von Flooding in Gnutella
public class GnutellaNode {
    private List<String> connections; // Zufällige Verbindungen zu anderen Knoten
    private int ttl; // Time-To-Live für Flooding-Begrenzung

    public GnutellaNode() {
        this.connections = new ArrayList<>();
        this.ttl = 7; // Standard-TTL für Flooding
    }
    
    // Baut eine zufällige Verbindung zu einem anderen Knoten auf
    public void addRandomConnection(String node) {
        if (!connections.contains(node)) {
            connections.add(node);
        }
    }
    
    // Sendet eine Suchanfrage per Flooding an alle verbundenen Knoten
    public void floodSearchRequest(String query, int currentTtl) {
        if (currentTtl <= 0) {
            return; // Abbruch bei TTL-Erreichung
        }
        for (String node : connections) {
            sendRequest(node, query, currentTtl - 1);
        }
    }

    private void sendRequest(String node, String query, int newTtl) {
        // Logik zum Weiterleiten der Anfrage mit reduzierter TTL
        System.out.println("Forwarding query to " + node + " with TTL " + newTtl);
    }
}
```
