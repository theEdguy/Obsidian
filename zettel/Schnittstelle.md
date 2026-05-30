---
id: 9291b368-60fa-4244-b162-19861dd49773
title: "Schnittstelle"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - entwurf
  - vertragsbasierte_programmierung
  - architektur
  - design
  - designprinzip
  - software_architektur
  - draft
source: "SWE Slides (Folien 376-388)"
---

# [[Schnittstelle]]

- **Kernkonzept:** Eine [[Schnittstelle]] definiert die externe [[Sichtbarkeit]] von [[Operation|Operationen]] einer [[Komponente]] oder eines [[System|Systems]], indem sie einen [[Vertrag]] zwischen [[Komponente|Komponenten]] festlegt. Sie spezifiziert das *Was* der [[Interaktion]] – einschließlich verfügbarer [[Operation|Operationen]], [[Signatur|Signaturen]], [[Datenformat|Datenformate]] und [[Protokoll|Protokolle]] – ohne die interne [[Struktur]] oder [[Implementierung]] vorzuschreiben und ermöglicht so [[Polymorphie]] und [[Lose_Kopplung|lose Kopplung]].
- **Nutzen & Zweck:** [[Schnittstelle|Schnittstellen]] lösen das [[Problem]] der [[Abhängigkeit]] zwischen [[Komponente|Komponenten]], indem sie eine klare [[Definition]] der [[Interaktion]] bereitstellen und [[Lose_Kopplung|lose Kopplung]] fördern. Sie sind essenziell für [[Entwurfsmuster]] wie das [[Strategy_Pattern]], [[Observer_Pattern]] oder [[Factory_Method_Pattern]] und bilden die Grundlage für [[vertragsbasierte_Programmierung]]. Durch die Trennung von [[Schnittstelle]] und [[Implementierung]] wird die [[Wiederverwendbarkeit]], [[Erweiterbarkeit]], [[Modularität]] und [[Kohäsion]] innerhalb von [[Modul|Modulen]] gestärkt. Zudem vereinfachen sie die [[Integration]] heterogener [[System|Systeme]] und ermöglichen die unabhängige Weiterentwicklung von [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** [[Schnittstelle|Schnittstellen]] sind kein Ersatz für konkrete [[Implementierung|Implementierungen]] oder [[Datenmodellierung]] und beschreiben ausschließlich das *Was* der [[Interaktion]], nicht das *Wie* der Umsetzung. Im Gegensatz zu [[abstrakte_Klasse|abstrakten Klassen]] können sie keine [[Attribut|Attribute]] oder konkrete [[Methode|Methoden]] enthalten. Sie sind ungeeignet, wenn die [[Komplexität]] der [[Schnittstelle]] den Nutzen übersteigt oder eine direkte [[Implementierung]] ohne [[Abstraktion]] effizienter ist. Während [[API]]s oft technisch spezifiziert sind (z. B. durch [[Protokoll|Protokolle]] wie HTTP), bleiben [[Schnittstelle|Schnittstellen]] abstrakter und können auch auf konzeptioneller Ebene definiert werden. Nicht nutzen, wenn eine teilweise [[Implementierung]] oder gemeinsame [[Attribut|Attribute]] benötigt werden.
- **Beispiel / Code:** ```java
// Beispiel einer Schnittstelle in Java mit zwei Implementierungen und Anwendung des Observer-Patterns
public interface Team {
    int leistungsprognose(Date datum);
    // Weitere Operationen können hinzugefügt werden, ohne bestehende Implementierungen zu brechen
}

public class DDDTeam implements Team {
    @Override
    public int leistungsprognose(Date datum) {
        return 42; // Einfache Implementierung
    }
}

public interface ZahlungsService {
    Zahlung verarbeiteZahlung(Bestellung bestellung);
    boolean storniereZahlung(Zahlung zahlung);
}

public class KreditkartenService implements ZahlungsService {
    @Override
    public Zahlung verarbeiteZahlung(Bestellung bestellung) {
        // Konkrete Implementierung für Kreditkartenzahlungen
        return new Zahlung(bestellung.getBetrag(), "KREDITKARTE");
    }
    
    @Override
    public boolean storniereZahlung(Zahlung zahlung) {
        // Logik zum Stornieren
        return true;
    }
}

// Beispiel für das Observer-Pattern mit Schnittstellen
public interface Subject {
    void attach(Observer obs);
    void detach(Observer obs);
    void notifyObservers();
}

public interface Observer {
    void update(String message);
}

public class ConcreteSubject implements Subject {
    private List<Observer> observers = new ArrayList<>();
    
    @Override
    public void attach(Observer obs) {
        observers.add(obs);
    }
    
    @Override
    public void detach(Observer obs) {
        observers.remove(obs);
    }
    
    @Override
    public void notifyObservers() {
        for (Observer obs : observers) {
            obs.update("State changed");
        }
    }
}
```
