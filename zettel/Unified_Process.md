---
id: 699959ef-42e4-4c62-87ce-367407d6eabf
title: "Unified Process"
date: 2026-06-24
tags:
  - software_engineering
  - vorgehensmodell
  - softwareentwicklung
  - uml
  - draft
source: "SWE Slides – Kapitel 2: Entwicklungsprozesse gestern und heute"
---

# [[Unified Process]]

- **Kernkonzept:** Der [[Unified_Process]] (UP) ist ein [[iteratives_und_inkrementelles_Vorgehensmodell|iteratives und inkrementelles]] [[Vorgehensmodell]] für die [[Softwareentwicklung]], das auf [[objektorientierte_Analyse_und_Design|objektorientierter Analyse und Design]] (OOAD) basiert. Er strukturiert den Entwicklungsprozess in vier [[Phase|Phasen]] (Inception, Elaboration, Construction, Transition) und betont die Verwendung von [[UML]] zur [[Modellierung]] sowie die Ausrichtung an [[Use-Case|Use-Cases]] für eine systematische, risikoarme und architekturzentrierte Umsetzung.
- **Nutzen & Zweck:** Der [[Unified_Process]] existiert, um komplexe [[Softwareprojekt|Softwareprojekte]] systematisch und risikoorientiert zu steuern. Er löst Probleme wie unklare [[Anforderung|Anforderungen]], unstrukturierte Entwicklungsabläufe und mangelnde [[Anpassungsfähigkeit]] an Veränderungen, indem er [[iterative_Entwicklung|iterative Zyklen]], klare [[Meilenstein|Meilensteine]] und eine enge Verzahnung von [[Analyse]], [[Design]] und [[Implementierung]] fördert. Dadurch ermöglicht er frühzeitiges [[Feedback]], kontinuierliche [[Qualitätssicherung]] und eine bessere Abstimmung zwischen [[Stakeholder|Stakeholdern]] und Entwicklungsteams. Die Verwendung von [[UML]] unterstützt die [[Kommunikation]] zwischen den Beteiligten und reduziert Missverständnisse durch visuelle [[Modellierung]]. Der UP legt besonderen Wert auf die Architekturzentrierung, um langfristige [[Wartbarkeit]] und [[Skalierbarkeit]] der Systeme zu gewährleisten. Durch die Integration von [[Use-Case|Use-Cases]] wird sichergestellt, dass die Entwicklung an den tatsächlichen Bedürfnissen der Nutzer ausgerichtet ist und [[Risiko|Risiken]] frühzeitig identifiziert und minimiert werden.
- **Abgrenzung & Grenzen:** Der [[Unified_Process]] sollte nicht genutzt werden, wenn [[Projekt|Projekte]] sehr klein, einfach oder mit extrem kurzen Entwicklungszyklen (z. B. [[Prototyping]]) umgesetzt werden müssen, da der Aufwand für die Prozessstrukturierung und Dokumentation dann unverhältnismäßig hoch ist. Im Vergleich zu [[agile_Methode|agilen Methoden]] wie [[Scrum]] oder [[Kanban]] ist der UP weniger flexibel und erfordert mehr Dokumentation, was bei dynamischen oder unsicheren [[Anforderung|Anforderungen]] nachteilig sein kann. Alternativen wie [[Extreme_Programming]] (XP) setzen stärker auf direkte [[Code]]-Entwicklung und weniger auf modellbasierte Vorarbeit. Für [[Projekt|Projekte]] mit stabilen [[Anforderung|Anforderungen]] und klaren Zielen eignet sich ein lineares [[Vorgehensmodell]] wie das [[Wasserfallmodell]] besser, während der UP für komplexe, unsichere oder sich ändernde Rahmenbedingungen konzipiert ist. Zudem kann der hohe Dokumentationsaufwand in [[Projekt|Projekten]] mit begrenzten Ressourcen oder kurzen [[Release]]-Zyklen hinderlich sein. Im Gegensatz zu [[agile_Methode|agilen Ansätzen]] fehlt dem UP oft die Fähigkeit, schnell auf kurzfristige Änderungen zu reagieren, was in stark volatilen Umgebungen problematisch sein kann.
- **Beispiel / Code:** ```java
// Beispiel für eine Use-Case-Realisierung im Unified Process (Analysephase)
// Use-Case: "[[Mitglied]] anmelden" mit erweiterter Funktionalität und Architekturzentrierung
public class MitgliedAnmeldung {
    private Mitglied mitglied;
    private Verein verein;
    private MitgliedRepository repository;
    private BenachrichtigungsService benachrichtigungsService;

    public void anmelden(String name, String adresse) {
        mitglied = new Mitglied(name, adresse);
        // Validierung der Eingabedaten
        if (!mitglied.isValide()) {
            throw new IllegalArgumentException("Ungültige Mitgliedsdaten");
        }
        verein.hinzufuegen(mitglied);
        repository.speichern(mitglied);
        benachrichtigungsService.sendeBestätigung(mitglied);
        // Weitere Schritte: Persistenz, Benachrichtigung an [[Stakeholder|Stakeholder]], Protokollierung
    }
}

// Designphase: Klassendiagramm-Transformation in Code mit [[Schnittstelle|Schnittstellen]] und [[Entwurfsmuster|Mustern]]
public class Mitglied {
    private String name;
    private String adresse;
    private int leistung;
    private List<Disziplin> disziplinen;
    private MitgliedStatus status;

    public Mitglied(String name, String adresse) {
        this.name = name;
        this.adresse = adresse;
        this.leistung = 1; // Standardwert
        this.disziplinen = new ArrayList<>();
        this.status = MitgliedStatus.AKTIV;
    }
    
    public boolean isValide() {
        return name != null && !name.isEmpty() && adresse != null && !adresse.isEmpty();
    }
    
    public void hinzufuegenDisziplin(Disziplin disziplin) {
        disziplinen.add(disziplin);
    }
    
    public void aktualisiereLeistung(int neueLeistung) {
        this.leistung = neueLeistung;
    }
    
    public MitgliedStatus getStatus() {
        return status;
    }
}

public class Disziplin {
    private String name;
    private int schwierigkeitsgrad;
    private List<Mitglied> teilnehmendeMitglieder;

    public Disziplin(String name, int schwierigkeitsgrad) {
        this.name = name;
        this.schwierigkeitsgrad = schwierigkeitsgrad;
        this.teilnehmendeMitglieder = new ArrayList<>();
    }
    
    public void hinzufuegenMitglied(Mitglied mitglied) {
        teilnehmendeMitglieder.add(mitglied);
    }
}

// Beispiel für die Verwendung des [[Repository_Pattern|Repository-Musters]] in der Construction-Phase
public interface MitgliedRepository {
    void speichern(Mitglied mitglied);
    Mitglied laden(String name);
    List<Mitglied> findeAlleMitgliederMitStatus(MitgliedStatus status);
}

// Beispiel für die Phasen des Unified Process
/*
1. Inception: Vision & Business Case
   - Definition der Projektziele und des Umfangs
   - Erstellung eines groben [[Use-Case|Use-Case-Diagramms]]
   - Risikoanalyse und Machbarkeitsstudie

2. Elaboration: Architektur-Entwurf & Risikoanalyse
   - Detaillierte [[Modellierung]] der Systemarchitektur mit [[UML]]
   - Identifikation und Minimierung von [[Risiko|Risiken]]
   - Erstellung eines Architekturprototyps

3. Construction: Implementierung & Tests
   - Umsetzung der [[Anforderung|Anforderungen]] in [[Code]]
   - Durchführung von [[Unit_Test|Unit-Tests]] und [[Integrationstest|Integrationstests]]
   - Kontinuierliche [[Qualitätssicherung]]

4. Transition: Auslieferung & Wartung
   - Bereitstellung des Systems für die Nutzer
   - Schulung der [[Stakeholder|Stakeholder]]
   - Wartung und Weiterentwicklung
*/
```
