---
id: 1d58841b-f18b-4864-bf14-550740dc4183
title: "Klausur_SoSe2025_Aufgabe5_Graphenanalyse_und_Iteration"
date: 2026-05-30
tags:
  - software_engineering
  - sose_2025
  - klausur_sose_2025
  - graphen
  - java_collections
  - breitensuche
  - sequenzdiagramm
  - implizite_iteration
  - adjazenzliste
  - exercise
  - draft
source: "SWE-SoSe-2025-Loesung.pdf"
---

# [[Klausur_SoSe2025_Aufgabe5_Graphenanalyse_und_Iteration]]

- **Aufgabenstellung:** 
  - **a:** Beschreiben Sie den prinzipiellen Ablauf der Methode `unvisitedNeighbors` im Detail. Gehen Sie dabei insbesondere auf folgende Aspekte ein:
  - **a1:** Wie wird über alle Nachbarn des zu betrachtenden Knotens iteriert?
  - **a2:** Welche Java-spezifischen Features werden genutzt, um die Iteration zu realisieren?
  - **a3:** Wie wird sichergestellt, dass nur unbesuchte Nachbarn zurückgegeben werden?
  - **b:** Vervollständigen Sie das gegebene Sequenzdiagramm (hier textuell beschrieben), um den Ablauf der Methode `unvisitedNeighbors` darzustellen. Berücksichtigen Sie dabei die Interaktionen zwischen den folgenden Objekten:
  - **b1:** - `ConnectedSubGraph`-Instanz (Aufrufer der Methode)
  - **b2:** - `parentGraph` (Instanz von `GraphImpl`)
  - **b3:** - `edgeMap` (Datenstruktur zur Speicherung der Kanten)
  - **b4:** - `visited` (Menge der bereits besuchten Knoten)
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **a1:** Die Methode `unvisitedNeighbors` iteriert über alle Nachbarn eines gegebenen Knotens `node`, indem sie auf die `edgeMap` des `parentGraph` zugreift. Die `edgeMap` ist eine `HashMap<Node, Set<Node>>`, die jedem Knoten eine Menge seiner Nachbarn zuordnet. Die Iteration erfolgt mittels einer **for-each-Schleife** über das `Set<Node>`, das durch `parentGraph.edgeMap.get(node)` zurückgegeben wird. Dies ist ein Beispiel für **implizite Iteration** in Java, da die Schleife intern über das `Set` iteriert, ohne dass ein expliziter Iterator verwendet werden muss.
    - **a2:** Folgende Java-spezifische Features werden genutzt:
    - **a2_1:** - **For-Each-Schleife**: Ermöglicht die einfache Iteration über das `Set<Node>` der Nachbarn, ohne manuell einen `Iterator` zu verwalten.
    - **a2_2:** - **Generics**: Die `HashMap` und das `Set` sind mit Generics (`Node`, `Set<Node>`) typisiert, um Typsicherheit zu gewährleisten.
    - **a2_3:** - **Collection-API**: Die Methode nutzt die `contains`-Methode des `Set`-Interfaces, um zu prüfen, ob ein Nachbar bereits besucht wurde.
    - **a3:** Die Methode prüft für jeden Nachbarn, ob er in der `visited`-Menge enthalten ist. Nur wenn dies nicht der Fall ist (`!visited.contains(neighbor)`), wird der Nachbar zur Ergebnismenge `unvisited` hinzugefügt. Dadurch wird sichergestellt, dass ausschließlich unbesuchte Nachbarn zurückgegeben werden.
    - **code:**
  ```java
  private Set<Node> unvisitedNeighbors(Set<Node> visited, Node node) {
      Set<Node> unvisited = new HashSet<>();
      /* Iteriere über alle Nachbarn des Knotens */
      for (Node neighbor : parentGraph.edgeMap.get(node)) {
          if (!visited.contains(neighbor)) {
              unvisited.add(neighbor);
          }
      }
      /* Gib die unbesuchten Nachbarn zurück */
      return unvisited;
  }
  ```
  - **b:**
  - **sequenzdiagramm_beschreibung:**
  - **schritte:**
  - - **schritt:** 1
          - **aufrufer:** ConnectedSubGraph
          - **aktion:** Ruft `unvisitedNeighbors(visited, node)` auf.
        - - **schritt:** 2
          - **aufrufer:** unvisitedNeighbors
          - **aktion:** Greift auf `parentGraph.edgeMap.get(node)` zu, um das `Set<Node>` der Nachbarn von `node` zu erhalten.
        - - **schritt:** 3
          - **aufrufer:** unvisitedNeighbors
          - **aktion:** Iteriert über das `Set<Node>` der Nachbarn (implizite Iteration via for-each).
        - - **schritt:** 4
          - **aufrufer:** unvisitedNeighbors
          - **aktion:** Prüft für jeden Nachbarn `neighbor`, ob `visited.contains(neighbor)` `false` ergibt.
        - - **schritt:** 5
          - **aufrufer:** unvisitedNeighbors
          - **aktion:** Fügt `neighbor` zur Ergebnismenge `unvisited` hinzu, falls er nicht in `visited` enthalten ist.
        - - **schritt:** 6
          - **aufrufer:** unvisitedNeighbors
          - **aktion:** Gibt die Menge `unvisited` an `ConnectedSubGraph` zurück.
    - **hinweis:** Im Sequenzdiagramm sollten die Lebenslinien der Objekte `ConnectedSubGraph`, `parentGraph`, `edgeMap` und `visited` dargestellt werden. Die Nachrichten zwischen diesen Objekten entsprechen den oben beschriebenen Schritten.
