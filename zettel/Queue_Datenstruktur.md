---
id: 45fd3d9f-6951-459c-a85d-de242885eb3b
title: "Queue_Datenstruktur"
date: 2026-05-31
tags:
  - software_engineering
  - datenstrukturen
  - algorithmen
  - java
  - graphentheorie
  - multithreading
  - draft
source: "Klausur_Referenz"
---

# [[Queue_Datenstruktur]]

- **Kernkonzept:** Eine [[Queue]] (deutsch: Warteschlange) ist eine lineare [[Datenstruktur]], die nach dem **FIFO-Prinzip** (First-In-First-Out) arbeitet. Elemente werden am Ende der Schlange eingefügt (Enqueue-Operation) und am Anfang entnommen (Dequeue-Operation). Sie modelliert reale Warteschlangen (z. B. Druckaufträge) und ist essenziell für die Steuerung von [[Prozess_Synchronisation]] oder [[Breitensuche]] in Graphen.
- **Nutzen & Zweck:** Queues dienen der **temporären Pufferung** von Daten oder Aufgaben, um eine sequenzielle Abarbeitung zu gewährleisten. Typische Anwendungen:
- **Algorithmen**: [[Breitensuche]] in Graphen (wie im gegebenen Codebeispiel), [[Task_Scheduling]] in Betriebssystemen.
- **Systemdesign**: Entkopplung von [[Produzent_Konsument_Problem]]-Komponenten (z. B. Nachrichtenwarteschlangen in [[Microservices]]).
- **Echtzeitsysteme**: Priorisierte Warteschlangen für [[Ereignisbehandlung]].

Vorteile: Einfache Implementierung, deterministische Zeitkomplexität (O(1) für Enqueue/Dequeue bei [[LinkedList]]-Implementierung).
- **Abgrenzung & Grenzen:** Abgrenzung zu ähnlichen Strukturen:
- **[[Stack]]**: Arbeitet nach LIFO (Last-In-First-Out), während Queues FIFO nutzen.
- **[[Deque]]**: Erlaubt Einfügen/Entfernen an beiden Enden (flexibler, aber komplexer).
- **[[Priority_Queue]]**: Elemente werden nach Priorität entnommen, nicht nach Einfügezeit.

Stolpersteine:
- **Überlauf**: Bei statischen Implementierungen (z. B. Arrays) kann die Kapazität erschöpft sein.
- **Thread-Sicherheit**: In [[Multithreading]]-Umgebungen sind synchronisierte Queues (z. B. `ConcurrentLinkedQueue`) erforderlich.
- **Performance**: Bei falscher Implementierung (z. B. Array-basiert mit Verschiebung) kann Dequeue O(n) statt O(1) kosten.
- **Beispiel / Code:** {'beschreibung': 'Java-Implementierung einer Queue für die [[Breitensuche]] (aus dem Kontext):', 'code': 'import java.util.*;\n\npublic class GraphTraversal {\n    private Set<Node> connectedNodeSet = new HashSet<>();\n\n    public void init(Node startNode) {\n        Queue<Node> notVisited = new LinkedList<>();  // Queue-Implementierung\n        Set<Node> visited = new HashSet<>();\n        notVisited.add(startNode);\n\n        while (!notVisited.isEmpty()) {\n            Node currentNode = notVisited.poll();  // FIFO: ältestes Element entnehmen\n            if (!visited.contains(currentNode)) {\n                visited.add(currentNode);\n                connectedNodeSet.add(currentNode);\n                notVisited.addAll(unvisitedNeighbors(visited, currentNode));  // Neue Knoten am Ende einfügen\n            }\n        }\n    }\n\n    private Set<Node> unvisitedNeighbors(Set<Node> visited, Node node) {\n        // ... (Filtert unbesuchte Nachbarn)\n    }\n}\n\nclass Node {\n    // Knoten-Implementierung (z. B. mit Adjazenzliste)\n}', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Queue~T~ {\n        +add(T element)  // Enqueue\n        +poll() T        // Dequeue\n        +isEmpty() boolean\n    }\n    Queue <|-- LinkedList\n    Queue : FIFO-Prinzip\n```'}
