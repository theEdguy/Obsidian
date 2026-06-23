---
id: 7e154da1-7ec7-4ffe-b37a-6315b4b87659
title: "Singleton"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - oop
  - software_architecture
  - singleton
  - erzeugung
  - draft
source: "software_engineering_kapitel_14"
---

# [[Singleton]]

- **Kernkonzept:** Das [[Singleton]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das sicherstellt, dass von einer [[Klasse]] genau eine [[Instanz]] existiert und einen globalen Zugriffspunkt auf diese [[Instanz]] bereitstellt. Es kontrolliert die [[Instanziierung]] und verhindert die Erzeugung weiterer [[Objekt|Objekte]] dieser [[Klasse]], um [[Konsistenz]] und [[Ressourceneffizienz]] im System zu gewährleisten.
- **Nutzen & Zweck:** Das [[Singleton]] löst das [[Problem]] der mehrfachen [[Instanziierung]] von [[Klasse|Klassen]], die nur einmalig existieren dürfen, um [[Ressourcenverschwendung]] zu vermeiden und [[Konsistenz]] zu garantieren. Es eignet sich besonders für zentrale [[Dienst|Dienste]] wie [[Konfigurationsmanager]], [[Logging-Dienst|Logging-Systeme]] oder [[Datenbankverbindung|Datenbankverbindungen]], bei denen mehrere [[Instanz|Instanzen]] zu [[Konflikt|Konflikten]], [[Inkonsistenz|Inkonsistenzen]] oder unnötigem Overhead führen würden. Durch die Bereitstellung eines globalen Zugriffspunkts vereinfacht es den Zugriff auf zentrale [[Ressource|Ressourcen]] und ermöglicht eine zentrale Steuerung. Im Vergleich zu [[Statische_Klasse|statischen Klassen]] bietet es den Vorteil der [[Lazy_Initialization|lazy Initialization]] (späte Erzeugung bei Bedarf) und die Möglichkeit, [[Schnittstelle|Schnittstellen]] zu implementieren.
- **Abgrenzung & Grenzen:** Das [[Singleton]] ist nicht geeignet, wenn mehrere [[Instanz|Instanzen]] einer [[Klasse]] benötigt werden oder wenn die globale Verfügbarkeit zu unkontrollierten [[Abhängigkeit|Abhängigkeiten]] und schwer testbarem [[Code]] führt. Es kann die [[Testbarkeit]] erschweren, da es schwer zu [[Mocken|mocken]] ist, und verstößt gegen das Prinzip der [[Lose_Kopplung|losen Kopplung]]. In [[Multithreading|multithreaded]] Umgebungen kann es zu [[Nebenläufigkeit|Nebenläufigkeitsproblemen]] kommen, wenn die [[Synchronisation]] nicht korrekt umgesetzt wird. Alternativen wie [[Dependency_Injection]], [[Monostate]] oder [[Statische_Klasse|statische Klassen]] bieten mehr [[Flexibilität]] und bessere [[Testbarkeit]], insbesondere in komplexen Systemen. Zudem führt das [[Singleton]] zu [[Globaler_Zustand|globalem Zustand]], der die [[Wartbarkeit]] und [[Skalierbarkeit]] des Systems beeinträchtigen kann.
- **Beispiel / Code:** ```java
// Thread-sichere Variante mit synchronized (Lazy Initialization)
public class Singleton {
    private static Singleton instance = null;

    private Singleton() {}

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

// Alternative: Early Initialization (thread-sicher, aber ohne Lazy Initialization)
public class SingletonEarly {
    private static final SingletonEarly instance = new SingletonEarly();

    private SingletonEarly() {}

    public static SingletonEarly getInstance() {
        return instance;
    }
}

// Moderne Variante mit Enum (thread-sicher, empfohlen in Java)
public enum SingletonEnum {
    INSTANCE;
    
    public void doSomething() {
        // Logik hier
    }
}
```

**Hinweis:** Die Enum-Variante ist die empfohlene Implementierung in Java, da sie von Haus aus thread-sicher ist und [[Serialisierung|Serialisierung]] sowie [[Reflexion|Reflexionsangriffe]] verhindert. Sie kombiniert die Vorteile der [[Lazy_Initialization]] mit einfacher Syntax und robuster Sicherheit.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1c
- **Vorgänger / Parent:** [[Erzeugungsmuster]]
- **Folgezettel / Unterzettel:**
  - [[Implementierung_des_Singletons]]
  - [[Anwendungsfälle_des_Singletons]]
- **Querverweise:**
  - [[Erzeugungsprozess]]
  - [[Objekterzeugung]]
