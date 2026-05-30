---
id: b27a831f-8977-4cac-b2df-b1119e3e6784
title: "Abstrakte_Klasse"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - entwurf
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Abstrakte_Klasse]]

- **Kernkonzept:** Eine [[abstrakte_Klasse|abstrakte Klasse]] ist eine [[Klasse]], die keine direkten [[Instanz|Instanzen]] besitzt und bewusst unvollständig definiert ist. Sie dient als [[Oberklasse]] für [[Unterklasse|Unterklassen]] und kann [[abstrakte_Methode|abstrakte Methoden]] enthalten, die von [[Unterklasse|Unterklassen]] implementiert werden müssen.
- **Nutzen & Zweck:** Sie ermöglicht die Definition gemeinsamer [[Schnittstelle|Schnittstellen]] und [[Verhalten]] für eine Gruppe verwandter [[Klasse|Klassen]], ohne eine konkrete Implementierung vorzugeben. Dies fördert die [[Wiederverwendbarkeit]] und [[Modularität]] im [[Softwareentwurf]].
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn eine vollständige Implementierung ohne [[Unterklasse|Unterklassen]] benötigt wird. Im Gegensatz zu [[Schnittstelle|Schnittstellen]] können [[abstrakte_Klasse|abstrakte Klassen]] bereits teilweise Implementierungen enthalten. Eine [[abstrakte_Klasse]] ohne [[Unterklasse|Unterklassen]] ist sinnlos.
- **Beispiel / Code:** ```java
public abstract class Team {
    protected String name;
    
    public abstract int leistungsprognose(Date datum);
}

public class DDDTeam extends Team {
    @Override
    public int leistungsprognose(Date datum) {
        return 42; // Beispielimplementierung
    }
}
```
