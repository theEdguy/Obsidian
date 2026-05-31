---
id: 48d13a7c-5b43-4905-90a8-f60441c4edc0
title: "UML_Notation"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - softwarearchitektur
  - modellierung
  - meta-modell
  - entwurfsmuster
  - draft
source: "Klausur_Referenz"
---

# [[UML_Notation]]

- **Kernkonzept:** Die **UML_Notation** (Unified Modeling Language Notation) ist eine standardisierte grafische Sprache zur Spezifikation, Visualisierung, Konstruktion und Dokumentation von Artefakten in der [[Softwareentwicklung]]. Sie basiert auf einem [[Meta-Modell]], das alle Beschreibungselemente (z. B. Klassen, Assoziationen, Use Cases) formal definiert und in sich selbst in UML_Notation dargestellt wird. Die Notation ermöglicht die einheitliche Darstellung struktureller (z. B. [[Klassendiagramm]]) und verhaltensbezogener (z. B. [[Sequenzdiagramm]]) Aspekte von Softwaresystemen.
- **Nutzen & Zweck:** Die UML_Notation dient folgenden Zwecken:
- **Kommunikation**: Schafft eine gemeinsame Sprache für Entwickler, Architekten und Stakeholder zur Diskussion von [[Softwarearchitektur]] und [[Entwurfsmuster]].
- **Abstraktion**: Ermöglicht die Modellierung komplexer Systeme auf verschiedenen Abstraktionsebenen (z. B. Analyse vs. Implementierung).
- **Dokumentation**: Liefert präzise, toolgestützte Dokumentation für Wartung und Weiterentwicklung.
- **Methodische Durchgängigkeit**: Unterstützt den gesamten [[Softwareentwicklungsprozess]] von der Anforderungsanalyse (z. B. [[Use-Case-Diagramm]]) bis zur Implementierung (z. B. [[Zustandsdiagramm]]).
- **Erweiterbarkeit**: Das Meta-Modell erlaubt die Anpassung an domänenspezifische Bedürfnisse (z. B. durch [[Stereotypen]] oder Profile).
- **Abgrenzung & Grenzen:** Abgrenzungen und typische Stolpersteine:
- **Keine Programmiersprache**: UML_Notation beschreibt *was* modelliert wird, nicht *wie* es implementiert wird (z. B. keine Algorithmen).
- **Semantische Lücken**: Die Notation ist präzise, aber die Interpretation hängt vom Kontext ab (z. B. Multiplizitäten in [[Assoziationen]]).
- **Übermodellierung**: Zu detaillierte Diagramme können die Lesbarkeit beeinträchtigen (z. B. zu viele [[Aktivitätsdiagramme]] für triviale Abläufe).
- **Toolabhängigkeit**: Unterschiedliche UML-Tools unterstützen nicht alle Notationselemente gleich (z. B. [[Komponentendiagramm]]-Erweiterungen).
- **Kein Ersatz für Code**: UML_Notation ersetzt keine [[Testfälle]] oder Implementierungsdetails, sondern ergänzt sie.
- **Beispiel / Code:** ```mermaid
classDiagram
    class Vereinsmanager {
        +mitgliederVerwalten()
    }
    class Mitglied {
        -name: String
        -email: String
        +aktualisiereDaten()
    }
    class MailClient {
        +sendeBestätigung()
    }
    Vereinsmanager "1" --> "*" Mitglied : verwaltet
    Vereinsmanager "1" --> "1" MailClient : nutzt
    note for Vereinsmanager "Use Case: Mitglieder verwalten\nAkteure: Vereinsmanager, MailClient\nSystemgrenze: MyClub"
```

**Erläuterung**:
- Das [[Klassendiagramm]] zeigt die strukturelle Beziehung zwischen `Vereinsmanager`, `Mitglied` und `MailClient`.
- Die Notation `1 --> *` beschreibt eine [[Assoziation]] mit Multiplizität (ein Vereinsmanager verwaltet viele Mitglieder).
- Der `note`-Block verweist auf den Use Case aus dem Kontext und illustriert die Verbindung zwischen [[Use-Case-Diagramm]] und Klassendiagramm.
