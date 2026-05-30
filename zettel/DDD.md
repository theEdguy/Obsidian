---
id: 745398f9-55ee-4bfa-be01-646cb2c8155f
title: "DDD"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsansatz
  - draft
source: "SWE Slides (Folien 46-60)"
---

# [[DDD]]

- **Kernkonzept:** [[Domain_Driven_Design|DDD]] (Domain-Driven Design) ist ein [[Entwurfsansatz]], der die [[Softwareentwicklung]] auf die [[Fachdomäne]] ausrichtet. Es betont die Bedeutung einer [[Ubiquitous_Language]] und die Modellierung von [[Domänenmodell|Domänenmodellen]] mit [[Entität|Entitäten]], [[Wertobjekt|Wertobjekten]] und [[Aggregat|Aggregaten]].
- **Nutzen & Zweck:** Es löst das Problem der [[Komplexität]] in [[Softwareprojekt|Softwareprojekten]] durch eine klare [[Modellierung]] der [[Fachdomäne]] und verbessert die [[Kommunikation]] zwischen [[Entwickler|Entwicklern]] und [[Fachexperte|Fachexperten]].
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Anwendung|Anwendungen]] mit geringer [[Fachdomäne|Domänenkomplexität]]. Unterscheidet sich von [[Datengetriebener_Entwurf|datengetriebenen Ansätzen]] durch den Fokus auf die [[Fachdomäne]] statt auf die [[Datenbank]].
- **Beispiel / Code:** Beispiel für ein [[Aggregat]] in [[DDD]]:

```java
public class Order {
    private OrderId id;
    private List<OrderItem> items;
    private Customer customer;

    public void addItem(Product product, int quantity) {
        items.add(new OrderItem(product, quantity));
    }
}

public class OrderItem {
    private Product product;
    private int quantity;
}
```
