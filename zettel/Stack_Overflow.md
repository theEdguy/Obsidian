---
id: 9a3173ac-e162-4dbd-ad66-cb1027d904f3
title: "Stack_Overflow"
date: 2026-05-31
tags:
  - software_engineering
  - fehlerbehandlung
  - rekursion
  - speicherverwaltung
  - algorithmen
  - laufzeitfehler
  - draft
source: "Klausur_Referenz"
---

# [[Stack_Overflow]]

- **Kernkonzept:** Ein **Stack_Overflow** (Stapelüberlauf) ist ein Laufzeitfehler, der auftritt, wenn der [[Call_Stack]] eines Programms seine maximale Kapazität überschreitet. Dies geschieht typischerweise durch eine unkontrollierte Rekursion oder eine extrem tiefe Verschachtelung von Funktionsaufrufen, wodurch der verfügbare Speicher für den Stack erschöpft wird. Der Fehler führt in der Regel zum Absturz des Programms mit einer entsprechenden Fehlermeldung (z. B. `StackOverflowError` in Java).
- **Nutzen & Zweck:** Das Verständnis von **Stack_Overflow** ist essenziell für die Fehleranalyse und -vermeidung in der Softwareentwicklung. Es hilft Entwicklern, rekursive Algorithmen korrekt zu implementieren (z. B. mit [[Basisfall]] in der Rekursion) und Speichergrenzen von [[Call_Stack]]s zu berücksichtigen. Zudem dient es als Warnsignal für ineffiziente oder fehlerhafte Programmstrukturen, insbesondere in Systemen mit begrenzten Ressourcen (z. B. Embedded-Systeme).
- **Abgrenzung & Grenzen:** **Stack_Overflow** ist abzugrenzen von anderen Speicherfehlern wie [[Heap_Overflow]] oder [[Out_of_Memory_Error]], die den dynamischen Speicher betreffen. Während ein **Stack_Overflow** durch zu viele verschachtelte Aufrufe entsteht, resultieren die anderen Fehler aus übermäßiger Speicherallokation (z. B. durch große Objekte oder Speicherlecks). Typische Stolpersteine sind:
- Fehlende oder falsche Basisfälle in rekursiven Funktionen.
- Unbeabsichtigte Rekursion (z. B. durch zyklische Abhängigkeiten in [[Objektgraph]]en).
- Zu große lokale Variablen oder Parameter, die den Stack pro Aufruf überlasten.
- Unzureichende Stack-Größen in Threads (konfigurierbar in einigen Laufzeitumgebungen).
- **Beispiel / Code:** ```java
// Beispiel für einen StackOverflow durch unendliche Rekursion
public class StackOverflowExample {
    public static void main(String[] args) {
        recursiveMethod(); // Führt zu StackOverflowError
    }
    
    public static void recursiveMethod() {
        recursiveMethod(); // Kein Basisfall -> unendliche Rekursion
    }
}

// Korrekte Rekursion mit Basisfall
public class CorrectRecursion {
    public static void main(String[] args) {
        System.out.println(factorial(5)); // Ausgabe: 120
    }
    
    public static int factorial(int n) {
        if (n <= 1) { // Basisfall
            return 1;
        }
        return n * factorial(n - 1); // Rekursiver Aufruf
    }
}
```
