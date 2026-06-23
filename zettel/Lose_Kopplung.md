---
id: 9f5d1d1f-b234-4fed-abc7-971dbc363f37
title: "Lose_Kopplung"
date: 2026-06-23
tags:
  - software_engineering
  - design_principle
  - architektur
  - software_architektur
  - prinzipien
  - design
  - modularisierung
  - oop
  - draft
source: "software_engineering_kapitel_13"
---

# [[Lose_Kopplung]]

- **Kernkonzept:** [[Lose_Kopplung]] ist ein zentrales [[Designprinzip]] der [[Softwareentwicklung]], das darauf abzielt, die [[Abhängigkeit|Abhängigkeiten]] zwischen [[Komponente|Komponenten]], [[Modul|Modulen]] oder [[Klasse|Klassen]] eines [[Systems]] zu minimieren. Dies wird durch [[Schnittstelle|Schnittstellen]], [[Abstraktion|Abstraktionen]], [[Dependency_Injection]], [[Event-gesteuerte_Systeme|Event-gesteuerte Systeme]], [[Abhängigkeitsinversion]] oder [[Entwurfsmuster|Entwurfsmuster]] wie [[Observer_Pattern]], [[Abstrakte_Fabrik_(Abstract_Factory)|Abstrakte Fabrik]] und [[Brücke_(Bridge)|Brücke]] erreicht, um [[Änderung|Änderungen]] zu erleichtern und [[Starre_Abhängigkeit|starre Abhängigkeiten]] zu vermeiden.
- **Nutzen & Zweck:** [[Lose_Kopplung]] löst das [[Problem]] der [[Starre_Abhängigkeit|starren Abhängigkeiten]] und fördert die [[Wiederverwendbarkeit]], [[Erweiterbarkeit]], [[Wartbarkeit]] und [[Testbarkeit]] von [[Komponente|Komponenten]] und [[Modul|Modulen]]. Durch die Isolation von [[Abhängigkeit|Abhängigkeiten]] werden [[Ripple_Effekt|Ripple-Effekte]] von [[Änderung|Änderungen]] reduziert, was die unabhängige Entwicklung, Prüfung und [[Wiederverwendung]] ermöglicht. Zudem erlaubt sie die einfache Austauschbarkeit von [[Implementierung|Implementierungen]], ohne dass andere Teile des [[Systems]] angepasst werden müssen. Dies erhöht die [[Flexibilität]] des [[Systems]] und ist besonders wertvoll in [[Komponentenbasierte_Architektur|komponentenbasierten Architekturen]], wo [[Modul|Module]] flexibel kombiniert oder ersetzt werden sollen. [[Lose_Kopplung]] erleichtert auch die [[Parallelentwicklung]] in Teams, da [[Komponente|Komponenten]] mit klar definierten [[Schnittstelle|Schnittstellen]] unabhängig voneinander entwickelt werden können. Darüber hinaus unterstützt sie die Umsetzung des [[Dependency_Inversion_Principle|Dependency Inversion Principle]], das die Abhängigkeit von [[Abstraktion|Abstraktionen]] statt von konkreten [[Implementierung|Implementierungen]] fordert. Durch die Reduktion von [[Wartungsproblem|Wartungsproblemen]] und [[Fehleranfälligkeit]] trägt sie maßgeblich zur [[Robustheit]] und [[Skalierbarkeit]] eines [[Systems]] bei. Sie verbessert zudem die [[Modularität]] und ermöglicht eine bessere Trennung von Verantwortlichkeiten, was die [[Kohäsion]] innerhalb einzelner [[Komponente|Komponenten]] stärkt.
- **Abgrenzung & Grenzen:** [[Lose_Kopplung]] kann zu [[Überengineering]] führen, wenn zu viele [[Abstraktion|Abstraktionen]] oder [[Schnittstelle|Schnittstellen]] eingeführt werden, deren [[Komplexität]] den Nutzen übersteigt. Sie ist nicht sinnvoll bei trivialen oder eng verknüpften [[Funktionalität|Funktionalitäten]], bei denen der Aufwand für die Entkopplung den Mehrwert nicht rechtfertigt. Im Gegensatz dazu steht [[Enge_Kopplung]], bei der [[Komponente|Komponenten]] stark voneinander abhängig sind und [[Änderung|Änderungen]] schwerer umsetzbar sind. Zudem ist [[Lose_Kopplung]] nicht immer anwendbar, wenn [[Komponente|Komponenten]] oder [[Modul|Module]] stark miteinander interagieren müssen, z. B. in [[Echtzeitsysteme|Echtzeitsystemen]] mit strengen [[Performance]]- oder [[Konsistenz]]-Anforderungen. In solchen Fällen kann [[Enge_Kopplung]] effizienter sein, da [[Abstraktionsschicht|Abstraktionsschichten]] zusätzlichen [[Overhead]] verursachen. In [[Monolith|Monolithen]] kann der Einsatz von [[Lose_Kopplung]] übertrieben wirken, insbesondere wenn die [[Komplexität]] der [[Indirektion]] oder des [[Boilerplate-Code|Boilerplate-Codes]] den Nutzen nicht aufwiegt. Bei Priorisierung von [[Einfachheit]] oder [[Performance]] kann [[Enge_Kopplung]] in bestimmten Fällen vorzuziehen sein. Nicht alle [[Systeme]] erfordern [[Lose_Kopplung]], insbesondere wenn die [[Komponente|Komponenten]] eng zusammenarbeiten müssen oder [[Performance]]-kritische Anforderungen bestehen. Der initiale Aufwand für die Definition von [[Schnittstelle|Schnittstellen]] und Kommunikationsmechanismen kann höher sein als bei [[Enge_Kopplung]], was bei kleinen oder einfachen [[Systemen]] den Nutzen übersteigen kann.
- **Beispiel / Code:** ```java
// Lose Kopplung durch [[Schnittstelle|Schnittstellen]] und [[Dependency_Injection]]
public interface PaymentProcessor {
    void processPayment(double amount);
}

public class CreditCardProcessor implements PaymentProcessor {
    public void processPayment(double amount) {
        System.out.println("Processing credit card payment: " + amount);
    }
}

public class PayPalProcessor implements PaymentProcessor {
    public void processPayment(double amount) {
        System.out.println("Processing PayPal payment: " + amount);
    }
}

// Verwendung mit [[Dependency_Injection]]
public class PaymentService {
    private final PaymentProcessor paymentProcessor;
    
    public PaymentService(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor;
    }
    
    public void executePayment(double amount) {
        paymentProcessor.processPayment(amount);
    }
}

// Beispiel für [[Event-gesteuertes_System|Event-gesteuerte Systeme]] mit [[Observer_Pattern]]
public class EventPublisher {
    private List<Observer> listeners = new ArrayList<>();
    
    public void addListener(Observer listener) {
        listeners.add(listener);
    }
    
    public void publishEvent(String event) {
        for (Observer listener : listeners) {
            listener.update(event);
        }
    }
}

public interface Observer {
    void update(String state);
}

// Beispiel für lose Kopplung durch [[Schnittstelle|Schnittstellen]] in einer [[Komponentenbasierte_Architektur|komponentenbasierten Architektur]]
public interface MemberRepository {
    void save(Member member);
    Member findById(MemberId id);
}

public class MemberService {
    private final MemberRepository repository;
    
    public MemberService(MemberRepository repository) {
        this.repository = repository;
    }
    
    public void registerMember(Member member) {
        repository.save(member);
    }
}

// Beispiel für lose Kopplung durch [[Fassade_(Entwurfsmuster)|Fassade]] und [[Dependency_Injection]]
interface MemberManagement {
    void manageMembers(Token token);
}

class ManagementFacade implements MemberManagement {
    private MemberManagement manager;
    
    public ManagementFacade(MemberManagement manager) {
        this.manager = manager; // [[Abhängigkeit]] wird injiziert
    }
    
    public void manageMembers(Token token) {
        manager.manageMembers(token);
    }
}

// Beispiel für lose Kopplung durch [[Abstrakte_Fabrik_(Abstract_Factory)|Abstrakte Fabrik]]
public interface LabelFactory {
    AddressLabel createLabel();
}

public class FrenchLabelFactory implements LabelFactory {
    public AddressLabel createLabel() {
        return new FrenchAL();
    }
}

public interface AddressLabel {
    String format();
}

public class FrenchAL implements AddressLabel {
    public String format() { return "French Address"; }
}

// Beispiel für lose Kopplung durch Dependency Injection (aus neuem Konzept)
public interface MitgliedRepository {
    Mitglied findById(String id);
    void save(Mitglied mitglied);
}

// Konkrete Implementierung, die leicht austauschbar ist
public class MitgliedRepositoryImpl implements MitgliedRepository {
    @Override
    public Mitglied findById(String id) {
        // Implementierung
        return null;
    }
    
    @Override
    public void save(Mitglied mitglied) {
        // Implementierung
    }
}

// Klasse, die das Repository nutzt, ohne direkte Abhängigkeit zur Implementierung
public class MitgliedService {
    private final MitgliedRepository mitgliedRepository;
    
    public MitgliedService(MitgliedRepository mitgliedRepository) {
        this.mitgliedRepository = mitgliedRepository;
    }
    
    public Mitglied getMitglied(String id) {
        return mitgliedRepository.findById(id);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a3
- **Vorgänger / Parent:** [[Objektorientierte_Analyse_und_Design]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
