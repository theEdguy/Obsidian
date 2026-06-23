---
id: 09d4ffcc-727d-4abf-a718-d830e56eb8d9
title: "Design_Patterns"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - entwurfsmuster
  - design
  - muster
  - wiederverwendung
  - architektur
  - draft
source: "software_engineering_kapitel_11"
---

# [[Design_Patterns]]

- **Kernkonzept:** [[Design_Patterns|Entwurfsmuster]] sind bewährte [[Lösungsmuster]] für wiederkehrende [[Entwurfsproblem|Probleme]] im [[objektorientierten_Design|objektorientierten Software-Design]]. Sie bieten standardisierte Vorlagen zur Gestaltung von [[Klasse|Klassen]], [[Schnittstelle|Schnittstellen]] und deren [[Interaktion|Interaktionen]], um [[Flexibilität]], [[Wartbarkeit]], [[Skalierbarkeit]] und [[Erweiterbarkeit]] zu verbessern. Durch die Bereitstellung erprobter Strukturen reduzieren sie [[Komplexität]] und beschleunigen die Entwicklung, indem sie [[Wiederverwendung]] von [[Entwurf|Entwürfen]] und [[Best_Practice|Best Practices]] fördern.
- **Nutzen & Zweck:** [[Design_Patterns]] lösen das Problem der [[Wiederverwendung]] von [[Entwurf|Entwürfen]] und verbessern die [[Wartbarkeit]] und [[Verständlichkeit]] von [[Software-System|Software-Systemen]]. Sie ermöglichen die gezielte Umsetzung von Anforderungen wie [[Flexibilität]], [[Austauschbarkeit]] oder [[Wiederverwendbarkeit]] und fördern die [[Kommunikation]] zwischen [[Entwickler|Entwicklern]] durch eine gemeinsame [[Terminologie]]. Darüber hinaus reduzieren sie [[Redundanz|Redundanzen]] und unterstützen grundlegende [[Prinzipien]] wie [[Lose_Kopplung|lose Kopplung]], [[Hohe_Kohäsion|hohe Kohäsion]] und [[Trennung_von_Zuständigkeiten]]. 

Durch die Nutzung etablierter [[Best_Practice|Best Practices]] minimieren sie Fehler, beschleunigen die Entwicklung und erhöhen die Qualität der Software. Ein zentraler Nutzen liegt in der Reduktion der [[Komplexität]] von [[Software-Entwicklungsprozess|Software-Entwicklungsprozessen]], indem sie standardisierte [[Lösungsstrategie|Lösungsstrategien]] für wiederkehrende [[Entwurfsproblem|Probleme]] bereitstellen. Dies verbessert die [[Anpassungsfähigkeit]] an neue Anforderungen und erleichtert die [[Wiederverwendung]] von Konzepten. 

[[Design_Patterns]] etablieren bewährte [[Best_Practice|Praktiken]], die die Anpassung und Erweiterung von Systemen erleichtern, ohne bestehende Strukturen grundlegend zu verändern. Sie fördern zudem die [[Wiederverwendung]] von Code und verbessern die [[Kommunikation]] im Team durch eine gemeinsame Sprache. Zusätzlich beherrschbar machen sie die [[Komplexität]] von [[Software-System|Software-Systemen]] und unterstützen die [[Anpassungsfähigkeit]] an sich ändernde Anforderungen.
- **Abgrenzung & Grenzen:** [[Design_Patterns]] sind nicht für triviale [[Problem|Probleme]] oder stark spezialisierte Anwendungsfälle sinnvoll, bei denen der [[Aufwand]] den Nutzen übersteigt. Übermäßiger Einsatz kann zu unnötiger [[Komplexität]] oder [[Over-Engineering]] führen. Sie sind keine fertigen [[Code-Bibliothek|Code-Bibliotheken]], sondern müssen an den jeweiligen [[Kontext]] angepasst werden. Alternativen wie [[Framework|Frameworks]], [[domänenspezifische_Sprache|domänenspezifische Sprachen]] oder einfache prozedurale Ansätze können in manchen Fällen effizienter sein. 

