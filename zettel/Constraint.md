---
id: b8065165-8438-485f-837a-69820c945d86
title: "Constraint"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - datenintegrität
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Constraint]]

- **Kernkonzept:** Ein [[Constraint]] ist eine Bedingung oder Regel, die die [[Instanz|Instanzen]] einer [[Assoziation]] oder [[Klasse|Klassen]] einschränkt, um die [[Konsistenz]] und [[Datenintegrität]] des [[Modell|Modells]] zu gewährleisten. Spezialformen wie der [[XOR_Constraint]] erzwingen [[Ausschluss|ausschließende Beziehungen]] zwischen [[Assoziation|Assoziationen]], um "entweder-oder"-Bedingungen abzubilden.
- **Nutzen & Zweck:** [[Constraint|Constraints]] stellen sicher, dass [[Geschäftsregel|Geschäftsregeln]] und [[Datenintegrität]] im [[Modell]] eingehalten werden, indem sie ungültige [[Beziehung|Beziehungen]] oder [[Zustand|Zustände]] ausschließen. Sie sind besonders nützlich, um statische Bedingungen wie Wertebereiche, Kardinalitäten oder [[Ausschluss|ausschließende Abhängigkeiten]] (z. B. via [[XOR_Constraint]]) zu definieren. Dadurch wird die [[Korrektheit]] des [[Modell|Modells]] bereits zur [[Designzeit]] sichergestellt.
- **Abgrenzung & Grenzen:** [[Constraint|Constraints]] eignen sich nicht für dynamische oder komplexe [[Validierung|Validierungen]], die besser durch [[Methode|Methoden]], [[Design_by_Contract]] oder [[Regel-Engine|Regel-Engines]] umgesetzt werden. Eine übermäßige Verwendung kann die [[Lesbarkeit]] des [[Modell|Modells]] beeinträchtigen, insbesondere wenn die Bedingungen schwer nachvollziehbar sind. Spezialformen wie der [[XOR_Constraint]] sind ungeeignet, wenn [[Instanz|Instanzen]] gleichzeitig an mehreren [[Assoziation|Assoziationen]] teilnehmen dürfen.
- **Beispiel / Code:** ```java
// Allgemeiner Constraint: teamA != teamB und ersteRunde != zweiteRunde
class Wettkampf {
    private Team teamA;
    private Team teamB;
    private Runde ersteRunde;
    private Runde zweiteRunde;
    
    public Wettkampf(Team teamA, Team teamB, Runde ersteRunde, Runde zweiteRunde) {
        if (teamA.equals(teamB)) {
            throw new IllegalArgumentException("Teams müssen unterschiedlich sein.");
        }
        if (ersteRunde.equals(zweiteRunde)) {
            throw new IllegalArgumentException("Runden müssen unterschiedlich sein.");
        }
        this.teamA = teamA;
        this.teamB = teamB;
        this.ersteRunde = ersteRunde;
        this.zweiteRunde = zweiteRunde;
    }
}

// XOR-Constraint: Mitglied darf entweder aktiv oder passiv in Vereinen sein, aber nicht beides
class Mitglied {
    private Verein aktivBei;
    private List<Verein> passivBei;
    
    public void setAktivBei(Verein verein) {
        if (passivBei != null && passivBei.contains(verein)) {
            throw new IllegalStateException("Mitglied kann nicht gleichzeitig aktiv und passiv im selben Verein sein.");
        }
        this.aktivBei = verein;
    }
    
    public void addPassivBei(Verein verein) {
        if (aktivBei != null && aktivBei.equals(verein)) {
            throw new IllegalStateException("Mitglied kann nicht gleichzeitig aktiv und passiv im selben Verein sein.");
        }
        if (passivBei == null) {
            passivBei = new ArrayList<>();
        }
        passivBei.add(verein);
    }
}
```
