---
id: bc8ef5cb-0d44-4a8b-8fd1-ab58e83a4664
title: "Klausur_WiSe2023_2024_Aufgabe5_Graphen_Durchsuchung_Breitensuche"
date: 2026-05-30
tags:
  - software_engineering
  - wise2023_2024
  - klausur_ws2023_2024
  - graphentheorie
  - breitensuche
  - algorithmen
  - datenstrukturen
  - java
  - pfadfindung
  - exercise
  - draft
source: "SWE 2023-2024 mit Loesung.pdf"
---

# [[Klausur_WiSe2023_2024_Aufgabe5_Graphen_Durchsuchung_Breitensuche]]

- **Aufgabenstellung:** 
  Gegeben ist eine Graphen-Bibliothek mit der Klasse `Node`, die Knoten und deren Verbindungen repräsentiert. Ihre Aufgabe ist es, die Methode `pathExists(Node node)` zu implementieren, die prüft, ob der übergebene Knoten von dem aktuellen Knoten aus erreichbar ist.
  
  Teilaufgaben:
  1. Vervollständigen Sie die Methode `pathExists` in der Klasse `Node`, sodass sie mittels Breitensuche (BFS) prüft, ob der Zielknoten erreichbar ist.
  2. Achten Sie darauf, dass die Implementierung keine unendlichen Schleifen verursacht und effizient arbeitet.
  3. Erläutern Sie kurz, warum die gewählte Suchstrategie (BFS) für dieses Problem geeignet ist.
- **Lösungsweg / Musterlösung:** 
  - **implementierung:**
  Die Methode `pathExists` wurde bereits korrekt implementiert. Hier die Lösung mit zusätzlichen Kommentaren für Klarheit:
  
  ```java
  public boolean pathExists(Node node) {
      // Abbruch, falls der Zielknoten null ist oder mit dem aktuellen Knoten übereinstimmt
      if (node == null || this.equals(node)) {
          return true;
      }
      
      boolean found = false;
      boolean done = false;
      Queue<Node> nextToVisit = new LinkedList<>();
      Set<Node> visited = new HashSet<>();
      
      // Starte die Suche beim aktuellen Knoten
      nextToVisit.add(this);
      
      do {
          Node next = nextToVisit.poll();
          boolean alreadyVisited = visited.contains(next);
          
          if (!alreadyVisited) {
              // Prüfe, ob der aktuelle Knoten der Zielknoten ist
              found = next.equals(node);
              
              if (!found) {
                  // Markiere den Knoten als besucht und füge seine Nachbarn zur Warteschlange hinzu
                  visited.add(next);
                  Set<Node> neighbors = next.getNeighbors();
                  nextToVisit.addAll(neighbors);
              }
          }
          // Beende die Schleife, wenn die Warteschlange leer ist oder der Zielknoten gefunden wurde
          done = nextToVisit.isEmpty();
      } while (!done && !found);
      
      return found;
  }
  ```
  - **begründung_bfs:**
  Die Breitensuche (BFS) ist für dieses Problem geeignet, weil:
  - Sie systematisch alle Knoten Ebene für Ebene durchsucht und garantiert den kürzesten Pfad findet, falls einer existiert.
  - Sie effizient mit einer Warteschlange (`Queue`) arbeitet und sicherstellt, dass jeder Knoten nur einmal besucht wird (durch die Verwendung einer `Set` für besuchte Knoten).
  - Sie im Gegensatz zur Tiefensuche (DFS) nicht in unendliche Schleifen gerät, falls der Graph Zyklen enthält, da besuchte Knoten markiert werden.
  - Sie für ungewichtete Graphen optimal ist, da sie alle erreichbaren Knoten in minimaler Zeit durchsucht.
- **Theoretischer Bezug:** 
  - Die Aufgabe bezieht sich auf [[Graphentheorie|Graphen]] und [[Breitensuche|Breitensuche (BFS)]].
  - Die Implementierung nutzt grundlegende Konzepte der [[Datenstruktur|Datenstrukturen]] wie [[Queue|Warteschlangen]] und [[HashSet|Hash-Sets]].
  - Die Methode `pathExists` ist ein Beispiel für [[Algorithmus|Algorithmen]] zur Pfadfindung in ungerichteten [[Graph|Graphen]].
  - Die Verwendung von `Set` zur Vermeidung von Zyklen ist ein zentrales Konzept der [[Graph_Durchsuchung|Graphendurchsuchung]].
- **Stolpersteine / Fehlerquellen:** 
  - Vergessen, den aktuellen Knoten als besucht zu markieren, führt zu unendlichen Schleifen, insbesondere bei zyklischen Graphen.
  - Falsche Initialisierung der Warteschlange: Die Suche muss beim aktuellen Knoten (`this`) beginnen, nicht beim Zielknoten.
  - Unnötige Überprüfung von `null`-Werten innerhalb der Schleife, obwohl dies bereits zu Beginn abgefangen wird.
  - Verwendung einer `List` statt einer `Set` für besuchte Knoten führt zu ineffizienter Suche, da `List.contains()` eine lineare Zeitkomplexität hat.
  - Vermischung von BFS und DFS: Die Wahl der falschen Suchstrategie kann zu ineffizienter oder unvollständiger Pfadfindung führen.
  - Fehlende Prüfung auf Gleichheit des aktuellen Knotens mit dem Zielknoten vor dem Start der Suche (`this.equals(node)`).
