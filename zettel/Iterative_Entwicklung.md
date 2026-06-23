---
id: 8b413816-858f-44cd-b517-7e8255421286
title: "Iterative_Entwicklung"
date: 2026-06-24
tags:
  - software_engineering
  - agile_methoden
  - softwareentwicklung
  - projektmanagement
  - draft
source: "SWE Slides – Kapitel 2: Entwicklungsprozesse gestern und heute"
---

# [[Iterative_Entwicklung]]

- **Kernkonzept:** Die [[Iterative_Entwicklung]] ist ein [[Vorgehensmodell|zyklisches Vorgehensmodell]] im [[Software_Engineering]], das ein [[Softwareprojekt]] in kleinere, wiederholbare [[Iteration|Iterationen]] (auch [[Sprint|Sprints]] genannt) zerlegt. Jede [[Iteration]] liefert ein funktionsfähiges [[Inkrement]] des Gesamtsystems und umfasst [[Anforderungsanalyse]], [[Design]], [[Implementierung]] und [[Test]], um [[Feedback]] frühzeitig zu integrieren, [[Anforderung|Anforderungen]] schrittweise zu verfeinern und einen zusammenhängenden Satz von [[Use_Case|Use Cases]] umzusetzen. Ziel ist es, die [[Komplexität]] großer [[Projekt|Projekte]] beherrschbar zu machen, kontinuierlich auf sich ändernde [[Anforderung|Anforderungen]] oder [[Risiko|Risiken]] zu reagieren und durch inkrementelle [[Lieferung|Lieferungen]] die [[Qualität]] des Endprodukts zu steigern.
- **Nutzen & Zweck:** Die [[Iterative_Entwicklung]] existiert, um die [[Komplexität]] großer [[Softwareprojekt|Softwareprojekte]] beherrschbar zu machen und frühzeitig auf Änderungen oder neue [[Anforderung|Anforderungen]] zu reagieren. Sie löst das Problem starrer, linearer [[Vorgehensmodell|Entwicklungsmodelle]] wie dem [[Wasserfallmodell]], indem sie kontinuierliches [[Feedback]] von [[Stakeholder|Stakeholdern]] ermöglicht, [[Risiko|Risiken]] durch frühe Validierung minimiert und die [[Anpassungsfähigkeit]] an sich ändernde Rahmenbedingungen erhöht. Durch die schrittweise [[Risikominimierung]] und inkrementelle [[Lieferung|Lieferungen]] wird die [[Qualität]] des Endprodukts gesteigert, die [[Kommunikation]] zwischen [[Entwickler|Entwicklern]] und [[Stakeholder|Stakeholdern]] verbessert und die Wahrscheinlichkeit von [[Projekt|Projektfehlschlägen]] verringert. Besonders geeignet ist sie für [[Projekt|Projekte]] mit hoher [[Komplexität]] oder unklaren [[Anforderung|Anforderungen]], da sie [[Flexibilität]], [[Agilität]] im [[Projektmanagement]] und diszipliniertes [[Refactoring]] fördert. Der zyklische Prozess unterstützt die schrittweise Verfeinerung der [[Architektur]], die frühzeitige Erkennung von Fehlern oder neuen [[Anforderung|Anforderungen]] und die kontinuierliche Verbesserung der [[Softwarequalität]] durch regelmäßige [[Review|Reviews]] und [[Retrospektive|Retrospektiven]]. Zudem ermöglicht sie die [[Priorisierung]] von [[Funktionalität|Funktionalitäten]] basierend auf [[Stakeholder]]-Feedback, reduziert den [[Aufwand]] für nachträgliche Änderungen durch iterative [[Planung]] und [[Testautomatisierung]] und fördert die kontinuierliche [[Integration]] sowie [[Auslieferung]] von Teilfunktionalitäten. Durch regelmäßige Lieferungen von Teilprodukten wird die [[Kundenzufriedenheit]] erhöht und die [[Projekttransparenz]] verbessert. Jede [[Iteration]] fungiert als Mini-Projekt mit klar definierten Zielen, das Planung, Umsetzung und Review umfasst, um gezielt [[Feedback]] zu sammeln und in die nächste Iteration einfließen zu lassen.
- **Abgrenzung & Grenzen:** Die [[Iterative_Entwicklung]] ist nicht geeignet für [[Projekt|Projekte]] mit stabilen, vollständig bekannten [[Anforderung|Anforderungen]], bei denen ein linearer Ansatz wie das [[Wasserfallmodell]] effizienter wäre. Im Gegensatz zur [[Ad-hoc_Entwicklung]] setzt sie auf strukturierte [[Planung]] und [[Dokumentation]], erfordert jedoch diszipliniertes [[Projektmanagement]], um [[Scope_Creep]] zu vermeiden. Ein weiteres [[Risiko]] besteht in der Notwendigkeit kontinuierlicher [[Testautomatisierung]] und [[Refactoring|Refactorings]], was bei starren [[Anforderung|Anforderungen]] oder langen Freigabezyklen hinderlich sein kann. Zudem ist sie weniger effektiv, wenn [[Stakeholder|Stakeholder]] nicht regelmäßig [[Feedback]] geben können oder wenn die [[Architektur]] des Systems zu Beginn nicht ausreichend flexibel gestaltet wird. Der [[Aufwand]] für iterative [[Planung]] kann bei kleinen oder klar definierten [[Projekt|Projekten]] unverhältnismäßig hoch sein. Alternativen wie das [[Spiralmodell]] betonen zusätzlich explizite [[Risikoanalyse|Risikoanalysen]], während [[Agile_Methoden|agile Methoden]] (z. B. [[Scrum]]) [[Iteration|Iterationen]] mit festen Zeitrahmen ([[Sprint|Sprints]]) und stärkerer [[Teamautonomie]] kombinieren. Bei unklaren [[Ziel|Zielen]] oder unflexiblen [[Team|Teams]] kann der erhöhte Koordinationsaufwand zu Ineffizienz führen. Im Vergleich zu rein sequenziellen [[Vorgehensmodell|Modellen]] erfordert die iterative Entwicklung mehr [[Kommunikation]] und Koordination, was bei instabilen [[Team|Teams]] oder unklaren [[Projekt|Projektzielen]] zu Herausforderungen führen kann. Im Gegensatz zu [[Kanban]], das auf einen kontinuierlichen Fluss ohne feste [[Iteration|Iterationen]] setzt, bietet die iterative Entwicklung klare Zyklen, die jedoch bei sehr kleinen [[Projekt|Projekten]] mit minimaler [[Komplexität]] unnötigen Overhead verursachen können. Iterative Entwicklung sollte vermieden werden, wenn [[Anforderung|Anforderungen]] von Anfang an vollständig und unveränderlich feststehen, bei extrem kurzen Zeitvorgaben oder fehlender Bereitschaft für regelmäßige [[Review|Reviews]] und [[Retrospektive|Retrospektiven]]. Im Vergleich zu rein [[Agile_Methoden|agilen Methoden]] ist sie weniger formalisiert und bietet weniger feste Rahmenbedingungen für die [[Teamorganisation]].
- **Beispiel / Code:** ```java
// Beispiel: Iterative Verbesserung einer Klasse über mehrere Iterationen
public class MitgliedVerwaltung {
    // Iteration 1: Grundlegende Mitgliederdaten
    private String name;
    private String adresse;

    public MitgliedVerwaltung(String name, String adresse) {
        this.name = name;
        this.adresse = adresse;
    }
    
    // Iteration 1: Grundfunktionalität zur Leistungsberechnung
    public int berechneLeistung() {
        return 0; // Initiale Implementierung
    }
    
    // Iteration 2: Erweiterung um Leistungsdaten und Bonusberechnung
    private int leistung;
    private int leistungspunkte;

    public void aktualisiereLeistung(int punkte) {
        this.leistungspunkte = punkte;
        this.leistung = punkte * 10;
    }

    public int berechneLeistung(java.util.Date datum) {
        return this.leistung + getBonus(datum);
    }

    private int getBonus(java.util.Date datum) {
        // Logik zur Bonusberechnung
        return 5;
    }
    
    // Iteration 3: Hinzufügen einer Prognosefunktion und Refactoring
    public int prognostiziereLeistung(int zukuenftigePunkte) {
        return this.leistungspunkte + zukuenftigePunkte;
    }
    
    // Iteration 4: Erweiterung um Validierung und Performance-Optimierung
    public boolean mitgliedHinzufuegen([[Mitglied|Mitglied]] mitglied) {
        if (validiereMitglied(mitglied)) {
            datenbank.speichernAsync(mitglied, callback);
            return true;
        }
        return false;
    }

    private boolean validiereMitglied([[Mitglied|Mitglied]] mitglied) {
        // Validierungslogik
        return mitglied != null && mitglied.getName() != null;
    }
}

// Beispiel für eine iterative Entwicklungsschleife in einem Scrum-Sprint (Pseudocode)
public class Sprint {
    private List<[[User_Story|UserStory]]> backlog;
    private List<[[User_Story|UserStory]]> completedStories;

    public void startIteration() {
        while (!backlog.isEmpty()) {
            [[User_Story|UserStory]] story = backlog.remove(0);
            // 1. Analyse & Design
            designSolution(story);
            // 2. Implementierung
            implementFeature(story);
            // 3. Testen
            if (testFeature(story)) {
                completedStories.add(story);
            } else {
                backlog.add(0, story); // Zurück ins Backlog für nächste Iteration
            }
        }
        // Sprint-Review und Retrospektive
        reviewAndAdapt();
    }
    
    private void designSolution([[User_Story|UserStory]] story) {
        System.out.println("  - Design für [[User_Story|User Story]] " + story.getId() + " erstellt");
    }
    
    private void implementFeature([[User_Story|UserStory]] story) {
        System.out.println("  - [[User_Story|User Story]] " + story.getId() + " implementiert");
    }
    
    private boolean testFeature([[User_Story|UserStory]] story) {
        System.out.println("  - [[User_Story|User Story]] " + story.getId() + " getestet");
        return true; // Vereinfachte Logik
    }
    
    private void reviewAndAdapt() {
        System.out.println("  - [[Review|Sprint-Review]] und [[Retrospektive|Retrospektive]] durchgeführt");
    }
}

// Beispiel für eine iterative Implementierung eines Suchalgorithmus
public class IterativeSearch {
    public static int binarySearch(int[] array, int target) {
        int low = 0;
        int high = array.length - 1;
        
        // Iteration statt Rekursion: Jeder Durchlauf verfeinert die Suche
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (array[mid] == target) {
                return mid;
            } else if (array[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return -1; // Ziel nicht gefunden
    }
}

// Typischer Iterations-Ablauf mit Use Cases und Architektur-Verfeinerung:
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

// Beispiel für eine Iteration in Scrum (Pseudocode)
Sprint 1 (2 Wochen):
- [[User_Story|User Story]] 1: [[Login]]-Funktionalität implementieren
- [[User_Story|User Story]] 2: [[Datenbank]]-Anbindung realisieren
- [[Review|Sprint-Review]] und [[Retrospektive|Retrospektive]] durchführen
```
