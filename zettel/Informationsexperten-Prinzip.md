---
id: f3b4e71a-5595-4c57-8245-2b8707afbe18
title: "Informationsexperten-Prinzip"
date: 2026-06-23
tags:
  - software_engineering
  - designprinzip
  - verantwortung
  - draft
source: "software_engineering_kapitel_13"
---

# [[Informationsexperten-Prinzip]]

- **Kernkonzept:** Das Informationsexperten-Prinzip ist ein zentrales Designprinzip im objektorientierten Software-Engineering, das besagt, dass Verantwortlichkeiten für eine bestimmte Aufgabe der Klasse zugewiesen werden sollten, die über die meisten Informationen verfügt, um diese Aufgabe zu erfüllen. Es fördert die natürliche Verteilung von Wissen und Logik innerhalb eines Systems.
- **Nutzen & Zweck:** Dieses Prinzip existiert, um die Kohäsion und Wartbarkeit von Software zu erhöhen. Es löst das Problem der unklaren Verantwortungsverteilung in komplexen Systemen, indem es sicherstellt, dass Klassen nur die Aufgaben übernehmen, für die sie die notwendigen Daten und Kenntnisse besitzen. Dadurch wird die Kopplung reduziert, die Verständlichkeit des Codes verbessert und die Fehleranfälligkeit verringert, da Logik dort platziert wird, wo sie am sinnvollsten ist.
- **Abgrenzung & Grenzen:** Das Informationsexperten-Prinzip sollte nicht angewendet werden, wenn es zu einer übermäßigen Zentralisierung von Verantwortung führt oder wenn die Klasse, die die meisten Informationen besitzt, bereits zu viele Aufgaben übernimmt (Verstoß gegen das Prinzip der hohen Kohäsion). Alternativen wie das Delegationsprinzip oder das Erzeuger-Prinzip können in solchen Fällen sinnvoller sein. Zudem ist es ungeeignet, wenn die benötigten Informationen über mehrere Klassen verteilt sind und keine klare Zuordnung möglich ist, da dies zu unnötiger Komplexität führen kann.
- **Beispiel / Code:** ```java
// Beispiel: Eine Bestellungsklasse, die den Gesamtpreis berechnet, da sie alle notwendigen Informationen (die einzelnen Posten) besitzt.
public class Order {
    private List<OrderItem> items;

    public double calculateTotalPrice() {
        double total = 0.0;
        for (OrderItem item : items) {
            total += item.getPrice() * item.getQuantity();
        }
        return total;
    }
}

// Falsche Anwendung: Eine andere Klasse berechnet den Preis, obwohl sie die Daten nicht direkt besitzt.
public class PriceCalculator {
    public double calculateTotalPrice(Order order) {
        double total = 0.0;
        for (OrderItem item : order.getItems()) {
            total += item.getPrice() * item.getQuantity();
        }
        return total;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1
- **Vorgänger / Parent:** [[Objektorientierte_Analyse_und_Design]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
