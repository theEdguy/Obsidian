---
id: bc365d30-66fd-40b8-9637-7eb3b247613b
title: "Warteschlange_FIFO"
date: 2026-05-31
tags:
  - software_engineering
  - datenstrukturen
  - algorithmen
  - entwurfsmuster
  - uml
  - java
  - nebenlaeufigkeit
  - draft
source: "Klausur_Referenz"
---

# [[Warteschlange_FIFO]]

- **Kernkonzept:** Eine [[Warteschlange]] (engl. *Queue*) ist eine abstrakte [[Datenstruktur]], die nach dem **FIFO-Prinzip** (*First In, First Out*) arbeitet. Elemente werden am Ende der Schlange eingefügt (*Enqueue*) und am Anfang entnommen (*Dequeue*). Dies modelliert reale Wartesysteme (z. B. Druckaufträge, Prozess-Scheduling) und dient als Grundlage für komplexere [[Algorithmen]] wie [[Breitensuche]] oder [[Pufferung]] in Netzwerken.
- **Nutzen & Zweck:** Warteschlangen ermöglichen die **entkoppelte Verarbeitung** von Datenströmen, indem sie temporäre Speicherung und sequenzielle Abarbeitung garantieren. Typische Anwendungen:
- **Task-Scheduling** (z. B. [[Thread-Pool]] in Betriebssystemen)
- **Nachrichtenübermittlung** (z. B. [[Message_Queue]] in verteilten Systemen)
- **Pufferung** (z. B. Tastatureingaben, Netzwerkpakete)
- **Ereignisverarbeitung** (z. B. [[Event_Driven_Architecture]]).
Durch die strikte FIFO-Ordnung wird **Determinismus** in der Verarbeitungsreihenfolge sichergestellt, was für [[Nebenläufigkeit]] und [[Synchronisation]] essenziell ist.
- **Abgrenzung & Grenzen:** 1. **Kein wahlfreier Zugriff**: Im Gegensatz zu [[Liste]]n oder [[Array]]s ist nur das erste/letzte Element direkt zugänglich.
2. **Speicherbedarf**: Dynamische Warteschlangen (z. B. [[Linked_List]]-Implementierung) verursachen Overhead durch Zeigerstrukturen.
3. **Blockierende Operationen**: Bei leerer Schlange führt *Dequeue* zu Fehlern oder Blockaden (Lösungen: [[Null_Object_Pattern]] oder [[Blocking_Queue]]).
4. **Priorisierung**: Standard-Warteschlangen ignorieren Prioritäten – hierfür sind [[Priority_Queue]]s oder [[Heap]]-Strukturen nötig.
5. **Iterator-Design**: Ein [[Iterator]] muss die FIFO-Ordnung respektieren, darf aber die Schlange nicht modifizieren (vgl. [[Fail_Fast_Iterator]]).
- **Beispiel / Code:** {'uml_beschreibung': 'classDiagram\n    class Queue {\n        +enqueue(element: Object): void\n        +dequeue(): Object\n        +isEmpty(): boolean\n        +iterator(): Iterator~Object~\n    }\n    class QueueIterator {\n        -current: Node\n        +hasNext(): boolean\n        +next(): Object\n    }\n    Queue --> QueueIterator : <<creates>>\n    Queue *-- Node : <<composes>>\n    class Node {\n        +data: Object\n        +next: Node\n    }', 'java_implementierung': 'public class Queue<T> implements Iterable<T> {\n    private static class Node<T> {\n        T data;\n        Node<T> next;\n        Node(T data) { this.data = data; }\n    }\n    private Node<T> head, tail;\n\n    public void enqueue(T element) {\n        Node<T> newNode = new Node<>(element);\n        if (tail == null) {\n            head = tail = newNode;\n        } else {\n            tail.next = newNode;\n            tail = newNode;\n        }\n    }\n\n    public T dequeue() {\n        if (head == null) throw new NoSuchElementException();\n        T data = head.data;\n        head = head.next;\n        if (head == null) tail = null;\n        return data;\n    }\n\n    @Override\n    public Iterator<T> iterator() {\n        return new QueueIterator();\n    }\n\n    private class QueueIterator implements Iterator<T> {\n        private Node<T> current = head;\n\n        @Override\n        public boolean hasNext() {\n            return current != null;\n        }\n\n        @Override\n        public T next() {\n            if (!hasNext()) throw new NoSuchElementException();\n            T data = current.data;\n            current = current.next;\n            return data;\n        }\n    }\n}', 'hinweis': 'Der Iterator implementiert das [[Iterator_Pattern]] und ermöglicht das Durchlaufen der Schlange ohne deren interne Struktur offenzulegen. Die `next()`-Methode wirft eine `NoSuchElementException`, falls die Schlange leer ist (vgl. [[Fail_Fast_Iterator]]).'}
