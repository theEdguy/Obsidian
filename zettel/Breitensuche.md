---
id: 278aaacc-913c-4ab5-b068-431bd077763d
title: "Breitensuche"
date: 2026-05-30
tags:
  - software_engineering
  - graphenalgorithmen
  - datenstrukturen
  - algorithmen_und_komplexitaet
  - kuenstliche_intelligenz
  - draft
source: "Klausur_Referenz"
---

# [[Breitensuche]]

- **Kernkonzept:** Die Breitensuche (engl. Breadth-First Search, BFS) ist ein [[Graphenalgorithmus]], der systematisch alle Knoten eines [[Graphen]] in der Reihenfolge ihrer Entfernung vom Startknoten durchläuft. Dabei werden zunächst alle direkten Nachbarn des Startknotens besucht, anschließend deren Nachbarn usw., bis alle erreichbaren Knoten abgearbeitet sind. Die Suche erfolgt schichtweise (Level für Level) und nutzt eine [[Queue]] zur Verwaltung der zu besuchenden Knoten.
- **Nutzen & Zweck:** Die Breitensuche wird primär eingesetzt, um:
- Den kürzesten Pfad in ungewichteten Graphen zu finden (z. B. in [[Navigationssysteme]]n oder sozialen Netzwerken).
- Alle erreichbaren Knoten von einem Startpunkt aus zu traversieren (z. B. für [[Web_Crawler]] oder Netzwerkanalysen).
- Probleme in der [[Künstlichen_Intelligenz]] zu lösen, wie z. B. das Finden optimaler Lösungen in Spielbäumen (z. B. Schach).
- Zyklen in Graphen zu erkennen oder die [[Zusammenhangskomponenten]] eines Graphen zu bestimmen.

Vorteile: Garantiert die kürzeste Pfadlänge in ungewichteten Graphen und ist einfach zu implementieren.
- **Abgrenzung & Grenzen:** Abgrenzung zu anderen Algorithmen:
- Im Gegensatz zur [[Tiefensuche]] (DFS) wird bei der Breitensuche nicht sofort in die Tiefe gegangen, sondern schichtweise vorgegangen. Dies führt zu höherem Speicherbedarf (da alle Knoten eines Levels in der Queue gehalten werden müssen).
- Für gewichtete Graphen ist die Breitensuche ungeeignet – hier kommen Algorithmen wie [[Dijkstra_Algorithmus]] oder [[A*_Algorithmus]] zum Einsatz.

Typische Stolpersteine:
- Unendliche Schleifen bei zyklischen Graphen, wenn besuchte Knoten nicht markiert werden.
- Hoher Speicherbedarf bei Graphen mit großer Breite (z. B. Bäume mit hohem Verzweigungsfaktor).
- Ineffizienz bei Graphen mit vielen Knoten, wenn nur ein Teilbereich durchsucht werden soll (hier wäre DFS oft besser).
- **Beispiel / Code:** ```java
import java.util.*;

public class Breitensuche {
    public static void bfs(Map<Integer, List<Integer>> graph, int start) {
        Queue<Integer> queue = new LinkedList<>();
        Set<Integer> visited = new HashSet<>();
        
        queue.add(start);
        visited.add(start);
        
        while (!queue.isEmpty()) {
            int current = queue.poll();
            System.out.println("Besuche Knoten: " + current);
            
            for (int neighbor : graph.getOrDefault(current, new ArrayList<>())) {
                if (!visited.contains(neighbor)) {
                    visited.add(neighbor);
                    queue.add(neighbor);
                }
            }
        }
    }
    
    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(2));
        graph.put(2, Arrays.asList(0, 3));
        graph.put(3, Arrays.asList(3));
        
        bfs(graph, 2); // Startknoten: 2
    }
}
```

**Ausgabe (Reihenfolge der Besuche):**
2 → 0 → 3 → 1
