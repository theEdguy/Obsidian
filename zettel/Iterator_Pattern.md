---
id: 31e9b7e8-7ae2-4717-aaef-60fd6e904a52
title: "Iterator_Pattern"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - verhaltensmuster
  - datenstrukturen
  - uml
  - java
  - iterator
  - warteschlange
  - traversierung
  - draft
source: "Klausur_Referenz"
---

# [[Iterator_Pattern]]

- **Kernkonzept:** Das [[Iterator_Pattern]] ist ein [[Verhaltensmuster]] in der Softwareentwicklung, das den sequenziellen Zugriff auf die Elemente einer [[Datenstruktur]] (z. B. Listen, Bäume, Warteschlangen) ermöglicht, ohne deren interne Repräsentation offenzulegen. Es kapselt die Iterationslogik in einem separaten Objekt (dem Iterator) und trennt so die Traversierung der Daten von deren Nutzung. Der Iterator stellt typischerweise Methoden wie `next()`, `hasNext()` oder `remove()` bereit, um die Elemente nacheinander zu durchlaufen.
- **Nutzen & Zweck:** Das Muster wird verwendet, um:
- **Kapselung** zu fördern: Die interne Struktur der [[Datenstruktur]] bleibt verborgen, was die [[Kohäsion]] erhöht und [[Kopplung]] reduziert.
- **Flexibilität** zu ermöglichen: Verschiedene Iterationsstrategien (z. B. vorwärts, rückwärts, gefiltert) können ohne Änderung der [[Datenstruktur]] implementiert werden.
- **Einheitliche Schnittstellen** zu schaffen: Unterschiedliche [[Datenstrukturen]] können über dieselbe [[Schnittstelle]] traversiert werden (z. B. `java.util.Iterator` in Java).
- **Mehrfachiteration** zu unterstützen: Mehrere Iteratoren können unabhängig voneinander dieselbe [[Datenstruktur]] durchlaufen.

Typische Anwendungsfälle sind das Durchlaufen von Collections, das Parsen von Datenströmen oder die Implementierung von [[Warteschlangen]] (wie im gegebenen Kontext).
- **Abgrenzung & Grenzen:** Abgrenzung zu ähnlichen Konzepten:
- **[[Besucher_Pattern]]**: Während das [[Iterator_Pattern]] die Traversierung kapselt, ermöglicht das [[Besucher_Pattern]] zusätzlich die Ausführung von Operationen auf den Elementen während der Traversierung.
- **Direkte Schleifen**: Iteratoren sind mächtiger als einfache `for`- oder `while`-Schleifen, da sie zustandsbehaftet sind und komplexe Iterationslogik kapseln können.

Grenzen und Stolpersteine:
- **Thread-Sicherheit**: Iteratoren sind oft nicht thread-sicher. Bei gleichzeitigen Modifikationen der [[Datenstruktur]] während der Iteration können `ConcurrentModificationException` (Java) oder undefiniertes Verhalten auftreten.
- **Performance-Overhead**: Iteratoren können zusätzlichen Speicher- oder Rechenaufwand verursachen, insbesondere bei großen [[Datenstrukturen]].
- **Fehlende Persistenz**: Iteratoren sind meist nicht persistent – ihr Zustand geht verloren, wenn die [[Datenstruktur]] verändert wird.
- **Komplexität bei verschachtelten Strukturen**: Für hierarchische [[Datenstrukturen]] (z. B. Bäume) sind spezielle Iteratoren (z. B. [[Tiefensuche]], [[Breitensuche]]) erforderlich.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt die Implementierung eines Iterators für eine [[FiFo_Warteschlange]] (First-In-First-Out) in Java, basierend auf dem gegebenen Kontext. Die Warteschlange speichert `Job`-Objekte, und der Iterator durchläuft sie in der Reihenfolge der Entnahme (FIFO).', 'uml_sequenzdiagramm': {'beschreibung': 'Sequenzdiagramm für die `next()`-Operation des Iterators (textuelle Darstellung in Mermaid-Syntax):', 'mermaid': 'sequenceDiagram\n    participant Client\n    participant Iterator\n    participant FiFo\n    participant Elem\n    \n    Client->>Iterator: next()\n    Iterator->>Iterator: hasNext()\n    alt hasNext() == true\n        Iterator->>Elem: getNext()\n        Elem-->>Iterator: currentElem\n        Iterator->>Elem: getNext().getNext()\n        Elem-->>Iterator: nextElem\n        Iterator->>Iterator: setNext(nextElem)\n        Iterator-->>Client: currentElem\n    else hasNext() == false\n        Iterator-->>Client: NoSuchElementException\n    end'}, 'java_code': {'beschreibung': 'Implementierung der Iterator-Klasse für die FiFo-Warteschlange:', 'code': 'public class FiFo<E> {\n    private Elem<E> first;\n    private Elem<E> last;\n    \n    // Innere Klasse für Listenelemente\n    private static class Elem<E> {\n        E value;\n        Elem<E> next;\n        \n        Elem(E value) {\n            this.value = value;\n            this.next = null;\n        }\n    }\n    \n    // Iterator-Klasse\n    public static class Iter<E> implements Iterator<E> {\n        private Elem<E> next;\n        \n        public Iter(FiFo<E> fifo) {\n            this.next = fifo.first; // Initialisiere mit dem ersten Element der Warteschlange\n        }\n        \n        @Override\n        public boolean hasNext() {\n            return next != null;\n        }\n        \n        @Override\n        public E next() {\n            if (!hasNext()) {\n                throw new NoSuchElementException("Keine weiteren Elemente in der Warteschlange.");\n            }\n            E value = next.value;\n            next = next.next; // Setze den Iterator auf das nächste Element\n            return value;\n        }\n    }\n    \n    // Methoden der FiFo-Klasse (Ausschnitt)\n    public void enqueue(E value) {\n        Elem<E> newElem = new Elem<>(value);\n        if (last == null) {\n            first = last = newElem;\n        } else {\n            last.next = newElem;\n            last = newElem;\n        }\n    }\n    \n    public E dequeue() {\n        if (first == null) {\n            throw new NoSuchElementException("Warteschlange ist leer.");\n        }\n        E value = first.value;\n        first = first.next;\n        if (first == null) {\n            last = null;\n        }\n        return value;\n    }\n    \n    public Iterator<E> iterator() {\n        return new Iter<>(this);\n    }\n}'}}
