---
id: 793b144f-d49f-4f16-aee1-3e1061c0b4e5
title: "Abhängigkeitsinversion"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - solid_prinzipien
  - dependency_injection
  - uml
  - modularisierung
  - draft
source: "Klausur_Referenz"
---

# [[Abhängigkeitsinversion]]

- **Kernkonzept:** Das Prinzip der **Abhängigkeitsinversion** (Dependency Inversion Principle, DIP) ist ein zentrales [[Entwurfsmuster]] in der [[Softwarearchitektur]], das besagt: 
1. **Hochrangige Module** sollten nicht von **tiefrangigen Modulen** abhängen. Beide sollten von [[Schnittstelle|Schnittstellen]] (oder [[Abstraktion|Abstraktionen]]) abhängen.
2. **Abstraktionen** sollten nicht von **Details** abhängen. Details (konkrete Implementierungen) sollten von Abstraktionen abhängen.

DIP zielt darauf ab, die Kopplung zwischen Komponenten zu reduzieren, indem Abhängigkeiten auf abstrakte Schnittstellen umgelenkt werden. Dies fördert die [[Wiederverwendbarkeit]], [[Testbarkeit]] und [[Erweiterbarkeit]] von Systemen.
- **Nutzen & Zweck:** - **Flexibilität**: Durch die Abhängigkeit von Schnittstellen statt konkreten Implementierungen können Module leichter ausgetauscht oder erweitert werden (z. B. für [[Dependency_Injection]] oder [[Mocking]] in Tests).
- **Wartbarkeit**: Änderungen in tiefrangigen Modulen haben keine Auswirkungen auf hochrangige Module, solange die Schnittstellen stabil bleiben.
- **Testbarkeit**: Hochrangige Module lassen sich isoliert testen, indem Mock-Implementierungen der Schnittstellen verwendet werden.
- **Modularität**: Fördert die Trennung von Verantwortlichkeiten ([[Single_Responsibility_Principle]]) und unterstützt [[SOLID_Prinzipien]].

Typische Anwendungsfälle sind:
- [[Plugin-Architekturen]] (z. B. in IDEs oder Frameworks).
- [[Microservices]], bei denen Services über Schnittstellen kommunizieren.
- [[Schichtenarchitektur]] (z. B. Trennung von UI, Business-Logik und Datenzugriff).
- **Abgrenzung & Grenzen:** - **Kein Allheilmittel**: DIP erhöht die Komplexität durch zusätzliche Abstraktionen. Bei einfachen Systemen kann dies übertrieben wirken.
- **Überengineering**: Unnötige Schnittstellen oder zu frühe Abstraktion können die Lesbarkeit beeinträchtigen (vgl. [[YAGNI]]).
- **Stolpersteine**: 
  - **Falsche Abstraktionsebene**: Zu generische Schnittstellen können zu unklaren Verantwortlichkeiten führen.
  - **Zyklische Abhängigkeiten**: Auch bei DIP können zyklische Abhängigkeiten zwischen Schnittstellen entstehen.
  - **Performance-Overhead**: Indirektion über Schnittstellen kann (minimale) Laufzeitkosten verursachen.
- **Nicht gleich Dependency Injection**: DIP ist ein **Prinzip**, während [[Dependency_Injection]] ein **Muster** zur Umsetzung von DIP ist.
- **Beispiel / Code:** {'beschreibung': 'Beispiel in Java: Ein `OrderProcessor` (hochrangiges Modul) hängt nicht direkt von einer konkreten `PaymentMethod` (tiefrangiges Modul) ab, sondern von einer Schnittstelle `IPaymentMethod`.', 'code': {'schnittstelle': '// Abstraktion (Schnittstelle)\npublic interface IPaymentMethod {\n    void processPayment(double amount);\n}', 'konkrete_implementierung': '// Detail (konkrete Implementierung)\npublic class CreditCardPayment implements IPaymentMethod {\n    @Override\n    public void processPayment(double amount) {\n        System.out.println("Zahlung von " + amount + " € per Kreditkarte.");\n    }\n}', 'hochrangiges_modul': '// Hochrangiges Modul (abhängig von der Abstraktion)\npublic class OrderProcessor {\n    private final IPaymentMethod paymentMethod;\n\n    // Dependency Injection via Konstruktor\n    public OrderProcessor(IPaymentMethod paymentMethod) {\n        this.paymentMethod = paymentMethod;\n    }\n\n    public void processOrder(double amount) {\n        paymentMethod.processPayment(amount);\n    }\n}', 'anwendung': '// Anwendung\npublic class Main {\n    public static void main(String[] args) {\n        IPaymentMethod payment = new CreditCardPayment(); // oder PayPalPayment, etc.\n        OrderProcessor processor = new OrderProcessor(payment);\n        processor.processOrder(100.0);\n    }\n}'}, 'uml_diagramm': {'mermaid': 'classDiagram\n    class IPaymentMethod {\n        <<interface>>\n        +processPayment(amount: double)\n    }\n\n    class CreditCardPayment {\n        +processPayment(amount: double)\n    }\n\n    class PayPalPayment {\n        +processPayment(amount: double)\n    }\n\n    class OrderProcessor {\n        -paymentMethod: IPaymentMethod\n        +OrderProcessor(paymentMethod: IPaymentMethod)\n        +processOrder(amount: double)\n    }\n\n    IPaymentMethod <|-- CreditCardPayment\n    IPaymentMethod <|-- PayPalPayment\n    OrderProcessor --> IPaymentMethod'}}
