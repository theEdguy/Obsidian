---
id: 4e97a642-5069-4d9e-999f-c9883828caf2
title: "Builder"
date: 2026-06-23
tags:
  - software_engineering
  - builder
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Builder]]

- **Kernkonzept:** Das Builder-Entwurfsmuster ist ein objektorientiertes Konstruktionsmuster, das die schrittweise Erstellung komplexer Objekte von ihrer Repräsentation trennt, um denselben Konstruktionsprozess für verschiedene Darstellungen zu ermöglichen.
- **Nutzen & Zweck:** Der Builder löst das Problem der übermäßig komplexen oder unübersichtlichen Objekterzeugung, insbesondere wenn ein Objekt viele optionale Parameter oder Konfigurationsschritte benötigt. Es ermöglicht eine klare, lesbare und wartbare Trennung zwischen der Konstruktion eines Objekts und seiner endgültigen Form, was die Flexibilität und Wiederverwendbarkeit des Codes erhöht. Zudem verhindert es die Notwendigkeit von Teleskop-Konstruktoren oder unübersichtlichen Parameterlisten.
- **Abgrenzung & Grenzen:** Der Builder sollte nicht eingesetzt werden, wenn die Objekterzeugung einfach ist und nur wenige Parameter erfordert, da der zusätzliche Aufwand für die Implementierung des Musters in solchen Fällen unnötig ist. Alternativen wie Factory-Methoden oder einfache Konstruktoren sind hier oft effizienter. Zudem eignet sich der Builder weniger für Objekte, die nach ihrer Erstellung häufig verändert werden müssen, da er primär auf die initiale Konstruktion abzielt. Im Vergleich zu anderen Erzeugungsmustern wie dem Abstract Factory liegt der Fokus des Builders auf der schrittweisen und kontrollierten Erstellung eines einzelnen, komplexen Objekts.
- **Beispiel / Code:** ```java
// Beispiel für das Builder-Muster in Java
public class Pizza {
    private final String teig;
    private final String sauce;
    private final String belag;

    private Pizza(Builder builder) {
        this.teig = builder.teig;
        this.sauce = builder.sauce;
        this.belag = builder.belag;
    }

    public static class Builder {
        private String teig;
        private String sauce;
        private String belag;

        public Builder teig(String teig) {
            this.teig = teig;
            return this;
        }

        public Builder sauce(String sauce) {
            this.sauce = sauce;
            return this;
        }

        public Builder belag(String belag) {
            this.belag = belag;
            return this;
        }

        public Pizza build() {
            return new Pizza(this);
        }
    }
}

// Verwendung
Pizza pizza = new Pizza.Builder()
    .teig("Vollkorn")
    .sauce("Tomate")
    .belag("Käse")
    .build();
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7a4
- **Vorgänger / Parent:** [[Erzeugungsmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Erzeugungsmuster]]
  - [[Design_Pattern]]
