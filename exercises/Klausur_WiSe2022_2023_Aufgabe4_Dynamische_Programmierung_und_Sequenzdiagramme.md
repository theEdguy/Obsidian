---
id: e56cb583-971f-4b10-9067-0cd4c1fae4eb
title: "Klausur_WiSe2022_2023_Aufgabe4_Dynamische_Programmierung_und_Sequenzdiagramme"
date: 2026-05-30
tags:
  - software_engineering
  - wise2022_2023
  - klausur_ws_2022_2023
  - dynamische_programmierung
  - sequenzdiagramm
  - rekursion
  - memoization
  - algorithmen_optimierung
  - exercise
  - draft
source: "SWE 2022-2023 mit Loesung.pdf"
---

# [[Klausur_WiSe2022_2023_Aufgabe4_Dynamische_Programmierung_und_Sequenzdiagramme]]

- **Aufgabenstellung:** 
  - **einleitung:**
  Der Fachbegriff 'Dynamisches Programmieren' steht für rekursive Algorithmen mit immer wiederkehrenden Teilaufgaben. Durch das Speichern von Zwischenergebnissen kann ein unnötiges rekursives Absteigen vermieden werden, wodurch oft eine enorme Reduktion der Komplexität erzielt wird. Ein typisches Beispiel hierfür ist die Berechnung der Fibonacci-Zahlen, definiert als:
  
  ```
  fib(0) = 0
  fib(1) = 1
  fib(n+2) = fib(n) + fib(n+1) für alle n ∈ N0
  ```
  
  Ein rein rekursiver Algorithmus würde diese Definition direkt umsetzen, hätte jedoch das Problem, dass dieselben Fibonacci-Zahlen mehrfach berechnet werden. Um dies zu vermeiden, sollen bereits berechnete Ergebnisse zwischengespeichert werden.
  - **teilaufgaben:**
  - - **teil:** a
      - **punkte:** 10
      - **beschreibung:**
  Skizzieren Sie einen auf diesem Prinzip beruhenden Algorithmus zur Berechnung der n-ten Fibonacci-Zahl mithilfe eines Sequenzdiagramms. Verwenden Sie die vorgegebenen Klassen (`FiboSolver`, `FiboStore`).
  
  Hinweise:
  - Ein `FiboStore` ist nach seiner Erzeugung leer und liefert auf eine Anfrage (`get`) stets `null` zurück.
  - Erst nach dem Eintragen eines Werts (`set`) kann dieser abgefragt werden.
    - - **teil:** b
      - **punkte:** 5
      - **beschreibung:** Implementieren Sie die Klasse `FiboSolver` gemäß Ihrem Design und der obigen Vorlage in Java-Pseudocode. Die Klasse soll die Methode `fibonacci(long n)` enthalten, die die n-te Fibonacci-Zahl unter Verwendung des `FiboStore` berechnet.
- **Lösungsweg / Musterlösung:** 
  - **teil_a:**
  - **beschreibung:**
  Das Sequenzdiagramm sollte folgende Interaktionen darstellen:
  1. `FiboSolver` ruft `store.get(n)` auf, um zu prüfen, ob das Ergebnis bereits gespeichert ist.
  2. Falls `null` zurückgegeben wird (Ergebnis nicht vorhanden):
     - Für `n == 0` oder `n == 1`: Direkte Rückgabe von `n`.
     - Für `n > 1`: Rekursive Aufrufe von `fibonacci(n-1)` und `fibonacci(n-2)`.
  3. Das Ergebnis wird mit `store.set(n, fib)` im `FiboStore` gespeichert.
  4. Der gespeicherte oder berechnete Wert wird zurückgegeben.
  
  **Beispielablauf für `fibonacci(3)`:**
  - `FiboSolver` fragt `store.get(3)` → `null` (nicht vorhanden).
  - Rekursiver Aufruf `fibonacci(2)`:
    - `store.get(2)` → `null`.
    - Rekursiver Aufruf `fibonacci(1)` → Rückgabe `1` (direkt).
    - Rekursiver Aufruf `fibonacci(0)` → Rückgabe `0` (direkt).
    - Berechnung `1 + 0 = 1` und Speicherung mit `store.set(2, 1)`.
  - Rekursiver Aufruf `fibonacci(1)` → Rückgabe `1` (direkt).
  - Berechnung `1 + 1 = 2` und Speicherung mit `store.set(3, 2)`.
  - Rückgabe `2`.
    - **diagramm_hinweis:** Das Sequenzdiagramm sollte die Objekte `FiboSolver` und `FiboStore` als Lebenslinien darstellen, mit Nachrichten wie `get(n)`, `set(n, fib)` und rekursiven Aufrufen von `fibonacci(n-1)` und `fibonacci(n-2)`.
  - **teil_b:**
  - **beschreibung:**
  Die Implementierung der Klasse `FiboSolver` in Java-Pseudocode:
  
  ```java
  public class FiboSolver {
      private FiboStore store = new FiboStore();
  
      public long fibonacci(long n) {
          Long fib = store.get(n);
          if (fib == null && 0 <= n) {
              fib = (n == 0 || n == 1) ? n : fibonacci(n - 1) + fibonacci(n - 2);
              store.set(n, fib);
          }
          return fib;
      }
  }
  ```
  
  **Erläuterung:**
  - Die Methode `fibonacci(long n)` prüft zunächst, ob das Ergebnis für `n` bereits im `FiboStore` vorhanden ist.
  - Falls nicht (`fib == null`), wird das Ergebnis rekursiv berechnet:
    - Für `n == 0` oder `n == 1` wird `n` direkt zurückgegeben.
    - Für `n > 1` werden `fibonacci(n-1)` und `fibonacci(n-2)` aufgerufen und deren Ergebnisse addiert.
  - Das Ergebnis wird im `FiboStore` gespeichert, um zukünftige Berechnungen zu vermeiden.
  - Der gespeicherte oder berechnete Wert wird zurückgegeben.
- **Theoretischer Bezug:** 
  - [[Dynamische_Programmierung|Dynamisches Programmieren]]
  - [[Rekursion|Rekursive Algorithmen]]
  - [[Sequenzdiagramm|Sequenzdiagramme]]
  - [[Memoization|Memoization]]
  - [[Klassendiagramm|Klassendiagramme]] (für die Struktur von `FiboSolver` und `FiboStore`)
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von Basisfällen (`n == 0` und `n == 1`) mit rekursiven Fällen, was zu unendlichen Rekursionen führen kann.
  - Vergessen, das Ergebnis im `FiboStore` zu speichern (`store.set(n, fib)`), wodurch die Optimierung durch [[Dynamische_Programmierung|Dynamisches Programmieren]] verloren geht.
  - Falsche Handhabung des `FiboStore`: Annahme, dass `get(n)` bereits Werte liefert, ohne dass `set(n, fib)` aufgerufen wurde.
  - Unklare Darstellung der Rekursion im Sequenzdiagramm, z. B. durch fehlende oder falsch platzierte Lebenslinien für rekursive Aufrufe.
  - Übersehen der Bedingung `0 <= n`, was zu falschen Rückgaben für negative `n` führen kann (obwohl die Fibonacci-Definition nur für `n ∈ N0` gilt).
