---
id: de833f0f-d367-4dfb-95c2-81c9863ae03e
title: "Graphen_Darstellung"
date: 2026-05-30
tags:
  - software_engineering
  - graphentheorie
  - datenstrukturen
  - algorithmen
  - entwurfsmuster
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Graphen_Darstellung]]

- **Kernkonzept:** Die [[Graphen_Darstellung]] bezeichnet die strukturelle und algorithmische Repräsentation von [[Graphen]] in der Softwareentwicklung, um Beziehungen zwischen Entitäten (Knoten) und deren Verbindungen (Kanten) abzubilden. Sie umfasst sowohl die interne Datenhaltung (z. B. Adjazenzlisten, Adjazenzmatrizen) als auch die externe Modellierung (z. B. [[UML-Klassendiagramm]] oder [[Sequenzdiagramm]]). Im gegebenen Kontext wird die Darstellung durch eine [[Schnittstelle]] `Graph` und deren Implementierung `GraphImpl` realisiert, wobei Knoten (`Node`) und Teilgraphen (`ConnectedSubGraph`) als zentrale Komponenten agieren.
- **Nutzen & Zweck:** Die [[Graphen_Darstellung]] ermöglicht die effiziente Abbildung komplexer Netzwerke (z. B. soziale Netzwerke, Routenplanung, Abhängigkeitsanalysen) und deren algorithmische Verarbeitung (z. B. Pfadsuche, Zyklenerkennung, Topologische_Sortierung). Durch die Trennung von [[Schnittstelle]] und Implementierung (vgl. [[Brückenmuster]]) wird Flexibilität für verschiedene Speicherstrategien (z. B. sparse vs. dichte Graphen) und Erweiterungen (z. B. gewichtete Kanten) geschaffen. Die Methode `pathExists` demonstriert die praktische Anwendung zur Erreichbarkeitsprüfung, ein Grundbaustein für [[Graphenalgorithmen]].
- **Abgrenzung & Grenzen:** Die [[Graphen_Darstellung]] grenzt sich von einfachen Datenstrukturen wie [[Listen]] oder [[Bäumen]] durch ihre Fähigkeit ab, zyklische und ungerichtete Beziehungen zu modellieren. Typische Stolpersteine sind:
- **Speichereffizienz**: Adjazenzmatrizen verbrauchen O(n²) Speicher, während Adjazenzlisten für sparse Graphen besser geeignet sind.
- **Konsistenz**: Bei dynamischen Graphen (z. B. Hinzufügen/Löschen von Knoten) muss die Integrität der Teilgraphen (`ConnectedSubGraph`) sichergestellt werden.
- **Algorithmenkomplexität**: Erreichbarkeitsprüfungen (z. B. `pathExists`) erfordern [[Tiefensuche]] oder [[Breitensuche]], deren Laufzeit von der Darstellung abhängt.
- **Abstraktion vs. Performance**: Eine zu generische [[Schnittstelle]] kann zu Overhead führen, während zu spezifische Implementierungen die Wiederverwendbarkeit einschränken.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Java-Codebeispiel zeigt eine vereinfachte Implementierung der `Node`-Klasse mit der Methode `pathExists`, die mittels [[Tiefensuche]] prüft, ob ein Zielknoten erreichbar ist. Die Darstellung nutzt eine Adjazenzliste (`neighbors`) und vermeidet Zyklen durch ein `visited`-Set.', 'code': 'public class Node {\n    private String id;\n    private Set<Node> neighbors = new HashSet<>();\n\n    public Node(String id) {\n        this.id = id;\n    }\n\n    public void addNeighbor(Node neighbor) {\n        neighbors.add(neighbor);\n    }\n\n    public boolean pathExists(Node target) {\n        return pathExists(target, new HashSet<>());\n    }\n\n    private boolean pathExists(Node target, Set<Node> visited) {\n        if (this.equals(target)) {\n            return true;\n        }\n        visited.add(this);\n        for (Node neighbor : neighbors) {\n            if (!visited.contains(neighbor) && neighbor.pathExists(target, visited)) {\n                return true;\n            }\n        }\n        return false;\n    }\n}', 'uml_diagramm': 'classDiagram\n    class Graph {\n        <<interface>>\n    }\n    class GraphImpl {\n        -nodeSet: Set~Node~\n        +addNode(Node node)\n        +getConnectedSubGraph(Node startNode): ConnectedSubGraph\n    }\n    class ConnectedSubGraph {\n        -connectedNodeSet: Set~Node~\n        -parentGraph: GraphImpl\n        +init(Node startNode)\n    }\n    class Node {\n        -id: String\n        -neighbors: Set~Node~\n        +addNeighbor(Node neighbor)\n        +pathExists(Node target): boolean\n    }\n    Graph <|-- GraphImpl\n    GraphImpl *-- Node : contains\n    GraphImpl *-- ConnectedSubGraph : creates\n    Node *-- Node : neighbors'}
