---
id: 9e073ba1-4e05-4af4-a576-bdd1b702b547
title: "Analysemodell"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - domain_modeling
  - modellierung
  - draft
source: "software_engineering_kapitel_06"
---

# [[Analysemodell]]

- **Kernkonzept:** Ein [[Analysemodell]] ist ein zentraler Schritt im [[Software_Engineering|Software-Engineering]], der die [[Problemdomäne]] strukturiert in [[Klasse|Klassen]], [[Beziehung|Beziehungen]] und [[Geschäftslogik]] abbildet, um [[Anforderung|Anforderungen]] zu verstehen und eine Grundlage für die [[Architektur]] und das [[Designmodell]] zu schaffen. Es umfasst die Erstellung von [[Use-Case|Use-Case-Modellen]], [[Objektmodell|Objektmodellen]] und funktionalen Modellen, die [[Interaktion|Interaktionen]], [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Beziehung|Beziehungen]] der Systemkomponenten beschreiben.
- **Nutzen & Zweck:** Das [[Analysemodell]] existiert, um die Komplexität von [[Softwareprojekt|Softwareprojekten]] beherrschbar zu machen, indem es ein gemeinsames Verständnis zwischen [[Auftraggeber|Auftraggebern]], [[Entwickler|Entwicklern]] und anderen [[Stakeholder|Stakeholdern]] schafft. Es löst das Problem unklarer oder widersprüchlicher [[Anforderung|Anforderungen]], indem es diese systematisch erfasst, strukturiert und in eine konsistente, nachvollziehbare Form überführt. Dadurch wird die Grundlage für eine zielgerichtete Entwicklung gelegt, das Risiko von Fehlentwicklungen minimiert und spätere Anpassungskosten reduziert. Zudem dient es als Brücke zwischen der [[Problemdomäne]] und dem [[Lösungsraum]], indem es zentrale [[Entität|Entitäten]] und [[Ablauf|Abläufe]] identifiziert und für das [[Designmodell]] vorbereitet.
- **Abgrenzung & Grenzen:** Ein [[Analysemodell]] sollte nicht genutzt werden, wenn das [[Projekt]] trivial oder die [[Problemdomäne]] bereits vollständig verstanden ist, da der Aufwand dann in keinem Verhältnis zum Nutzen steht. Es unterscheidet sich vom [[Designmodell]], das sich auf die technische Umsetzung konzentriert, indem es sich auf den *Problemraum* (Was soll das System leisten?) und nicht auf den *Lösungsraum* (Wie wird es umgesetzt?) fokussiert. Bei [[Agile_Entwicklung|agilen Projekten]] mit stark iterativem Vorgehen kann eine zu detaillierte Modellierung zu Overhead führen, wenn sie nicht flexibel an sich ändernde [[Anforderung|Anforderungen]] angepasst wird. Zudem ist das [[Analysemodell]] kein Ersatz für [[Domain-Driven_Design|DDD]]-Muster, sondern kann durch diese bei komplexen Systemen ergänzt werden.
- **Beispiel / Code:** ```java
// Beispiel: Vereinfachtes Analysemodell für eine Mitgliederverwaltung (Klassendiagramm-Notation)
class Mitglied {
    - mitgliedsnummer: String
    - name: String
    - adresse: [[Adresse|Adresse]]
    
    + datenAendern(neueAdresse: [[Adresse|Adresse]]): void
    + beitragZahlen(betrag: double): void
}

class Adresse {
    - strasse: String
    - plz: String
    - ort: String
}

// Beziehung: Ein Mitglied hat genau eine Adresse (1:1)
// Verantwortlichkeit: Mitglied verwaltet seine eigenen Daten und Zahlungen.
// Hinweis: In einem vollständigen Analysemodell würden zusätzlich Use-Cases und Interaktionen
// zwischen Mitgliedern und anderen Entitäten (z. B. Veranstaltungen) modelliert werden.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a5
- **Vorgänger / Parent:** [[Requirements-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Analyse-Objektmodell]]
  - [[Analyse-Use-Case-Modell]]
  - [[Klassen_finden]]
  - [[Verantwortlichkeiten_definieren]]
- **Querverweise:** keine
