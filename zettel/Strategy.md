---
id: 8192048e-46aa-49b1-bf68-897bea9e74c8
title: "Strategy"
date: 2026-06-23
tags:
  - software_engineering
  - strategy
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Strategy]]

- **Kernkonzept:** Das Strategy-Design-Pattern definiert eine Familie von austauschbaren Algorithmen, kapselt sie einzeln und macht sie untereinander ersetzbar. Dadurch kann der Algorithmus unabhängig vom Client, der ihn nutzt, variiert werden.
- **Nutzen & Zweck:** Das Strategy-Pattern löst das Problem, wenn eine Klasse mehrere Varianten eines Algorithmus oder Verhaltens implementieren muss und diese zur Laufzeit ausgetauscht werden sollen. Es fördert die Flexibilität und Wartbarkeit, indem es die Algorithmen von der Klasse trennt, die sie verwendet, und vermeidet dadurch bedingte Anweisungen (z. B. if-else oder switch-case). Dies ermöglicht eine einfache Erweiterung um neue Strategien, ohne bestehende Klassen zu modifizieren.
- **Abgrenzung & Grenzen:** Das Strategy-Pattern sollte nicht genutzt werden, wenn nur ein einziger Algorithmus benötigt wird oder wenn die Algorithmen sehr einfach sind und sich kaum ändern. Es kann Overhead verursachen, wenn zu viele kleine Strategie-Klassen erstellt werden müssen. Alternativen wie das Template-Method-Pattern sind besser geeignet, wenn die Algorithmen eine feste Struktur haben und nur bestimmte Schritte variieren. Im Gegensatz zur Vererbung ermöglicht Strategy eine dynamischere Auswahl von Algorithmen zur Laufzeit.
- **Beispiel / Code:** ```java
// Strategy-Interface
interface PaymentStrategy {
    void pay(int amount);
}

// Konkrete Strategien
class CreditCardPayment implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println(amount + "€ per Kreditkarte bezahlt.");
    }
}

class PayPalPayment implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println(amount + "€ per PayPal bezahlt.");
    }
}

// Context-Klasse, die die Strategie nutzt
class ShoppingCart {
    private PaymentStrategy paymentStrategy;

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void checkout(int amount) {
        paymentStrategy.pay(amount);
    }
}

// Nutzung
public class Main {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart();
        cart.setPaymentStrategy(new CreditCardPayment());
        cart.checkout(100);
        
        cart.setPaymentStrategy(new PayPalPayment());
        cart.checkout(50);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7c2
- **Vorgänger / Parent:** [[Verhaltensmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Verhaltensmuster]]
  - [[Design_Pattern]]
