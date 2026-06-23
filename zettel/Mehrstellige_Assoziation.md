---
id: 5acc2c07-f9df-43d6-8f70-72f4301b54e8
title: "Mehrstellige_Assoziation"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - klassendiagramm
  - beziehung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Mehrstellige_Assoziation]]

- **Kernkonzept:** Eine [[Mehrstellige_Assoziation|mehrstellige Assoziation]] beschreibt eine [[Beziehung]] zwischen drei oder mehr [[Klasse|Klassen]] im [[Klassendiagramm]], die gemeinsam eine semantische Einheit bilden und nicht in [[Binäre_Assoziation|binäre Assoziationen]] zerlegt werden können. Jede [[Instanz]] der Assoziation verbindet eine Kombination von [[Instanz|Instanzen]] der beteiligten [[Klasse|Klassen]].
- **Nutzen & Zweck:** Dieses Konzept ermöglicht die präzise Modellierung komplexer [[Beziehung|Beziehungen]], die nicht durch [[Binäre_Assoziation|binäre Assoziationen]] oder [[Assoziationsklasse|Assoziationsklassen]] abgebildet werden können. Es löst das Problem, dass [[Binäre_Assoziation|binäre Assoziationen]] oft nicht ausreichen, um reale Szenarien abzubilden, in denen mehrere [[Objekt|Objekte]] gleichzeitig in einer Beziehung stehen (z. B. ein [[Spiel]] zwischen zwei [[Team|Teams]] in einer bestimmten [[Runde]]). Dadurch bleibt das [[Modell]] konsistent und vermeidet unnötige Redundanzen oder künstliche Aufteilungen, die die [[Kohäsion]] des Systems beeinträchtigen könnten. Besonders nützlich ist dies in der [[Datenbankmodellierung]] oder [[Geschäftsprozessmodellierung]], wo mehrdimensionale Abhängigkeiten direkt dargestellt werden müssen.
- **Abgrenzung & Grenzen:** Mehrstellige Assoziationen sollten nur eingesetzt werden, wenn die [[Beziehung]] nicht durch mehrere [[Binäre_Assoziation|binäre Assoziationen]], [[Assoziationsklasse|Assoziationsklassen]] oder andere [[Entwurfsmuster|Muster]] wie [[Aggregation]] oder [[Komposition]] einfacher und verständlicher modelliert werden kann. Sie erhöhen die Komplexität des [[Modell|Modells]] und sind oft schwerer zu implementieren, insbesondere wenn die beteiligten [[Objekt|Objekte]] unterschiedliche [[Lebenszyklus|Lebenszyklen]] haben oder sich die [[Beziehung|Beziehungen]] dynamisch ändern. Zudem können sie die [[Wartbarkeit]] des Systems beeinträchtigen, da sie die [[Lose_Kopplung|lose Kopplung]] zwischen den [[Klasse|Klassen]] erschweren. Alternativen wie [[Delegation]] oder [[Event-gesteuertes_System|Event-gesteuerte Systeme]] sollten geprüft werden, bevor auf mehrstellige Assoziationen zurückgegriffen wird.
- **Beispiel / Code:** ```java
// Beispiel: Mehrstellige Assoziation für ein Spiel zwischen zwei Teams in einer Runde
class Spiel {
    private Team teamA;
    private Team teamB;
    private Runde ersteRunde;
    private Runde zweiteRunde;
    
    // Constraint: Teams und Runden müssen unterschiedlich sein
    public Spiel(Team teamA, Team teamB, Runde ersteRunde, Runde zweiteRunde) {
        if (teamA.equals(teamB) || ersteRunde.equals(zweiteRunde)) {
            throw new IllegalArgumentException("[[Team|Teams]] und [[Runde|Runden]] müssen unterschiedlich sein.");
        }
        this.teamA = teamA;
        this.teamB = teamB;
        this.ersteRunde = ersteRunde;
        this.zweiteRunde = zweiteRunde;
    }
}

// Alternatives Beispiel: Wettkampf mit mehreren Durchgängen
class Wettkampf {
    private Team teamA;
    private Team teamB;
    private Durchgang ersteRunde;
    private Durchgang zweiteRunde;
    
    // Zusätzliche Validierung für komplexe Constraints
    public Wettkampf(Team teamA, Team teamB, Durchgang ersteRunde, Durchgang zweiteRunde) {
        if (teamA == null || teamB == null || ersteRunde == null || zweiteRunde == null) {
            throw new IllegalArgumentException("Keine [[Instanz|Instanzen]] dürfen null sein.");
        }
        this.teamA = teamA;
        this.teamB = teamB;
        this.ersteRunde = ersteRunde;
        this.zweiteRunde = zweiteRunde;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a1b
- **Vorgänger / Parent:** [[Assoziation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Assoziation]]
  - [[Klassendiagramm]]
