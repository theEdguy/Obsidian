---
id: c1fda368-6dcc-49be-a6f0-81f0c7626d4a
title: "Graph_Durchsuchung"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - datenstrukturen
  - graphentheorie
  - java
  - traversierung
  - draft
source: "Klausur_Referenz"
---

# [[Graph_Durchsuchung]]

- **Kernkonzept:** Die [[Graph_Durchsuchung]] bezeichnet systematische Algorithmen zur Traversierung oder Exploration von [[Graphen]], um bestimmte Knoten, Pfade oder Strukturen zu finden. Sie ist ein fundamentales Konzept in der Graphentheorie und wird typischerweise in zwei Hauptvarianten unterteilt: **Breitensuche (BFS - Breadth-First Search)** und **Tiefensuche (DFS - Depth-First Search)**. Beide Methoden operieren auf der Grundlage von [[Schnittstellen]] wie `Graph` und `Node`, die die Struktur des Graphen abstrahieren (z. B. über Methoden wie `nodes()` oder `edge(Node n, Node m)`).
- **Nutzen & Zweck:** Graph_Durchsuchung wird eingesetzt, um:
- Pfade zwischen Knoten zu finden (z. B. kürzeste Wege in Navigationssystemen).
- Zyklen oder zusammenhängende Komponenten in [[Graphen]] zu identifizieren (z. B. in sozialen Netzwerken oder Abhängigkeitsanalysen).
- Datenstrukturen wie Bäume oder Listen aus Graphen abzuleiten (z. B. für [[Topologische_Sortierung]]).
- Suchprobleme in Spielen oder künstlicher Intelligenz zu lösen (z. B. Labyrinth-Algorithmen).

Die Wahl zwischen BFS und DFS hängt vom Anwendungsfall ab: BFS eignet sich für kürzeste Pfade in ungewichteten Graphen, während DFS speichereffizienter ist und für Backtracking-Probleme (z. B. Sudoku-Löser) genutzt wird.
- **Abgrenzung & Grenzen:** Graph_Durchsuchung unterscheidet sich von:
- **Graph_Traversierung**: Während Durchsuchung gezielt nach bestimmten Knoten oder Pfaden sucht, traversiert eine reine Traversierung alle Knoten (z. B. für Serialisierung).
- **Graph_Algorithmen wie Dijkstra oder A***: Diese erweitern die Durchsuchung um Gewichte oder Heuristiken, während BFS/DFS ungewichtete Graphen voraussetzen.

Typische Stolpersteine:
- **Unendliche Schleifen**: Bei zyklischen Graphen muss der besuchte Status von Knoten (`visited`-Markierung) verwaltet werden.
- **Speicherkomplexität**: BFS kann bei breiten Graphen viel Speicher benötigen (Warteschlange wächst exponentiell).
- **Implizite Graphen**: Bei dynamisch generierten Graphen (z. B. Spielbäumen) muss die Durchsuchung rekursiv oder iterativ mit Stacks/Warteschlangen umgesetzt werden.
- **Beispiel / Code:** {'beschreibung': 'Implementierung einer Tiefensuche (DFS) in Java für die gegebene `Graph`-Schnittstelle. Das Beispiel zeigt, wie Knoten rekursiv traversiert und besuchte Knoten markiert werden, um Zyklen zu vermeiden.', 'code': 'import java.util.*;\n\npublic class GraphSearch {\n    private final Graph graph;\n    private final Set<Node> visited = new HashSet<>();\n\n    public GraphSearch(Graph graph) {\n        this.graph = graph;\n    }\n\n    /**\n     * Führt eine Tiefensuche (DFS) ab einem Startknoten durch.\n     * @param start Der Startknoten.\n     * @return Liste der besuchten Knoten in DFS-Reihenfolge.\n     */\n    public List<Node> depthFirstSearch(Node start) {\n        List<Node> result = new ArrayList<>();\n        dfsHelper(start, result);\n        return result;\n    }\n\n    private void dfsHelper(Node current, List<Node> result) {\n        if (visited.contains(current)) {\n            return;\n        }\n        visited.add(current);\n        result.add(current);\n        // Iteriere über alle Nachbarn des aktuellen Knotens\n        for (Node neighbor : graph.nodes()) {\n            if (graph.edge(current, neighbor)) {\n                dfsHelper(neighbor, result);\n            }\n        }\n    }\n\n    /**\n     * Führt eine Breitensuche (BFS) ab einem Startknoten durch.\n     * @param start Der Startknoten.\n     * @return Liste der besuchten Knoten in BFS-Reihenfolge.\n     */\n    public List<Node> breadthFirstSearch(Node start) {\n        List<Node> result = new ArrayList<>();\n        Queue<Node> queue = new LinkedList<>();\n        queue.add(start);\n        visited.add(start);\n\n        while (!queue.isEmpty()) {\n            Node current = queue.poll();\n            result.add(current);\n            // Füge alle unbesuchten Nachbarn zur Warteschlange hinzu\n            for (Node neighbor : graph.nodes()) {\n                if (graph.edge(current, neighbor) && !visited.contains(neighbor)) {\n                    visited.add(neighbor);\n                    queue.add(neighbor);\n                }\n            }\n        }\n        return result;\n    }\n}', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Graph {\n        <<interface>>\n        +nodes() Set~Node~\n        +edge(Node n, Node m) boolean\n        +connectedSubGraph(Node n) Graph\n    }\n    class Node {\n        <<interface>>\n    }\n    class GraphSearch {\n        -graph: Graph\n        -visited: Set~Node~\n        +depthFirstSearch(Node start) List~Node~\n        +breadthFirstSearch(Node start) List~Node~\n    }\n    GraphSearch --> Graph : uses\n    Graph ..> Node : contains\n```'}
