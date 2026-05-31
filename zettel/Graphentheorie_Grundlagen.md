---
id: 95485e53-f007-4bba-9a11-89352cc8c470
title: "Graphentheorie_Grundlagen"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - datenstrukturen
  - diskrete_mathematik
  - graph_traversierung
  - java
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Graphentheorie_Grundlagen]]

- **Kernkonzept:** Die [[Graphentheorie]] ist ein zentrales Teilgebiet der [[Diskrete_Mathematik]], das sich mit der Untersuchung von [[Graphen]] beschäftigt. Ein Graph besteht aus einer Menge von Knoten (auch Ecken oder Vertices genannt) und einer Menge von Kanten (Edges), die Verbindungen zwischen diesen Knoten darstellen. Graphen können gerichtet oder ungerichtet sein und ermöglichen die Modellierung von Beziehungen und Strukturen in komplexen Systemen. Sie sind fundamental für die Abbildung von Netzwerken, wie z. B. sozialen Netzwerken, Straßenkarten oder Abhängigkeiten in [[Softwarearchitektur]]en.
- **Nutzen & Zweck:** Die Graphentheorie findet breite Anwendung in der Informatik und im [[Software_Engineering]], insbesondere bei der Lösung von Problemen, die Netzwerkstrukturen oder Beziehungen zwischen Entitäten betreffen. Typische Anwendungsfälle umfassen:
- Pfadfindungsalgorithmen (z. B. [[Dijkstra_Algorithmus]], [[A*_Algorithmus]]), die in Navigationssystemen oder Routenplanung eingesetzt werden.
- Analyse von Abhängigkeiten in [[Build_Tools]] (z. B. Maven, Gradle) oder [[Versionsverwaltung]] (z. B. Abhängigkeitsgraphen in Git).
- Modellierung von Datenbankstrukturen (z. B. [[Entity_Relationship_Diagramm]]).
- Optimierung von Netzwerkflüssen (z. B. in Telekommunikationsnetzen oder Logistik).
- Darstellung von Zustandsübergängen in [[Endliche_Automaten]] oder [[Petri_Netze]].
Die Methode `unvisitedNeighbors` aus dem Kontext ist ein Beispiel für die praktische Umsetzung graphentheoretischer Konzepte in der Programmierung, insbesondere zur Traversierung von Graphen (z. B. in [[Tiefensuche]] oder [[Breitensuche]]).
- **Abgrenzung & Grenzen:** Die Graphentheorie grenzt sich von anderen mathematischen oder informatischen Konzepten durch ihre Fokussierung auf relationale Strukturen ab. Typische Stolpersteine und Grenzen sind:
- **Komplexität**: Viele graphentheoretische Probleme (z. B. das [[Hamiltonkreis_Problem]] oder [[Cliquenproblem]]) sind NP-schwer, was ihre praktische Lösung in großen Graphen erschwert.
- **Speicherbedarf**: Die Repräsentation großer Graphen (z. B. als [[Adjazenzmatrix]] oder [[Adjazenzliste]]) kann ineffizient sein, insbesondere bei dünn besetzten Graphen.
- **Gerichtet vs. ungerichtet**: Die Unterscheidung zwischen gerichteten und ungerichteten Graphen ist entscheidend für die Wahl der Algorithmen (z. B. wirkt sich auf die Definition von Nachbarn aus, wie in der Methode `unvisitedNeighbors` gezeigt).
- **Zyklen**: Graphen mit Zyklen erfordern besondere Aufmerksamkeit bei Traversierungsalgorithmen, um Endlosschleifen zu vermeiden (z. B. durch Markierung besuchter Knoten).
- **Java-spezifische Implementierungsdetails**: Wie im Kontext beschrieben, können sprachspezifische Features (z. B. Streams oder implizite Iterationen) die Lesbarkeit von Graphenalgorithmen beeinträchtigen, obwohl sie die Implementierung kompakter machen.
- **Beispiel / Code:** {'beschreibung': 'Die Methode `unvisitedNeighbors` iteriert über alle Nachbarn eines gegebenen Knotens in einem Graphen und filtert diejenigen heraus, die noch nicht besucht wurden. Der folgende Java-Code veranschaulicht den prinzipiellen Ablauf, wobei die implizite Iteration (z. B. über Streams) aufgelöst wird, um die Logik klarer darzustellen:', 'code': 'import java.util.*;\n\npublic class Graph {\n    private Map<Integer, List<Integer>> adjacencyList;\n    private Set<Integer> visitedNodes;\n\n    public Graph() {\n        this.adjacencyList = new HashMap<>();\n        this.visitedNodes = new HashSet<>();\n    }\n\n    // Fügt eine Kante zwischen zwei Knoten hinzu (ungerichteter Graph)\n    public void addEdge(int source, int destination) {\n        adjacencyList.computeIfAbsent(source, k -> new ArrayList<>()).add(destination);\n        adjacencyList.computeIfAbsent(destination, k -> new ArrayList<>()).add(source);\n    }\n\n    // Gibt alle unbesuchten Nachbarn eines Knotens zurück\n    public List<Integer> unvisitedNeighbors(int node) {\n        List<Integer> neighbors = adjacencyList.getOrDefault(node, new ArrayList<>());\n        List<Integer> unvisited = new ArrayList<>();\n        \n        // Explizite Iteration über alle Nachbarn (anstelle von Streams)\n        for (Integer neighbor : neighbors) {\n            if (!visitedNodes.contains(neighbor)) {\n                unvisited.add(neighbor);\n            }\n        }\n        return unvisited;\n    }\n\n    public void markVisited(int node) {\n        visitedNodes.add(node);\n    }\n}\n\n// Beispielaufruf:\npublic class Main {\n    public static void main(String[] args) {\n        Graph graph = new Graph();\n        graph.addEdge(1, 2);\n        graph.addEdge(1, 3);\n        graph.addEdge(2, 4);\n        graph.addEdge(3, 4);\n        \n        graph.markVisited(1);\n        List<Integer> unvisited = graph.unvisitedNeighbors(1);\n        System.out.println("Unbesuchte Nachbarn von Knoten 1: " + unvisited); // Ausgabe: [2, 3]\n    }\n}', 'uml_sequenzdiagramm': {'beschreibung': 'Das folgende Sequenzdiagramm (textuell beschrieben) veranschaulicht den Ablauf der Methode `unvisitedNeighbors` für einen Beispielgraphen mit den Knoten 1, 2, 3 und 4 (Knoten 1 ist bereits besucht):', 'diagramm': 'participant Aufrufer\nparticipant Graph\nparticipant Adjazenzliste\nparticipant VisitedSet\n\nAufrufer -> Graph: unvisitedNeighbors(1)\nGraph -> Adjazenzliste: getOrDefault(1, []) → [2, 3]\nloop für jeden Nachbarn in [2, 3]\n    Graph -> VisitedSet: contains(2) → false\n    Graph -> VisitedSet: contains(3) → false\n    Graph --> Aufrufer: füge 2 zur Ergebnisliste hinzu\n    Graph --> Aufrufer: füge 3 zur Ergebnisliste hinzu\nend\nAufrufer <-- Graph: Rückgabe [2, 3]'}}
