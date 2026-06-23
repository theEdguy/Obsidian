---
id: d39a1191-f0a7-4cb6-ae90-2496deae7572
title: "Use-Case-basierte Analyse"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Use-Case-basierte Analyse]]

- **Kernkonzept:** Die use-case-basierte Analyse ist eine Methode im Software Engineering, bei der Anforderungen und Problemdomänen durch die systematische Untersuchung von Use Cases (Anwendungsfällen) strukturiert erfasst und modelliert werden. Sie dient dazu, zentrale Abläufe, Objekte und Interaktionen im Problemraum zu identifizieren, bevor Lösungsdetails entworfen werden.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Komplexität von Softwareprojekten beherrschbar zu machen, indem es den Fokus auf die Problemdomäne und die Nutzeranforderungen legt. Es löst das Problem, dass Entwickler oft zu früh in technische Details abgleiten, ohne das eigentliche Problem vollständig verstanden zu haben. Durch die Priorisierung und detaillierte Ausarbeitung von Use Cases wird sichergestellt, dass die Software die gewünschten Funktionen korrekt abbildet und die Schnittstellen zwischen System und Akteuren klar definiert sind. Zudem ermöglicht es eine iterative Entwicklung, bei der kritische Anforderungen frühzeitig validiert werden können.
- **Abgrenzung & Grenzen:** Die use-case-basierte Analyse sollte nicht genutzt werden, wenn das Problem oder die Anforderungen noch völlig unklar sind, da sie eine gewisse Struktur und Vorarbeit voraussetzt. Sie eignet sich weniger für Projekte mit stark technisch dominierten Anforderungen (z. B. reine Algorithmenentwicklung oder Systemsoftware), bei denen funktionale Abläufe nicht im Vordergrund stehen. Alternativen wie datenflussorientierte oder zustandsbasierte Analysen können hier sinnvoller sein. Zudem ist die Methode nicht geeignet, um nicht-funktionale Anforderungen (z. B. Performance, Sicherheit) umfassend zu adressieren, da diese oft übergreifend sind und nicht direkt aus Use Cases abgeleitet werden können. Im Vergleich zu agilen Methoden wie User Stories bietet die use-case-basierte Analyse eine detailliertere und formalere Beschreibung, was in komplexen Projekten Vorteile, in einfachen oder schnelllebigen Projekten jedoch Nachteile bringen kann.
- **Beispiel / Code:** ```java
// Beispiel: Systemoperation aus einem Use Case "Mitglieder verwalten"
// (basierend auf der Vorlesung, Operation "abteilungVerlassen")

public class Mitglied {
    private String status;
    private List<Abteilung> abteilungen;
    
    public void abteilungVerlassen(Abteilung abteilung) {
        if (!abteilungen.contains(abteilung)) {
            throw new IllegalArgumentException("Mitglied gehört nicht der Abteilung an.");
        }
        
        abteilungen.remove(abteilung);
        abteilung.informiereLeitung(this);
        
        if (abteilungen.isEmpty()) {
            this.status = "passiv";
            this.benachrichtigeMitglied("Ihr Status wurde auf 'passiv' gesetzt.");
        }
    }
    
    private void benachrichtigeMitglied(String nachricht) {
        // Logik zur Benachrichtigung (z. B. E-Mail oder Systemvermerk)
    }
}

public class Abteilung {
    public void informiereLeitung(Mitglied mitglied) {
        // Logik zur Information der Abteilungsleitung
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Use-Case-Diagramm]]
  - [[Use-Case-Beschreibung]]
  - [[System-Sequenz-Diagramm]]
  - [[Schnittstellenidentifikation]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Objektorientierte_Analyse]]
