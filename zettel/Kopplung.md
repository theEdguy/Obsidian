---
id: 2f1d73da-950f-4163-badb-c098c40cd7f6
title: "Kopplung"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - entwurfsmuster
  - uml
  - modularisierung
  - oop_prinzipien
  - draft
source: "Klausur_Referenz"
---

# [[Kopplung]]

- **Kernkonzept:** Kopplung bezeichnet das Ausmaß der Abhängigkeit zwischen [[Modul]]en, [[Komponente]]n oder [[Klasse]]n in einem Softwaresystem. Sie misst, wie stark die internen Details eines Moduls von anderen Modulen bekannt sind oder genutzt werden. Ziel ist eine **lose Kopplung**, bei der Änderungen in einem Modul möglichst geringe Auswirkungen auf andere Module haben. Dies wird erreicht durch klare [[Schnittstelle]]n, [[Information_Hiding]] und die Verwendung von [[Abstraktion]] (z. B. über [[Interface]]s oder [[Fassade_Pattern]]).
- **Nutzen & Zweck:** Lose Kopplung ist ein zentrales Prinzip der [[Softwarearchitektur]] und des [[Entwurfs]], um folgende Vorteile zu erzielen:
- **Wartbarkeit**: Änderungen in einem Modul erfordern weniger Anpassungen in abhängigen Modulen.
- **Wiederverwendbarkeit**: Module können leichter in anderen Kontexten eingesetzt werden, da sie weniger externe Abhängigkeiten haben.
- **Testbarkeit**: Module lassen sich isoliert testen (z. B. durch [[Mock_Objekt]]e).
- **Skalierbarkeit**: Systeme können einfacher erweitert oder umstrukturiert werden.
- **Robustheit**: Fehler in einem Modul propagieren seltener in andere Teile des Systems.

Hohe Kopplung führt dagegen zu "spaghettiartigen" Abhängigkeiten, die das System unflexibel und fehleranfällig machen.
- **Abgrenzung & Grenzen:** - **Kopplung vs. [[Kohäsion]]**: Während Kopplung die Abhängigkeit *zwischen* Modulen beschreibt, bezieht sich Kohäsion auf die *innere Zusammengehörigkeit* der Verantwortlichkeiten eines Moduls. Beide Konzepte sind komplementär: Hohe Kohäsion fördert oft lose Kopplung.
- **Arten der Kopplung**: 
  - **Datenkopplung** (geringste Kopplung): Module kommunizieren nur über einfache Datenstrukturen (z. B. Parameter).
  - **Stempelkopplung**: Module teilen komplexe Datenstrukturen (z. B. Objekte), was Abhängigkeiten erhöht.
  - **Kontrollkopplung**: Ein Modul steuert den Ablauf eines anderen (z. B. über Flags), was die Flexibilität einschränkt.
  - **Inhaltskopplung** (höchste Kopplung): Ein Modul greift direkt auf interne Daten oder Logik eines anderen Moduls zu (z. B. durch `friend`-Klassen in C++).
- **Stolpersteine**: 
  - Übermäßige Abstraktion kann zu unnötiger Komplexität führen (z. B. zu viele [[Interface]]s).
  - Falsche Anwendung von [[Entwurfsmuster]]n wie [[Singleton_Pattern]] kann globale Abhängigkeiten schaffen.
  - [[Fassade_Pattern]] kann Kopplung reduzieren, aber auch eine neue zentrale Abhängigkeit einführen.
- **Grenzen**: In verteilten Systemen (z. B. [[Microservices]]) ist lose Kopplung essenziell, aber Netzwerkkommunikation kann neue Abhängigkeiten schaffen (z. B. Latenz, Protokollabhängigkeiten).
- **Beispiel / Code:** {'beschreibung': 'Beispiel für lose vs. enge Kopplung in Java:', 'code_lose_kopplung': {'beschreibung': 'Lose Kopplung durch Verwendung eines [[Interface]]:', 'java': 'public interface PaymentProcessor {\n    void processPayment(double amount);\n}\n\npublic class CreditCardProcessor implements PaymentProcessor {\n    @Override\n    public void processPayment(double amount) {\n        System.out.println("Processing credit card payment: " + amount);\n    }\n}\n\npublic class Order {\n    private PaymentProcessor paymentProcessor;\n\n    public Order(PaymentProcessor paymentProcessor) {\n        this.paymentProcessor = paymentProcessor;\n    }\n\n    public void checkout(double amount) {\n        paymentProcessor.processPayment(amount);\n    }\n}\n// Verwendung:\nOrder order = new Order(new CreditCardProcessor());\norder.checkout(100.0);'}, 'code_enge_kopplung': {'beschreibung': 'Enge Kopplung durch direkte Abhängigkeit:', 'java': 'public class Order {\n    private CreditCardProcessor paymentProcessor = new CreditCardProcessor();\n\n    public void checkout(double amount) {\n        paymentProcessor.processPayment(amount);\n    }\n}\n\npublic class CreditCardProcessor {\n    public void processPayment(double amount) {\n        System.out.println("Processing credit card payment: " + amount);\n    }\n}'}, 'uml_diagramm': {'beschreibung': 'UML-Klassendiagramm zur Veranschaulichung loser Kopplung:', 'mermaid': 'classDiagram\n    class PaymentProcessor {\n        <<interface>>\n        +processPayment(amount: double)\n    }\n\n    class CreditCardProcessor {\n        +processPayment(amount: double)\n    }\n\n    class Order {\n        -paymentProcessor: PaymentProcessor\n        +Order(paymentProcessor: PaymentProcessor)\n        +checkout(amount: double)\n    }\n\n    PaymentProcessor <|-- CreditCardProcessor\n    Order --> PaymentProcessor'}}
