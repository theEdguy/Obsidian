---
id: 49d148d8-c76f-4cb1-a35c-68c69f6a98e6
title: "Iterative_Entwicklung"
date: 2026-05-30
tags:
  - software_engineering
  - prozessmodell
  - vorgehensmodell
  - agile_methoden
  - entwicklungsprozess
  - projektmanagement
  - software_process
  - agile
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[Iterative_Entwicklung]]

- **Kernkonzept:** Die [[Iterative_Entwicklung]] ist ein [[Vorgehensmodell|Vorgehensmodell]] im [[Software_Engineering]], das ein [[Softwareprojekt]] in kleinere, wiederholbare [[Iteration|Iterationen]] (auch [[Sprint|Sprints]] genannt) zerlegt. Jede [[Iteration]] liefert ein funktionsfähiges [[Inkrement]] des Gesamtsystems und umfasst [[Anforderungsanalyse]], [[Design]], [[Implementierung]] und [[Test]], um [[Feedback]] frühzeitig zu integrieren, [[Anforderung|Anforderungen]] schrittweise zu verfeinern und einen zusammenhängenden Satz von [[Use_Case|Use Cases]] umzusetzen.
- **Nutzen & Zweck:** Die [[Iterative_Entwicklung]] ermöglicht die schrittweise [[Risikominimierung]] durch frühes [[Feedback]] und kontinuierliche [[Anpassung]], was besonders bei [[Projekt|Projekten]] mit hoher [[Komplexität]] oder unklaren [[Anforderung|Anforderungen]] nützlich ist. Sie löst das Problem langer [[Entwicklungszeit|Entwicklungszeiten]] und unflexibler [[Anforderung|Anforderungen]] in linearen [[Vorgehensmodell|Modellen]] wie dem [[Wasserfallmodell]], indem sie [[Flexibilität]], [[Agilität]] im [[Projektmanagement]] und inkrementelle [[Lieferung|Lieferungen]] fördert. Zudem reduziert sie [[Risiko|Risiken]] durch kontinuierliche Validierung, ermöglicht diszipliniertes [[Refactoring]] sowie [[Testautomatisierung]] und unterstützt die [[Priorisierung]] von [[Funktionalität|Funktionalitäten]] basierend auf [[Stakeholder]]-Feedback. Besonders geeignet ist sie für [[Projekt|Projekte]], die eine enge Zusammenarbeit mit [[Stakeholder|Stakeholdern]] erfordern, um [[Use_Case|Use Cases]] iterativ zu verfeinern und umzusetzen.
- **Abgrenzung & Grenzen:** Die [[Iterative_Entwicklung]] ist nicht geeignet für [[Projekt|Projekte]] mit stabilen, vollständig bekannten [[Anforderung|Anforderungen]], bei denen ein linearer Ansatz wie das [[Wasserfallmodell]] effizienter wäre. Im Gegensatz zur [[Ad-hoc_Entwicklung|Ad-hoc-Entwicklung]] setzt sie auf strukturierte [[Planung]] und [[Dokumentation]], erfordert jedoch diszipliniertes [[Projektmanagement]], um [[Scope_Creep]] zu vermeiden. Ein weiteres Risiko besteht in der Notwendigkeit kontinuierlicher [[Testautomatisierung]] und [[Refactoring|Refactorings]], was bei starren [[Anforderung|Anforderungen]] oder langen Freigabezyklen hinderlich sein kann. Zudem ist sie weniger effektiv, wenn [[Stakeholder|Stakeholder]] nicht regelmäßig [[Feedback]] geben können oder wenn die [[Architektur]] des Systems zu Beginn nicht ausreichend flexibel gestaltet wird. Der [[Aufwand]] für iterative [[Planung]] kann bei kleinen oder klar definierten [[Projekt|Projekten]] unverhältnismäßig hoch sein.
- **Beispiel / Code:** ```java
// Beispiel: Iterative Verbesserung einer Methode
// Iteration 1: Grundfunktionalität
public int berechneLeistung() {
    return this.leistung;
}

// Iteration 2: Erweiterte Logik mit [[Parameter|Parametern]] und [[Bonusberechnung]]
public int berechneLeistung(Date datum) {
    return this.leistung + getBonus(datum);
}
```

Ein typischer [[Iteration|Iterations]]-Ablauf mit [[Use_Case|Use Cases]] und [[Architektur]]-Verfeinerung:

```plaintext
Iteration 1:
- [[Use_Case|Use Cases]]: Bestellung aufgeben, Zahlung durchführen
- [[Architektur]]: Grundgerüst der [[Datenbank]] und [[Schnittstelle|Schnittstellen]] definieren
- [[Test]]: Grundlegende [[Testabdeckung]] aufbauen

Iteration 2:
- [[Use_Case|Use Cases]]: Produktbewertung, Retourenabwicklung
- [[Architektur]]: Erweiterung um [[Benachrichtigungssystem]] und [[Refactoring]] der [[Datenbank]]
- [[Test]]: [[Testautomatisierung]] ausbauen und [[Feedback]] von [[Stakeholder|Stakeholdern]] einarbeiten

Iteration 3:
- [[Use_Case|Use Cases]]: Benutzerprofilverwaltung, Empfehlungssystem
- [[Architektur]]: Integration eines [[Caching]]-Mechanismus und Optimierung der [[Schnittstelle|Schnittstellen]]
- [[Test]]: Performance-Tests und weitere [[Testautomatisierung]]
```

Typischer [[Iteration|Iterations]]-Zyklus:
1. [[Anforderungsanalyse|Anforderungen]] analysieren
2. [[Design]] erstellen
3. [[Implementierung]] durchführen
4. [[Test]] durchführen
5. [[Feedback]] einarbeiten und für nächste [[Iteration]] planen