- **Theoretischer Bezug:** 
  - [[Graphen_Darstellung|Graphendarstellung]] in der Informatik, insbesondere die Speicherung von [[Graph|Graphen]] als Adjazenzlisten (hier: `HashMap<Node, Set<Node>>`).
  - [[Iteration|Iteration]] über Collections in Java, speziell die Verwendung von [[For-Each-Schleife|for-each-Schleifen]] und [[Generics|Generics]].
  - [[Breitensuche|Breitensuche (BFS)]] als Anwendungsfall für die Methode `unvisitedNeighbors`, da diese im Kontext der Initialisierung eines zusammenhängenden Teilgraphen (`init`-Methode) verwendet wird.
  - [[Sequenzdiagramm|Sequenzdiagramme]] zur Visualisierung von Methodenaufrufen und Objektinteraktionen.
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung von **impliziter Iteration** (for-each) mit expliziter Iterator-Nutzung. Viele Studierende beschreiben fälschlicherweise die Verwendung eines `Iterator`-Objekts, obwohl dies hier nicht erforderlich ist.
  - Missverständnis der Datenstruktur `edgeMap`: Die `HashMap` speichert nicht die Kanten direkt, sondern ordnet jedem Knoten eine Menge seiner Nachbarn zu. Dies entspricht einer **Adjazenzliste**.
  - Verkennung des Kontexts: Die Methode `unvisitedNeighbors` ist Teil eines [[Breitensuche|BFS-Algorithmus]] (in der `init`-Methode). Ohne diesen Bezug wird die Bedeutung der Methode oft unterschätzt.
  - Fehler bei der Beschreibung des Sequenzdiagramms: Häufig werden die Lebenslinien der Objekte falsch zugeordnet oder die Nachrichten zwischen den Objekten unvollständig dargestellt (z. B. wird der Zugriff auf `edgeMap` vergessen).
  - Unklare Trennung zwischen der `GraphImpl`-Klasse und der inneren Klasse `ConnectedSubGraph`. Studierende verwechseln oft die Verantwortlichkeiten der beiden Klassen, insbesondere die Rolle von `parentGraph`.
