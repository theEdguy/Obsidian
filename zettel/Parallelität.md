---
id: f889abe3-f2b6-4921-9c11-507af15dc4e1
title: "Parallelität"
date: 2026-06-23
tags:
  - software_engineering
  - verteilte_systeme
  - architektur
  - performance
  - prozesse
  - threads
  - verteilte-systeme
  - parallelverarbeitung
  - kontextwechsel
  - uml-fragment
  - kontrollfluss
  - draft
source: "software_engineering_kapitel_13"
---

# [[Parallelität]]

- **Kernkonzept:** [[Parallelität]] beschreibt die Fähigkeit eines [[System|Systems]], mehrere [[Berechnung|Berechnungen]], [[Prozess|Prozesse]] oder [[Thread|Threads]] gleichzeitig auszuführen, um die [[Performance]] zu steigern und [[Ressource|Ressourcen]] effizient zu nutzen. Dies umfasst sowohl die technische Umsetzung auf [[Hardware]]-Ebene (z. B. [[Multicore-Prozessor|Multicore-Prozessoren]]) als auch die modellbasierte Darstellung in [[UML-Interaktionsdiagramm|UML-Interaktionsdiagrammen]], wo parallele [[Ablauf|Abläufe]] als Fragmente abgebildet werden.
- **Nutzen & Zweck:** [[Parallelität]] ermöglicht die gleichzeitige Bearbeitung mehrerer [[Aufgabe|Aufgaben]], verbessert die [[Skalierbarkeit]] und [[Reaktionszeit]] von [[System|Systemen]] und löst [[Blockierung|Blockierungen]] bei [[Ein-/Ausgabe-Operation|Ein-/Ausgabe-Operationen]]. Sie ist essenziell für [[Echtzeitsystem|Echtzeitsysteme]] und hochperformante [[Anwendung|Anwendungen]], da sie [[Netzwerklatenz]] verdeckt und die [[Durchsatzrate]] erhöht. In der [[Modellierung]] (z. B. [[UML]]) dient [[Parallelität]] dazu, nebenläufige [[Prozess|Prozesse]] oder asynchrone [[Operation|Operationen]] in [[Sequenzdiagramm|Sequenzdiagrammen]] abzubilden, was die Kommunikation zwischen [[Entwickler|Entwicklern]] und [[Stakeholder|Stakeholdern]] über zeitlich unabhängige [[Vorgang|Vorgänge]] erleichtert. Besonders wertvoll ist dies in [[Verteilte Systeme|verteilten Systemen]] oder [[Event-gesteuertes_System|Event-gesteuerten Systemen]], wo [[Multithreading]] oder verteilte [[Verarbeitung]] modelliert werden müssen.
- **Abgrenzung & Grenzen:** [[Parallelität]] ist kein Ersatz für [[Nebenläufigkeit]], die sich auf die Verwaltung und Koordination von [[Prozess|Prozessen]] und [[Thread|Threads]] konzentriert. Sie erfordert spezifische [[Hardware]]-Unterstützung (z. B. [[Multicore-Prozessor|Multicore-Prozessoren]]) und erhöht im Vergleich zur [[Sequenzielle_Abarbeitung|sequenziellen Abarbeitung]] die Komplexität des [[System|Systems]]. [[Parallelität]] sollte vermieden werden, wenn [[Aufgabe|Aufgaben]] stark voneinander abhängig sind oder der [[Overhead]] für [[Kontextwechsel]] die Leistungsvorteile überwiegt. Typische Herausforderungen sind [[Race Condition|Race Conditions]] und [[Deadlock|Deadlocks]], die durch sorgfältiges [[Synchronisation|Synchronisationsmanagement]] adressiert werden müssen. 

In der [[Modellierung]] (z. B. [[UML]]) ist [[Parallelität]] ungeeignet für streng sequenzielle oder abhängige [[Ablauf|Abläufe]], da dies die Lesbarkeit von [[Diagramm|Diagrammen]] erschwert. Im Gegensatz zu [[Kontrollstruktur|Kontrollstrukturen]] wie [[Alternative]] oder [[Option]] modelliert [[Parallelität]] keine bedingten Pfade, sondern explizit gleichzeitige Ausführungen. Für einfache [[System|Systeme]] mit linearer [[Logik]] ist der Einsatz überflüssig und kann zu Missverständnissen führen. Zudem können zeitliche [[Abhängigkeit|Abhängigkeiten]] oder [[Synchronisation|Synchronisationspunkte]] nicht detailliert abgebildet werden – hierfür sind zusätzliche [[Notation|Notationen]] oder separate [[Diagramm|Diagramme]] erforderlich.
- **Beispiel / Code:** ```java
// Beispiel 1: Parallelität in Java (ExecutorService)
ExecutorService executor = Executors.newFixedThreadPool(4);
for (int i = 0; i < 10; i++) {
    executor.submit(() -> {
        // Aufgabe parallel ausführen
    });
}
executor.shutdown();

// Beispiel 2: Multithreaded-Webserver zur parallelen Bearbeitung von Client-Anfragen
new Thread(() -> {
    try {
        handleRequest(clientSocket);
    } catch (IOException e) {
        e.printStackTrace();
    }
}).start();

// Beispiel 3: Parallelität in UML-Sequenzdiagrammen (Pseudocode-Darstellung)
parallel {
    // Ablauf 1: Datenbankabfrage (unabhängig von Ablauf 2)
    [[Nutzer]] -> [[Datenbank]]: Anfrage(stellen);
    [[Datenbank]] -> [[Nutzer]]: Ergebnis(liefern);
    
    // Ablauf 2: Benachrichtigung senden
    [[Nutzer]] -> [[Nachrichtensystem]]: Sende(Benachrichtigung);
    [[Nachrichtensystem]] -> [[Nutzer]]: Bestätigung;
}
```

// In einem UML-Sequenzdiagramm wird dies als 'par'-Fragment dargestellt:
// - Die [[Lebenslinie|Lebenslinien]] der [[Objekt|Objekte]] bleiben erhalten.
// - Die [[Nachricht|Nachrichten]] innerhalb des Fragments laufen parallel ab.
// - Das Fragment endet, wenn alle parallelen [[Ablauf|Abläufe]] abgeschlossen sind.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c4
- **Vorgänger / Parent:** [[Nachrichtenfragment]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
