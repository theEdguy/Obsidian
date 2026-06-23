---
id: 5ee9ed9a-5b5a-4f20-a602-b7fa94d4587d
title: "Dependency_Injection"
date: 2026-06-23
tags:
  - software_engineering
  - entwurfsmuster
  - software_architektur
  - dependency_management
  - design_pattern
  - abhängigkeit
  - draft
source: "software_engineering_kapitel_05"
---

# [[Dependency_Injection]]

- **Kernkonzept:** [[Dependency_Injection]] ist ein [[Entwurfsmuster|Muster]], bei dem die [[Abhängigkeit|Abhängigkeiten]] einer [[Klasse]] von außen injiziert werden, anstatt sie selbst zu erzeugen. Dies fördert die [[Lose_Kopplung|lose Kopplung]] und verbessert die [[Testbarkeit]] sowie [[Wartbarkeit]] von [[Softwarekomponente|Softwarekomponenten]].
- **Nutzen & Zweck:** [[Dependency_Injection]] löst das Problem der engen [[Kopplung]] zwischen [[Klasse|Klassen]], indem es die Verantwortung für das Erstellen und Verwalten von [[Abhängigkeit|Abhängigkeiten]] an eine externe Instanz – wie einen [[Container]] oder ein [[Framework]] – delegiert. Dadurch wird die [[Wiederverwendbarkeit]] von [[Code]] erhöht, die [[Testbarkeit]] durch einfache Austauschbarkeit von [[Abhängigkeit|Abhängigkeiten]] (z. B. [[Mock|Mock-Objekte]]) verbessert und die [[Modularität]] des Systems gestärkt. Zudem ermöglicht es eine klarere [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] und erleichtert die Anpassung an sich ändernde [[Anforderung|Anforderungen]].
- **Abgrenzung & Grenzen:** [[Dependency_Injection]] sollte nicht eingesetzt werden, wenn die [[Abhängigkeit|Abhängigkeiten]] trivial oder unveränderlich sind, da der zusätzliche Aufwand für die Konfiguration und Verwaltung des [[Injection-Mechanismus]] den Nutzen übersteigen kann. Alternativen wie das direkte Instanziieren von [[Abhängigkeit|Abhängigkeiten]] innerhalb einer [[Klasse]] (z. B. über den `new`-Operator) sind in solchen Fällen einfacher und effizienter. Zudem kann [[Dependency_Injection]] die [[Komplexität]] erhöhen, wenn es übermäßig oder unreflektiert eingesetzt wird, insbesondere in kleinen [[Projekt|Projekten]] oder bei stark gekoppelten Systemen, die keine [[Flexibilität]] erfordern. Im Vergleich zum [[Service_Locator]]-Pattern bietet [[Dependency_Injection]] eine explizitere und transparentere Handhabung von [[Abhängigkeit|Abhängigkeiten]], ist jedoch mit höherem Initialaufwand verbunden. Nicht geeignet für einfache [[Anwendung|Anwendungen]], in denen die [[Komplexität]] von [[Dependency_Injection]]-Frameworks überflüssig ist.
- **Beispiel / Code:** ```java
// Beispiel für Dependency Injection mit Annotation-basierter Injection (z. B. Spring Framework)
@Component
@ApplicationScope
class ManagementFacade implements MemberManagement {
    @Autowired
    private StateMachine stateMachine;
    
    // ...
}

// Beispiel für Dependency Injection mit Konstruktor-Injection
public class BestellService {
    private final ZahlungsGateway zahlungsGateway;

    // Abhängigkeit wird von außen injiziert
    public BestellService(ZahlungsGateway zahlungsGateway) {
        this.zahlungsGateway = zahlungsGateway;
    }

    public void bestellungAufgeben(Bestellung bestellung) {
        // Nutzung der injizierten Abhängigkeit
        zahlungsGateway.bezahlen(bestellung.getBetrag());
    }
}

// Nutzung
ZahlungsGateway gateway = new PayPalGateway(); // Konkrete Implementierung
BestellService service = new BestellService(gateway); // Injection
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e1
- **Vorgänger / Parent:** [[Abhängigkeit]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Abhängigkeit]]
  - [[Design_Patterns]]
