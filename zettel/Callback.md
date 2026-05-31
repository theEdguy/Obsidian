---
id: 2298e1eb-b227-41a4-a2cc-21005645591a
title: "Callback"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - asynchronitaet
  - event_handling
  - funktionale_programmierung
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Callback]]

- **Kernkonzept:** Ein **Callback** ist ein Programmiermuster, bei dem eine Funktion (oder ein Funktionsobjekt) als Argument an eine andere Funktion übergeben wird, um zu einem späteren Zeitpunkt – typischerweise nach Abschluss einer asynchronen Operation oder bei Eintritt eines bestimmten Ereignisses – aufgerufen zu werden. Callbacks ermöglichen die Entkopplung von [[Aufrufer]] und [[Aufgerufener]], indem sie die Steuerungshoheit an den Empfänger der Callback-Funktion delegieren. Sie sind ein zentrales Konzept in der ereignisgesteuerten Programmierung und bei der Implementierung von [[Asynchronität]] oder [[Event_Handling]].
- **Nutzen & Zweck:** Callbacks dienen folgenden Zwecken:
- **Asynchrone Verarbeitung**: Sie ermöglichen nicht-blockierende Operationen, z. B. bei Netzwerkrequests oder Datei-I/O, indem der Callback erst nach Abschluss der Operation ausgeführt wird.
- **Ereignisbehandlung**: Sie erlauben die Reaktion auf Ereignisse (z. B. Benutzereingaben, Timer, Systemereignisse) ohne starre [[Kontrollfluss]]-Strukturen wie Schleifen.
- **Erweiterbarkeit**: Durch die Übergabe von Callbacks kann Verhalten zur Laufzeit dynamisch angepasst werden, ohne die aufrufende Funktion zu modifizieren (Prinzip der [[Inversion_of_Control]]).
- **Entkopplung**: Sie reduzieren Abhängigkeiten zwischen Komponenten, da der Aufrufer nicht wissen muss, *wie* der Callback implementiert ist, sondern nur dessen [[Schnittstelle]].

Typische Anwendungsfälle sind:
- [[Observer_Pattern]] (z. B. Event-Listener in GUIs).
- [[Promise]]s oder [[Future]]s in asynchroner Programmierung.
- Middleware in Web-Frameworks (z. B. Express.js in Node.js).
- Hooks in Build-Systemen oder Test-Frameworks.
- **Abgrenzung & Grenzen:** Callbacks sind abzugrenzen von:
- **Polling**: Während Polling aktiv den Status einer Operation abfragt (z. B. in einer Schleife), wird ein Callback *passiv* aufgerufen, sobald das Ereignis eintritt.
- **[[Synchroner_Aufruf]]**: Bei synchronen Aufrufen blockiert der Aufrufer, bis die Funktion abgeschlossen ist. Callbacks ermöglichen dagegen nicht-blockierende Ausführung.
- **[[Delegates]] (C#) oder [[Function_Pointer]] (C/C++)**: Diese sind sprachspezifische Mechanismen zur Implementierung von Callbacks, aber nicht mit dem Muster selbst gleichzusetzen.

**Stolpersteine und Grenzen**:
- **Callback-Hell**: Tief verschachtelte Callbacks (z. B. bei mehreren asynchronen Operationen) führen zu schwer lesbarem Code. Abhilfe schaffen [[Promise]]s oder [[async/await]].
- **Kontextverlust**: Der `this`-Kontext kann in Callbacks verloren gehen, wenn sie nicht korrekt gebunden werden (z. B. mit `.bind()` in JavaScript oder Lambda-Ausdrücken in Java).
- **Fehlerbehandlung**: Ausnahmen in Callbacks müssen explizit behandelt werden, da sie sonst den gesamten [[Kontrollfluss]] unterbrechen können.
- **Thread-Sicherheit**: In multithreaded Umgebungen muss sichergestellt werden, dass Callbacks thread-sicher aufgerufen werden (z. B. durch [[Synchronisation]]).
- **Beispiel / Code:** {'beschreibung': 'Das folgende Java-Beispiel zeigt ein Callback zur asynchronen Verarbeitung einer Liste. Die `processList`-Methode akzeptiert einen Callback vom Typ `Consumer<Integer>`, der nach Abschluss der Verarbeitung aufgerufen wird. Dies demonstriert die Entkopplung von Verarbeitung und Ergebnisbehandlung.', 'code': {'java': 'import java.util.List;\nimport java.util.function.Consumer;\n\npublic class CallbackExample {\n    // Methode, die einen Callback akzeptiert\n    public void processList(List<Integer> numbers, Consumer<Integer> callback) {\n        for (Integer number : numbers) {\n            // Simuliere asynchrone Verarbeitung (z. B. Netzwerk-Request)\n            try {\n                Thread.sleep(100); // Verzögerung\n            } catch (InterruptedException e) {\n                Thread.currentThread().interrupt();\n            }\n            // Callback aufrufen\n            callback.accept(number * 2);\n        }\n    }\n\n    public static void main(String[] args) {\n        CallbackExample example = new CallbackExample();\n        List<Integer> numbers = List.of(1, 2, 3, 4);\n        \n        // Callback als Lambda-Ausdruck definieren\n        example.processList(numbers, result -> {\n            System.out.println("Ergebnis: " + result);\n        });\n        \n        System.out.println("Verarbeitung gestartet...");\n    }\n}'}, 'uml_diagramm': {'beschreibung': 'Ein [[Sequenzdiagramm]] zur Veranschaulichung des Callback-Ablaufs: Der `Aufrufer` übergibt einen Callback an die `Verarbeitungsmethode`, die diesen nach Abschluss der Operation aufruft.', 'mermaid': 'sequenceDiagram\n    participant Aufrufer\n    participant Verarbeitungsmethode\n    participant Callback\n    \n    Aufrufer->>Verarbeitungsmethode: processList(numbers, callback)\n    loop Für jedes Element in numbers\n        Verarbeitungsmethode->>Verarbeitungsmethode: Verarbeite Element (asynchron)\n        Verarbeitungsmethode->>Callback: accept(ergebnis)\n        Callback->>Aufrufer: Ergebnis verarbeiten\n    end'}}
