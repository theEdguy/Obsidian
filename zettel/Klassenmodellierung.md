---
id: 8b038243-0350-47b9-a34e-bf80434c7b60
title: "Klassenmodellierung"
date: 2026-06-23
tags:
  - software_engineering
  - modellierungssprache
  - uml
  - datenmodellierung
  - design
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Klassenmodellierung]]

- **Kernkonzept:** Klassenmodellierung ist ein zentrales Konzept der [[objektorientierte_Analyse_und_Design|objektorientierten Analyse und Design]], bei dem reale oder abstrakte [[Entität|Entitäten]] als [[Klasse|Klassen]] mit Attributen, Operationen und Beziehungen in einem [[UML]]-Modell abgebildet werden, um die statische Struktur und das Verhalten eines Systems zu formalisieren. Sie schafft eine systematische Abstraktion der Problemdomäne und dient als Grundlage für die spätere Implementierung, wobei sie eng mit [[Datenmodellierung]] verwandt ist, die die logische und physische Organisation von Informationen für [[Datenbankdesign]] und Systemarchitektur definiert.
- **Nutzen & Zweck:** Klassenmodellierung ermöglicht eine durchgängige und strukturierte Erfassung komplexer Systeme, indem sie relevante Eigenschaften der Realität in einem formalen Modell abbildet. Sie löst das Problem unstrukturierter Anforderungsanalyse, indem sie eine gemeinsame Sprache für [[Entwickler]], Anwender und [[Stakeholder|Stakeholdern]] schafft, die [[Konsistenz]] und Nachvollziehbarkeit über alle Phasen der Softwareentwicklung hinweg sicherstellt. Dadurch wird die Kommunikation verbessert, Missverständnisse über Anforderungen frühzeitig vermieden und die Grundlage für die Implementierung gelegt. Zudem fördert sie die [[Wiederverwendbarkeit]] von Komponenten und dient als Basis für [[Refactoring]] und iterative Anpassungen. Datenmodellierung ergänzt dies, indem sie die präzise Definition von [[Entität|Entitäten]], Attributen und Relationen ermöglicht, was die [[Datenintegrität]] sichert und effiziente [[Datenbankabfrage|Datenbankabfragen]] sowie objektorientierte Implementierungen unterstützt. Ohne sie entstehen häufig Fehler in der Systemlogik, Performance-Probleme oder hohe Wartungsaufwände durch nachträgliche Anpassungen.
- **Abgrenzung & Grenzen:** Klassenmodellierung sollte nicht eingesetzt werden, wenn das Problem keine klaren [[Entität|Entitäten]] oder Beziehungen aufweist, wie bei rein funktionalen oder [[datenstromorientiertes_System|datenstromorientierten Systemen]]. Sie ist weniger geeignet für kleine, einfache Projekte, bei denen der Overhead der Modellierung den Nutzen übersteigt, oder für Systeme mit hochdynamischen Datenstrukturen, wie [[NoSQL]]-Datenbanken mit schemalosen Ansätzen, wo starre Modelle die [[Agilität]] einschränken. Alternativen wie das [[Entity-Relationship-Modell]] (ERM) eignen sich besser für rein datenbankzentrierte Systeme, während prozedurale Ansätze bei stark algorithmischen Problemen vorzuziehen sein können. Zudem unterscheidet sich Klassenmodellierung von [[Datenmodellierung]] durch die explizite Berücksichtigung von Verhalten (Methoden) und objektorientierten Prinzipien wie [[Vererbung]] oder [[Polymorphismus]]. Sie ist kein Implementierungsmodell, sondern fokussiert auf die konzeptionelle Ebene der Analyse. Eine zu detaillierte Modellierung kann zu unflexiblen Architekturen führen, die iterative Anpassungen erschweren. Im Gegensatz zur [[Use-Case-Modellierung]], die funktionale Anforderungen beschreibt, oder [[Zustandsdiagramm|Zustandsdiagrammen]], die dynamische Abläufe abbilden, konzentriert sich Klassenmodellierung auf die statische Struktur – alle drei Ansätze ergänzen sich, sind aber nicht austauschbar.
- **Beispiel / Code:** ```java
// UML-Klasse "Mitglied" als Java-Implementierung (Klassenmodellierung)
class Mitglied {
    private String mitgliedsId;
    private String name;
    private String adresse;
    private int alter;
    private int leistung;
    private MitgliedStatus status;
    private List<Abteilung> abteilungen;

    public Mitglied(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
        this.leistung = 0;
        this.status = MitgliedStatus.AKTIV;
        this.abteilungen = new ArrayList<>();
    }

    public int leistungsprognose(int tage) {
        return this.leistung + (tage * 10); // Beispielhafte Berechnung
    }

    public void abteilungHinzufuegen(Abteilung abteilung) {
        this.abteilungen.add(abteilung);
    }

    public void abteilungVerlassen(Abteilung abteilung) {
        this.abteilungen.remove(abteilung);
        if (this.abteilungen.isEmpty()) {
            this.status = MitgliedStatus.PASSIV;
        }
    }
}

class Abteilung {
    private String abteilungsId;
    private String name;
    private Mitglied abteilungsleiter;
    private List<Mitglied> mitglieder;

    public Abteilung(String name, Mitglied abteilungsleiter) {
        this.name = name;
        this.abteilungsleiter = abteilungsleiter;
        this.mitglieder = new ArrayList<>();
    }
}

enum MitgliedStatus {
    AKTIV, PASSIV, GESPERRT
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2b
- **Vorgänger / Parent:** [[Objektorientierte_Analyse]]
- **Folgezettel / Unterzettel:**
  - [[Assoziation]]
  - [[Vererbung]]
  - [[Aggregation]]
- **Querverweise:**
  - [[UML]]
  - [[Statische_Modellierung]]
