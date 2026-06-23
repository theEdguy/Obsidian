---
id: bb81a598-c67b-4162-b17b-c459dd4d29d7
title: "Design-Prinzipien"
date: 2026-06-23
tags:
  - software_engineering
  - design
  - prinzipien
  - draft
source: "software_engineering_kapitel_14"
---

# [[Design-Prinzipien]]

- **Kernkonzept:** Design-Prinzipien sind grundlegende Leitlinien und bewährte Praktiken im Software-Engineering, die die Struktur, Lesbarkeit, Wartbarkeit und Erweiterbarkeit von Software-Systemen verbessern. Sie dienen als Rahmenwerk für die Entwicklung qualitativ hochwertiger, objektorientierter Designs und fördern die Wiederverwendung von Lösungen.
- **Nutzen & Zweck:** Design-Prinzipien existieren, um Entwicklern eine klare Orientierung bei der Gestaltung von Software zu geben. Sie lösen konkrete Probleme wie starre, schwer wartbare Code-Strukturen, hohe Kopplung zwischen Komponenten oder mangelnde Flexibilität bei Änderungen. Durch die Anwendung dieser Prinzipien wird die Software robuster, anpassungsfähiger und leichter verständlich, was die Entwicklungszeit verkürzt und die Fehleranfälligkeit reduziert. Zudem ermöglichen sie eine effizientere Kommunikation im Team durch ein gemeinsames Vokabular und standardisierte Lösungsansätze.
- **Abgrenzung & Grenzen:** Design-Prinzipien sollten nicht dogmatisch angewendet werden, da sie in bestimmten Kontexten kontraproduktiv sein können. Beispielsweise kann eine übermäßige Abstraktion die Komplexität unnötig erhöhen oder die Performance beeinträchtigen. Sie unterscheiden sich von konkreten Design-Patterns, da sie keine fertigen Lösungen vorgeben, sondern allgemeine Richtlinien darstellen. Alternativen wie prozedurale Programmierung oder funktionale Ansätze können in einfachen oder performancekritischen Szenarien sinnvoller sein, wenn die Vorteile der Objektorientierung nicht benötigt werden.
- **Beispiel / Code:** ```java
// Beispiel für das Prinzip 'Programmiere auf eine Schnittstelle, nicht auf eine Implementierung'
public interface PaymentMethod {
    void processPayment(double amount);
}

public class CreditCardPayment implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Zahlung von " + amount + " via Kreditkarte verarbeitet.");
    }
}

public class PayPalPayment implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Zahlung von " + amount + " via PayPal verarbeitet.");
    }
}

// Nutzung der Schnittstelle, ohne konkrete Implementierung zu kennen
public class ShoppingCart {
    private PaymentMethod paymentMethod;

    public ShoppingCart(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod;
    }

    public void checkout(double amount) {
        paymentMethod.processPayment(amount);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d
- **Vorgänger / Parent:** [[Software_Engineering]]
- **Folgezettel / Unterzettel:**
  - [[OpenClosed_Principle]]
  - [[Dependency_Inversion_Principle]]
  - [[Single_Responsibility_Principle]]
- **Querverweise:**
  - [[Entwurfsmuster]]
  - [[SOLID-Prinzipien]]
