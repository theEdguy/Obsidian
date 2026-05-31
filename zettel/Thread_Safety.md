---
id: 865a2bc3-34bf-4b3c-8de3-72ceecd53ba2
title: "Thread_Safety"
date: 2026-05-31
tags:
  - software_engineering
  - multithreading
  - entwurfsmuster
  - konkurrenz
  - synchronisation
  - datenstrukturen
  - java
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Thread_Safety]]

- **Kernkonzept:** Thread_Safety (Faden- oder Threadsicherheit) bezeichnet die Eigenschaft eines [[Programmmoduls]], [[Algorithmus]] oder [[Datenstruktur]], korrekt zu funktionieren, wenn es gleichzeitig von mehreren [[Threads]] eines [[Prozesses]] genutzt wird. Ein thread-sicheres System garantiert, dass durch parallele Zugriffe keine [[Race_Conditions]], [[Deadlocks]] oder inkonsistente Zustände entstehen. Dies wird oft durch Synchronisationsmechanismen wie [[Locks]], [[Mutex]] oder [[Atomare_Operationen]] erreicht, die den exklusiven Zugriff auf kritische Abschnitte regeln.
- **Nutzen & Zweck:** Thread_Safety ist essenziell in [[Multithreading]]-Umgebungen, um die [[Konsistenz]] von Daten und die [[Korrektheit]] von Programmen zu gewährleisten. Sie ermöglicht die effiziente Nutzung von Mehrkernprozessoren durch parallele Ausführung, ohne dass unerwartete Fehler (z. B. durch [[Race_Conditions]]) auftreten. Typische Anwendungsfälle sind [[Serveranwendungen]], [[Datenbanken]] (z. B. [[Hibernate]]-Sessions) oder [[Echtzeitsysteme]], bei denen mehrere [[Threads]] auf gemeinsame Ressourcen zugreifen. Thread-Safety ist zudem eine Voraussetzung für viele [[Entwurfsmuster]] wie [[Active_Object]] oder [[Monitor_Object]].
- **Abgrenzung & Grenzen:** Thread_Safety ist **nicht** gleichbedeutend mit Performance: Synchronisation kann zu [[Performance_Overhead]] oder [[Deadlocks]] führen, wenn sie falsch eingesetzt wird. Zudem garantiert Thread-Safety keine [[Skalierbarkeit]] – bei hoher [[Concurrency]] können [[Lock_Contention]] oder [[Thread_Starvation]] auftreten. Thread-Safety bezieht sich **nur auf den Zugriff durch Threads desselben Prozesses**; für [[Interprozesskommunikation]] sind zusätzliche Mechanismen wie [[Semaphore]] oder [[Message_Passing]] nötig. Typische Stolpersteine sind:
- **Falsche Granularität**: Zu grobe Locks (z. B. ein globaler Lock für alle Operationen) reduzieren die Parallelität, zu feine Locks erhöhen den Overhead.
- **Vergessene Synchronisation**: Selbst scheinbar harmlose Operationen (z. B. `i++`) können in [[Multithreading]] zu Fehlern führen.
- **[[Deadlocks]]**: Durch zyklische Abhängigkeiten von Locks.
- **[[Starvation]]**: Wenn Threads dauerhaft von Ressourcen ausgeschlossen werden.
- **[[Memory_Visibility]]**: Ohne Synchronisation können Änderungen an Variablen für andere Threads unsichtbar bleiben (z. B. durch [[CPU_Cache]]-Effekte).
- **Beispiel / Code:** {'beschreibung': 'Ein thread-sicheres Singleton in Java mit [[Double_Checked_Locking]] (ab Java 5 mit `volatile` korrigiert):', 'code': 'public class ThreadSafeSingleton {\n    private static volatile ThreadSafeSingleton instance;\n\n    private ThreadSafeSingleton() {}\n\n    public static ThreadSafeSingleton getInstance() {\n        if (instance == null) {  // Erster Check (ohne Lock)\n            synchronized (ThreadSafeSingleton.class) {\n                if (instance == null) {  // Zweiter Check (mit Lock)\n                    instance = new ThreadSafeSingleton();\n                }\n            }\n        }\n        return instance;\n    }\n}', 'alternative': {'beschreibung': 'Thread-Safety durch [[Immutable_Objects]] (unveränderliche Objekte):', 'code': 'public final class ImmutablePoint {\n    private final int x;\n    private final int y;\n\n    public ImmutablePoint(int x, int y) {\n        this.x = x;\n        this.y = y;\n    }\n\n    public int getX() { return x; }\n    public int getY() { return y; }\n    // Keine Setter – Objekt kann sicher von mehreren Threads gelesen werden.\n}'}, 'uml': {'beschreibung': 'UML-Klassendiagramm für ein thread-sicheres [[Producer_Consumer_Pattern]] mit [[Monitor_Object]]:', 'diagramm': 'classDiagram\n    class SharedBuffer {\n        -buffer: List~Object~\n        -lock: Object\n        +put(item: Object) void\n        +take(): Object\n    }\n    class Producer {\n        +run() void\n    }\n    class Consumer {\n        +run() void\n    }\n    Producer --> SharedBuffer : uses\n    Consumer --> SharedBuffer : uses\n    note for SharedBuffer\n        synchronized put() {\n            while (buffer.isFull()) wait();\n            buffer.add(item);\n            notifyAll();\n        }\n        synchronized take() {\n            while (buffer.isEmpty()) wait();\n            Object item = buffer.remove();\n            notifyAll();\n            return item;\n        }\n    end note'}}