Zudem ersetzen [[Entwurfsmuster]] kein fundiertes [[Design-Denken]] oder eine durchdachte [[Softwarearchitektur]]. In [[Performance-kritisches_System|Performance-kritischen Systemen]] können einige [[Pattern|Muster]] durch ihren [[Abstraktionsaufwand]] Nachteile bringen. Sie erfordern Erfahrung und Urteilsvermögen, um sinnvoll eingesetzt zu werden, und sollten nicht blind angewendet werden, da sie keine universellen Lösungen darstellen. 

Im Gegensatz zu [[Algorithmus|Algorithmen]] oder [[Datenstruktur|Datenstrukturen]] konzentrieren sie sich auf die [[Interaktion]] zwischen [[Objekt|Objekten]], nicht auf die Implementierung einzelner Funktionen oder die Organisation von Daten. [[Design_Patterns]] sind zudem nicht für nicht-objektorientierte Paradigmen geeignet und können in [[Performance-kritisches_System|Performance-kritischen Systemen]] unnötigen Overhead erzeugen. Sie sollten nur dann eingesetzt werden, wenn der Nutzen die zusätzlichen [[Abstraktionskosten]] rechtfertigt. Ein unreflektierter Einsatz kann die [[Komplexität]] erhöhen, insbesondere wenn das zugrundeliegende [[Problem]] zu einfach ist oder keine [[Wiederverwendung]] erfordert.
- **Beispiel / Code:** ```java
// Beispiel für das [[Factory_Pattern]] (Erzeugungsmuster)
public interface MemberFactory {
    Member createMember(String type);
}

public class StandardMemberFactory implements MemberFactory {
    @Override
    public Member createMember(String type) {
        return new StandardMember();
    }
}

// Beispiel für das [[Observer_Pattern]] (Verhaltensmuster) zur Benachrichtigung bei Zustandsänderungen
interface Observer {
    void update(String message);
}

class NewsAgency {
    private List<Observer> observers = new ArrayList<>();
    private String news;

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void setNews(String news) {
        this.news = news;
        for (Observer observer : observers) {
            observer.update(news);
        }
    }
}

class NewsChannel implements Observer {
    @Override
    public void update(String message) {
        System.out.println("Breaking News: " + message);
    }
}

class Mitglied implements Observer {
    private String name;

    public Mitglied(String name) {
        this.name = name;
    }

    @Override
    public void update(String message) {
        System.out.println(name + " erhielt Benachrichtigung: " + message);
    }
}

class Abteilung {
    private List<Observer> mitglieder = new ArrayList<>();

    public void addObserver(Observer observer) {
        mitglieder.add(observer);
    }

    public void notifyObservers(String message) {
        for (Observer observer : mitglieder) {
            observer.update(message);
        }
    }
}

// Beispiel für das [[Singleton_Pattern]] (Erzeugt genau eine Instanz einer Klasse)
public class DatabaseConnection {
    private static DatabaseConnection instance;

    private DatabaseConnection() {
        // Privater Konstruktor verhindert Instanziierung von außen
    }

    public static synchronized DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }

    public void connect() {
        System.out.println("Verbindung zur Datenbank hergestellt.");
    }
}

// Beispiel: [[Observer_Pattern]] (alternative Implementierung)
interface Observer {
    void update(String message);
}

class Subject {
    private List<Observer> observers = new ArrayList<>();
    
    public void addObserver(Observer observer) {
        observers.add(observer);
    }
    
    public void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }
}

class ConcreteObserver implements Observer {
    @Override
    public void update(String message) {
        System.out.println("Empfangen: " + message);
    }
}

// Verwendung:
public class ObserverDemo {
    public static void main(String[] args) {
        NewsAgency agency = new NewsAgency();
        NewsChannel channel = new NewsChannel();
        agency.addObserver(channel);
        agency.setNews("Neue Software-Version veröffentlicht!");
        
        Abteilung abteilung = new Abteilung();
        Mitglied mitglied = new Mitglied("Max Mustermann");
        abteilung.addObserver(mitglied);
        abteilung.notifyObservers("Abteilungsmeeting am Montag");
        
        DatabaseConnection db = DatabaseConnection.getInstance();
        db.connect();
        
        Subject subject = new Subject();
        subject.addObserver(new ConcreteObserver());
        subject.notifyObservers("Daten wurden aktualisiert!");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Observer-Pattern]]
  - [[Command-Pattern]]
  - [[Factory_Method]]
  - [[Singleton]]
- **Querverweise:**
  - [[Software-Architektur]]
  - [[GoF-Patterns]]
