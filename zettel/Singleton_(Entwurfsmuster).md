---
id: 4b8b9df7-079d-413f-a146-b869a8955558
title: "Singleton_(Entwurfsmuster)"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - software_architektur
  - design_pattern
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Singleton_(Entwurfsmuster)]]

- **Kernkonzept:** Das [[Singleton_(Entwurfsmuster)|Singleton]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das sicherstellt, dass eine [[Klasse]] genau eine [[Instanz]] besitzt und einen globalen Zugriffspunkt auf diese bereitstellt.
- **Nutzen & Zweck:** Es kontrolliert den Zugriff auf eine gemeinsame [[Ressource]] (z. B. [[Konfiguration]], [[Datenbankverbindung]]) und verhindert die unkontrollierte Erzeugung mehrerer [[Instanz|Instanzen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Klasse|Klassen]], die mehrere [[Instanz|Instanzen]] benötigen oder in [[Multithreading|multithreaded]] Umgebungen ohne Synchronisation problematisch sein können. Unterscheidet sich von [[Statische_Klasse|statischen Klassen]], die keine [[Instanz]] erzeugen.
- **Beispiel / Code:** ```java
public class ManageMembers {
    private static ManageMembers instance;

    private ManageMembers() {}

    public static synchronized ManageMembers getInstance() {
        if (instance == null) {
            instance = new ManageMembers();
        }
        return instance;
    }
}
```
