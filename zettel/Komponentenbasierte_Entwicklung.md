---
id: bceaec47-3a86-4d92-89c2-8038d81bb650
title: "Komponentenbasierte_Entwicklung"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - modularisierung
  - entwurfsmuster
  - komponenten_design
  - fassade_pattern
  - uml
  - kopplung_kohaesion
  - lifecycle_management
  - draft
source: "Klausur_Referenz"
---

# [[Komponentenbasierte_Entwicklung]]

- **Kernkonzept:** Die **komponentenbasierte Entwicklung** ist ein [[Softwareentwicklungsparadigma]], das die Strukturierung von Software in wiederverwendbare, abgeschlossene und austauschbare [[Komponente|Komponenten]] fokussiert. Eine Komponente ist eine eigenständige Einheit mit klar definierten [[Schnittstelle|Schnittstellen]] und einer Kapselung ihrer Implementierungsdetails. Sie kann unabhängig entwickelt, getestet und in verschiedene Systeme integriert werden. Die Kommunikation zwischen Komponenten erfolgt ausschließlich über ihre Schnittstellen, wodurch die [[Kopplung]] minimiert und die [[Kohäsion]] maximiert wird. Ein zentrales Entwurfsziel ist die Reduktion der Komplexität durch die Kanalisierung von Zugriffen, z. B. mittels [[Fassade_Pattern]] (Facade Pattern).
- **Nutzen & Zweck:** Die komponentenbasierte Entwicklung dient der **Modularisierung** und **Wiederverwendbarkeit** von Softwarebausteinen. Sie ermöglicht:
- **Reduzierte Komplexität**: Durch die Unterteilung in Subsysteme und Komponenten wird die Gesamtkomplexität beherrschbar.
- **Erhöhte Wartbarkeit**: Änderungen an einer Komponente haben minimale Auswirkungen auf andere Systemteile.
- **Parallele Entwicklung**: Teams können unabhängig an verschiedenen Komponenten arbeiten.
- **Flexible Systemarchitektur**: Komponenten können ausgetauscht oder aktualisiert werden, ohne das Gesamtsystem zu beeinträchtigen (z. B. durch [[Plugin_Architektur]]).
- **Skalierbarkeit**: Komponenten können je nach Bedarf instanziiert oder zerstört werden (z. B. [[Singleton]], Session-basierte oder Anfrage-spezifische Lebenszyklen).

Typische Anwendungsfälle sind [[Enterprise_Software]], [[Microservices]] oder [[UI_Frameworks]] (z. B. React-Komponenten).
- **Abgrenzung & Grenzen:** Die komponentenbasierte Entwicklung grenzt sich ab von:
- **Objektorientierter Programmierung (OOP)**: Während OOP auf Klassen und Vererbung basiert, liegt der Fokus hier auf der Komposition von Komponenten mit klaren Schnittstellen. Komponenten sind oft gröber granuliert als Objekte.
- **Monolithischen Architekturen**: Im Gegensatz zu monolithischen Systemen, bei denen alle Funktionen eng verknüpft sind, fördert die komponentenbasierte Entwicklung lose Kopplung.
- **Serviceorientierten Architekturen (SOA)**: SOA arbeitet mit verteilten Diensten, während Komponenten lokal oder remote eingesetzt werden können, aber nicht zwingend netzwerkbasiert sind.

**Stolpersteine und Grenzen**:
- **Übermäßige Fragmentierung**: Zu viele kleine Komponenten können die Systemkomplexität erhöhen.
- **Schnittstellenmanagement**: Schlechte Schnittstellendesigns führen zu hoher Kopplung oder unklaren Verantwortlichkeiten.
- **Lifecycle-Konflikte**: Unterschiedliche Lebenszyklen von Komponenten (z. B. Singleton vs. Session-basiert) können zu Inkonsistenzen führen.
- **Performance-Overhead**: Kommunikation zwischen Komponenten (z. B. über [[Remote_Procedure_Call]]) kann langsamer sein als direkte Methodenaufrufe.
- **Versionierung**: Komponentenabhängigkeiten müssen sorgfältig verwaltet werden, um Konflikte zu vermeiden (vgl. [[Dependency_Management]]).
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer komponentenbasierten Architektur mit Fassade in Java. Das System besteht aus zwei Komponenten (`UserManagement` und `OrderProcessing`), die über eine Fassade (`ShopFacade`) gekapselt werden. Die Komponenten sind unterschiedlichen Schichten zugeordnet (z. B. `UserManagement` in der Business-Logik-Schicht, `OrderProcessing` in der Datenzugriffsschicht).', 'uml_diagramm': {'mermaid': 'classDiagram\n    class ShopFacade {\n        +createUser(String name, String email)\n        +placeOrder(String userId, String productId)\n    }\n    \n    class UserManagement {\n        +User createUser(String name, String email)\n        +User getUser(String userId)\n    }\n    \n    class OrderProcessing {\n        +Order placeOrder(String userId, String productId)\n        +Order getOrder(String orderId)\n    }\n    \n    ShopFacade --> UserManagement : nutzt\n    ShopFacade --> OrderProcessing : nutzt\n    \n    note for ShopFacade "Fassade kapselt die Schnittstellen\nder Komponenten und reduziert\nKomplexität für den Client."\n    note for UserManagement "Komponente mit Singleton-Lifecycle:\nexistiert über die ganze Anwendung."\n    note for OrderProcessing "Komponente mit Session-Lifecycle:\nwird pro Nutzer-Session instanziiert."'}, 'java_code': {'fassade': '// Fassade zur Kapselung der Komponenten\npublic class ShopFacade {\n    private UserManagement userManagement;\n    private OrderProcessing orderProcessing;\n    \n    public ShopFacade() {\n        this.userManagement = UserManagement.getInstance(); // Singleton\n        this.orderProcessing = new OrderProcessing(); // Session-basiert\n    }\n    \n    public String createUser(String name, String email) {\n        User user = userManagement.createUser(name, email);\n        return user.getId();\n    }\n    \n    public String placeOrder(String userId, String productId) {\n        User user = userManagement.getUser(userId);\n        if (user != null) {\n            Order order = orderProcessing.placeOrder(userId, productId);\n            return order.getId();\n        }\n        throw new IllegalArgumentException("User not found");\n    }\n}', 'komponente_user_management': '// Komponente mit Singleton-Lifecycle\npublic class UserManagement {\n    private static UserManagement instance;\n    private Map<String, User> users = new HashMap<>();\n    \n    private UserManagement() {}\n    \n    public static synchronized UserManagement getInstance() {\n        if (instance == null) {\n            instance = new UserManagement();\n        }\n        return instance;\n    }\n    \n    public User createUser(String name, String email) {\n        User user = new User(name, email);\n        users.put(user.getId(), user);\n        return user;\n    }\n    \n    public User getUser(String userId) {\n        return users.get(userId);\n    }\n}', 'komponente_order_processing': '// Komponente mit Session-Lifecycle\npublic class OrderProcessing {\n    private Map<String, Order> orders = new HashMap<>();\n    \n    public Order placeOrder(String userId, String productId) {\n        Order order = new Order(userId, productId);\n        orders.put(order.getId(), order);\n        return order;\n    }\n    \n    public Order getOrder(String orderId) {\n        return orders.get(orderId);\n    }\n}'}}
