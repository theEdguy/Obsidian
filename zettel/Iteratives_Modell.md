---
id: 0bb0fb0f-2c1c-43c8-8f02-195777b74278
title: "Iteratives_Modell"
date: 2026-05-30
tags:
  - software_engineering
  - vorgehensmodell
  - agile_entwicklung
  - softwarearchitektur
  - use_case
  - refactoring
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Iteratives_Modell]]

- **Kernkonzept:** Das **Iterative_Modell** ist ein [[Vorgehensmodell]] im [[Software_Engineering]], bei dem die Entwicklung eines Systems in wiederholten Zyklen (Iterationen) erfolgt. Jede Iteration durchläuft die Phasen [[Anforderungsanalyse]], [[Systemdesign]], [[Implementierung]] und [[Testen]], wobei das System schrittweise verfeinert und erweitert wird. Im Gegensatz zum [[Wasserfallmodell]] ermöglicht das iterative Modell frühzeitiges Feedback, inkrementelle Verbesserungen und Anpassungen an sich ändernde Anforderungen.
- **Nutzen & Zweck:** Das iterative Modell wird eingesetzt, um komplexe Systeme flexibel und risikoarm zu entwickeln. Es bietet folgende Vorteile:
- **Frühe Lieferung von Teilergebnissen**: Stakeholder erhalten früh nutzbare Funktionalitäten.
- **Anpassungsfähigkeit**: Änderungen an Anforderungen oder Designentscheidungen können in späteren Iterationen berücksichtigt werden.
- **Risikominimierung**: Kritische Use Cases werden priorisiert und früh umgesetzt, um technische oder fachliche Risiken zu identifizieren.
- **Kontinuierliche Verbesserung**: Durch regelmäßige [[Refactoring]]-Schritte und Tests wird die Codequalität gesteigert.
- **Transparenz**: Fortschritt und Probleme werden durch die zyklische Natur des Modells sichtbar.

Typische Anwendungsbereiche sind agile Projekte, Prototyping oder die Entwicklung von Systemen mit unklaren oder sich ändernden Anforderungen.
- **Abgrenzung & Grenzen:** Das iterative Modell ist nicht für alle Projekte geeignet:
- **Grenzen**: Bei stark regulierten oder sicherheitskritischen Systemen (z. B. Luftfahrt, Medizin) kann der Dokumentationsaufwand durch häufige Iterationen steigen. Hier sind hybride Ansätze (z. B. Kombination mit [[V-Modell]]) sinnvoll.
- **Stolpersteine**: 
  - **Scope Creep**: Unkontrollierte Erweiterung der Anforderungen durch fehlende Priorisierung.
  - **Technische Schulden**: Durch schnelle Iterationen können Designentscheidungen vernachlässigt werden, was zu späteren [[Refactoring]]-Aufwänden führt.
  - **Dokumentation**: Modelle und Dokumente müssen nach jeder Iteration aktualisiert werden, um Konsistenz zu wahren.
  - **Teamkoordination**: Erfordert disziplinierte Kommunikation und klare [[Schnittstellen]] zwischen Teams, um Parallelentwicklungen zu synchronisieren.

Abzugrenzen ist das iterative Modell vom [[Spiralmodell]], das zusätzlich explizite Risikoanalysen in jeder Iteration vorsieht, sowie von rein sequenziellen Modellen wie dem [[Wasserfallmodell]].
- **Beispiel / Code:** ```mermaid
flowchart TD
    A[Iteration 1: Kernfunktionalität] --> B[Analyse: Use Cases priorisieren]
    B --> C[Design: Architektur entwerfen]
    C --> D[Implementierung: MVP umsetzen]
    D --> E[Testen: Validierung]
    E --> F[Feedback einarbeiten]
    F --> G[Iteration 2: Erweiterte Features]
    G --> B
```

**Beispiel (Java-Code-Snippet für eine Iteration in einem E-Commerce-System):**
```java
// Iteration 1: Grundlegende Warenkorb-Funktionalität
public class ShoppingCart {
    private List<Item> items;

    public void addItem(Item item) {
        items.add(item);
    }

    public double calculateTotal() {
        return items.stream().mapToDouble(Item::getPrice).sum();
    }
}

// Iteration 2: Erweiterte Features (z. B. Rabatte)
public class ShoppingCart {
    private List<Item> items;
    private DiscountStrategy discountStrategy;

    public void setDiscountStrategy(DiscountStrategy strategy) {
        this.discountStrategy = strategy;
    }

    public double calculateTotal() {
        double subtotal = items.stream().mapToDouble(Item::getPrice).sum();
        return discountStrategy.applyDiscount(subtotal);
    }
}
```
