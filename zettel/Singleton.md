---
id: 4766f538-c875-4f91-b159-5251b4d64ebd
title: "Singleton"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - oop
  - software_architecture
  - draft
source: "SWE Slides (Folien 331-345)"
---

# [[Singleton]]

- **Kernkonzept:** Das [[Singleton]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das sicherstellt, dass von einer [[Klasse]] nur eine einzige [[Instanz]] existiert und einen globalen Zugriffspunkt auf diese [[Instanz]] bereitstellt.
- **Nutzen & Zweck:** Es löst das [[Problem]] der mehrfachen [[Instanzierung]] von [[Klasse|Klassen]], die nur einmalig existieren dürfen (z. B. [[Konfigurationsmanager|Konfigurationsmanager]] oder [[Datenbankverbindung|Datenbankverbindungen]]). Es garantiert [[Konsistenz]] und vermeidet [[Ressourcenverschwendung]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn mehrere [[Instanz|Instanzen]] benötigt werden oder [[Testbarkeit]] erschwert wird. Im Vergleich zu [[Dependency_Injection]] führt es zu [[Globaler_Zustand|globalem Zustand]] und kann [[Nebenläufigkeit|Nebenläufigkeitsprobleme]] verursachen. Alternativen wie [[Monostate]] können ähnliche Ziele erreichen.
- **Beispiel / Code:** ```java
public class Singleton {
    private static Singleton instance = null;

    private Singleton() { }

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
