---
id: 3d27904e-9097-4bc7-b3ac-7814faaeba2d
title: "Datenstruktur"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - datenbanken
  - persistenz
  - softwarearchitektur
  - graphentheorie
  - lokalisierung
  - draft
source: "Klausur_Referenz"
---

# [[Datenstruktur]]

- **Kernkonzept:** Eine [[Datenstruktur]] ist ein systematisches Format zur Organisation, Speicherung und Verwaltung von Daten in einem Computersystem, um effizienten Zugriff und Modifikation zu ermöglichen. Sie definiert die logische und physische Anordnung von Daten sowie die Operationen, die auf diesen Daten ausgeführt werden können. Datenstrukturen sind fundamental für die Implementierung von [[Algorithmen]] und die Gestaltung von [[Softwarearchitektur|Softwarearchitekturen]], da sie die Performance, Skalierbarkeit und Wartbarkeit von Anwendungen maßgeblich beeinflussen.
- **Nutzen & Zweck:** Datenstrukturen dienen folgenden Zwecken:
1. **Effizienzsteigerung**: Durch die Wahl geeigneter Datenstrukturen (z. B. [[Hash_Tabelle]], [[Binärbaum]]) können Operationen wie Suchen, Einfügen oder Löschen optimiert werden (z. B. O(1) vs. O(n)).
2. **Datenorganisation**: Sie ermöglichen eine strukturierte Ablage von Daten, was die Lesbarkeit und Wartbarkeit von Code verbessert (z. B. [[Graph]] für Netzwerke, [[Stack]] für LIFO-Operationen).
3. **Abstraktion**: Datenstrukturen kapseln komplexe Implementierungsdetails und bieten klare [[Schnittstellen]] für die Interaktion (z. B. [[Liste]] vs. [[Array]]).
4. **Lokale Speicherung**: Im gegebenen Kontext (Smartphone-Apps) eignen sich spezifische Datenstrukturen für die lokale Persistenz, z. B. [[SQLite]] für relationale Daten oder [[NoSQL]]-Strukturen wie [[Key-Value_Store]] für individualisierte Touren.
5. **Datenintegrität**: Durch Validierungsmechanismen (z. B. in [[B-Baum]]-Indizes) wird die Konsistenz der Daten sichergestellt.
- **Abgrenzung & Grenzen:** 1. **Kein Algorithmus**: Eine Datenstruktur definiert *wie* Daten organisiert werden, nicht *wie* sie verarbeitet werden (letzteres ist Aufgabe von [[Algorithmen]]).
2. **Plattformabhängigkeit**: Manche Datenstrukturen sind sprach- oder systemabhängig (z. B. [[Linked_List]] in C vs. Java).
3. **Speicherbedarf vs. Performance**: Komplexe Strukturen (z. B. [[Graph]]) bieten Flexibilität, benötigen aber mehr Speicher als einfache (z. B. [[Array]]).
4. **Lokale vs. verteilte Speicherung**: Für Smartphone-Apps sind lokale Datenstrukturen (z. B. [[SQLite]]) geeignet, während verteilte Systeme [[Distributed_Hash_Table]] oder [[CAP_Theorem]]-konforme Lösungen erfordern.
5. **Stolpersteine**: 
   - Falsche Wahl der Datenstruktur führt zu Performance-Engpässen (z. B. lineare Suche in unsortierten [[Array]]s).
   - Thread-Safety: Datenstrukturen wie [[Hash_Tabelle]] müssen bei parallelem Zugriff synchronisiert werden (z. B. via [[Monitor_Pattern]]).
   - Persistenz: Nicht alle Datenstrukturen sind direkt serialisierbar (z. B. [[Pointer]] in C).
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer einfachen [[Graph]]-Datenstruktur in Java zur Modellierung von Touren (Knoten = Orte, Kanten = Verbindungen). Die Implementierung nutzt eine [[Adjazenzliste]] für effiziente Speicherung und Traversierung.', 'code': 'import java.util.*;\n\nclass Graph {\n    private Map<String, List<Edge>> adjacencyList;\n\n    public Graph() {\n        this.adjacencyList = new HashMap<>();\n    }\n\n    // Knoten hinzufügen\n    public void addNode(String node) {\n        adjacencyList.putIfAbsent(node, new ArrayList<>());\n    }\n\n    // Kante hinzufügen (gewichtet für Touren-Distanzen)\n    public void addEdge(String source, String destination, int weight) {\n        adjacencyList.get(source).add(new Edge(destination, weight));\n        adjacencyList.get(destination).add(new Edge(source, weight)); // Ungerichteter Graph\n    }\n\n    // Tiefensuche (DFS) zur Pfadfindung\n    public List<String> findPath(String start, String end) {\n        Set<String> visited = new HashSet<>();\n        List<String> path = new ArrayList<>();\n        dfsHelper(start, end, visited, path);\n        return path;\n    }\n\n    private boolean dfsHelper(String current, String end, Set<String> visited, List<String> path) {\n        visited.add(current);\n        path.add(current);\n\n        if (current.equals(end)) {\n            return true;\n        }\n\n        for (Edge edge : adjacencyList.get(current)) {\n            if (!visited.contains(edge.destination)) {\n                if (dfsHelper(edge.destination, end, visited, path)) {\n                    return true;\n                }\n            }\n        }\n\n        path.remove(path.size() - 1); // Backtracking\n        return false;\n    }\n\n    private static class Edge {\n        String destination;\n        int weight;\n\n        Edge(String destination, int weight) {\n            this.destination = destination;\n            this.weight = weight;\n        }\n    }\n}\n\n// Nutzung: Individualisierte Touren speichern und abrufen\npublic class TourenManager {\n    public static void main(String[] args) {\n        Graph tourGraph = new Graph();\n        tourGraph.addNode("Berlin");\n        tourGraph.addNode("München");\n        tourGraph.addNode("Hamburg");\n        tourGraph.addEdge("Berlin", "München", 584);\n        tourGraph.addEdge("Berlin", "Hamburg", 289);\n\n        List<String> tour = tourGraph.findPath("Berlin", "München");\n        System.out.println("Tour: " + tour); // Ausgabe: [Berlin, München]\n    }\n}', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Graph {\n        -adjacencyList: Map<String, List~Edge~>\n        +addNode(node: String)\n        +addEdge(source: String, destination: String, weight: int)\n        +findPath(start: String, end: String): List~String~\n    }\n    \n    class Edge {\n        +destination: String\n        +weight: int\n    }\n    \n    Graph "1" *-- "*" Edge : enthält\n```'}
