---
id: 334b653d-edb9-44e4-8eea-18d9fdb52825
title: "Logikschicht"
date: 2026-05-31
tags:
  - software_engineering
  - schichtenarchitektur
  - softwarearchitektur
  - domain_driven_design
  - mvc_pattern
  - uml
  - entwurfsmuster
  - separation_of_concerns
  - draft
source: "Klausur_Referenz"
---

# [[Logikschicht]]

- **Kernkonzept:** Die **Logikschicht** (auch *Geschäftslogikschicht* oder *Business_Logic_Layer* genannt) ist eine zentrale Komponente in der [[Schichtenarchitektur]] einer Softwareanwendung. Sie kapselt die domänenspezifischen Regeln, Prozesse und Algorithmen, die den funktionalen Kern der Anwendung ausmachen. Ihre Hauptaufgabe besteht darin, Eingaben aus der [[Präsentationsschicht]] zu verarbeiten, Geschäftslogik auszuführen und Ergebnisse an die Präsentations- oder [[Datenzugriffsschicht]] weiterzuleiten. Die Logikschicht agiert dabei unabhängig von der Darstellung (z. B. GUI, CLI, Web) und der Datenhaltung (z. B. Datenbank, Dateisystem).
- **Nutzen & Zweck:** Die Logikschicht dient folgenden Zwecken:
- **Trennung von Verantwortlichkeiten**: Durch die Entkopplung von [[Präsentationsschicht]] und [[Datenzugriffsschicht]] wird die Wartbarkeit und Erweiterbarkeit der Software verbessert. Änderungen an der Benutzeroberfläche oder Datenhaltung erfordern keine Anpassungen der Geschäftslogik.
- **Wiederverwendbarkeit**: Die Geschäftslogik kann in verschiedenen Kontexten (z. B. Desktop-, Web- oder Mobile-Anwendung) genutzt werden, ohne dupliziert zu werden.
- **Testbarkeit**: Da die Logikschicht keine Abhängigkeiten zu UI- oder Datenbank-Frameworks hat, lässt sie sich isoliert mit [[Unit_Tests]] prüfen.
- **Skalierbarkeit**: Die Schicht kann horizontal skaliert werden (z. B. in Microservices-Architekturen), um Last zu verteilen.
- **Sicherheit**: Durch die Kapselung der Geschäftslogik können Validierungen und Autorisierungen zentral implementiert werden (z. B. mittels [[MVC_Pattern]] oder [[Domain_Driven_Design]]).
- **Abgrenzung & Grenzen:** Die Logikschicht grenzt sich wie folgt ab:
- **Von der Präsentationsschicht**: Sie enthält *keine* Darstellungscode (z. B. HTML, Swing, JavaFX) oder Eingabevalidierung, die ausschließlich der UI-Logik dient. Allerdings kann sie *domänenspezifische Validierungen* (z. B. Geschäftsregeln) durchführen.
- **Von der Datenzugriffsschicht**: Sie enthält *keine* SQL-Abfragen, ORM-Konfigurationen (z. B. [[Hibernate]]) oder Dateisystemoperationen. Diese werden in der [[Datenzugriffsschicht]] gekapselt.
- **Stolpersteine**: 
  - *Fat Logic Layer*: Eine überladene Logikschicht kann zu monolithischen Strukturen führen. Abhilfe schafft eine weitere Aufteilung (z. B. in [[Service_Layer]] und [[Domain_Model]]).
  - *Verletzung der Schichtengrenzen*: Direkte Abhängigkeiten zwischen Präsentations- und Datenzugriffsschicht (z. B. durch *Lazy Loading* in ORMs) untergraben die Trennung.
  - *Technologieabhängigkeit*: Die Logikschicht sollte keine Frameworks-spezifischen Annotationen oder APIs verwenden, um Austauschbarkeit zu gewährleisten.
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Klassendiagramm (in Mermaid-Syntax) veranschaulicht eine typische Logikschicht in einer E-Commerce-Anwendung. Die Logikschicht (`OrderService`) nutzt das [[Domain_Model]] (`Order`, `Customer`) und delegiert Persistenz an die [[Datenzugriffsschicht]] (`OrderRepository`). Die Präsentationsschicht (hier nicht dargestellt) würde `OrderService` aufrufen, um Bestellungen zu verarbeiten.', 'uml_diagramm': 'classDiagram\n    class OrderService {\n        +placeOrder(customerId: String, items: List~OrderItem~): Order\n        +cancelOrder(orderId: String): void\n    }\n    \n    class Order {\n        -orderId: String\n        -customer: Customer\n        -items: List~OrderItem~\n        -status: OrderStatus\n        +calculateTotal(): double\n    }\n    \n    class Customer {\n        -customerId: String\n        -name: String\n        -address: String\n    }\n    \n    class OrderItem {\n        -productId: String\n        -quantity: int\n        -price: double\n    }\n    \n    class OrderRepository {\n        +save(order: Order): void\n        +findById(orderId: String): Order\n    }\n    \n    OrderService --> Order : erstellt/verarbeitet\n    OrderService --> OrderRepository : nutzt\n    Order "1" *-- "1..*" OrderItem : enthält\n    Order "1" *-- "1" Customer : gehört zu', 'code_beispiel': {'sprache': 'Java', 'auszug': '// Logikschicht: Geschäftslogik für Bestellungen\npublic class OrderService {\n    private final OrderRepository orderRepository;\n    \n    public OrderService(OrderRepository orderRepository) {\n        this.orderRepository = orderRepository;\n    }\n    \n    public Order placeOrder(String customerId, List<OrderItem> items) {\n        // Domänenspezifische Validierung\n        if (items.isEmpty()) {\n            throw new IllegalArgumentException("Bestellung muss mindestens ein Item enthalten");\n        }\n        \n        // Geschäftslogik: Bestellung erstellen\n        Customer customer = new Customer(customerId);\n        Order order = new Order(customer, items);\n        \n        // Delegation an Datenzugriffsschicht\n        orderRepository.save(order);\n        return order;\n    }\n}\n\n// Domain-Modell (Teil der Logikschicht)\npublic class Order {\n    private String orderId;\n    private Customer customer;\n    private List<OrderItem> items;\n    private OrderStatus status;\n    \n    public double calculateTotal() {\n        return items.stream().mapToDouble(OrderItem::getPrice).sum();\n    }\n    // ...\n}'}}
