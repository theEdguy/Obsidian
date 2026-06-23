---
id: edd8f45c-56c6-4b82-b61f-f65a850f7e3b
title: "UML_Notation"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - softwarearchitektur
  - modellierung
  - meta-modell
  - entwurfsmuster
  - notation
  - draft
source: "software_engineering_kapitel_07"
---

# [[UML_Notation]]

- **Kernkonzept:** Die **UML_Notation** (Unified Modeling Language Notation) ist eine standardisierte grafische [[Sprache]] zur Spezifikation, Visualisierung, Konstruktion und Dokumentation von [[Artefakt|Artefakten]] in der [[Softwareentwicklung]]. Sie basiert auf einem [[Meta-Modell]], das alle Beschreibungselemente (z. B. [[Klassendiagramm|Klassendiagramme]], [[Assoziation|Assoziationen]], [[Use-Case-Diagramm|Use-Case-Diagramme]]) formal definiert und in sich selbst in UML_Notation dargestellt wird. Die Notation ermöglicht die einheitliche Darstellung struktureller (z. B. [[Komponentendiagramm|Komponentendiagramme]]) und verhaltensbezogener (z. B. [[Sequenzdiagramm|Sequenzdiagramme]]) Aspekte von [[Softwaresystem|Softwaresystemen]], insbesondere im [[Objektorientierung|objektorientierten]] Kontext.
- **Nutzen & Zweck:** Die UML_Notation dient folgenden Zwecken:
- **Kommunikation**: Schafft eine gemeinsame [[Sprache]] für [[Entwickler]], [[Softwarearchitekt|Architekten]] und [[Stakeholder]] zur Diskussion von [[Softwarearchitektur]] und [[Entwurfsmuster|Entwurfsmustern]], wodurch Missverständnisse reduziert und die Zusammenarbeit strukturiert wird.
- **Abstraktion**: Ermöglicht die Modellierung komplexer [[System|Systeme]] auf verschiedenen Abstraktionsebenen (z. B. Analyse vs. Implementierung) und unterstützt die schrittweise Verfeinerung von [[Anforderung|Anforderungen]] bis zur technischen Umsetzung.
- **Dokumentation**: Liefert präzise, toolgestützte Dokumentation für Wartung, [[Refactoring]] und Weiterentwicklung, indem sie [[Systemverhalten]] und [[Systemstruktur]] visuell und nachvollziehbar festhält.
- **Methodische Durchgängigkeit**: Unterstützt den gesamten [[Softwareentwicklungsprozess]] von der [[Anforderungsanalyse]] (z. B. [[Use-Case-Diagramm|Use-Case-Diagramme]]) über den [[Softwareentwurf]] (z. B. [[Klassendiagramm|Klassendiagramme]]) bis zur Implementierung (z. B. [[Zustandsdiagramm|Zustandsdiagramme]]) und [[Testfall|Testfallerstellung]].
- **Erweiterbarkeit**: Das [[Meta-Modell]] erlaubt die Anpassung an domänenspezifische Bedürfnisse (z. B. durch [[Stereotyp|Stereotypen]] oder Profile) und ermöglicht die Integration in modellgetriebene [[Softwareentwicklung|Entwicklungsansätze]] wie [[MDA]] (Model-Driven Architecture).
- **Problemlösung**: Löst das Problem uneinheitlicher Darstellungen in der [[Softwareentwicklung]], indem sie eine klare, konsistente Syntax für die Modellierung von [[Anforderung|Anforderungen]], [[Architektur]] und [[Design]] bereitstellt.
- **Abgrenzung & Grenzen:** Abgrenzungen und typische Stolpersteine der UML_Notation:
- **Keine Programmiersprache**: UML_Notation beschreibt *was* modelliert wird, nicht *wie* es implementiert wird. Sie eignet sich nicht für die Darstellung algorithmischer [[Logik]] oder detaillierter Implementierungsdetails (z. B. [[Schleifen]], [[Bedingung|Bedingungen]]). Hier sind Alternativen wie [[Pseudocode]] oder konkrete [[Programmiersprache|Programmiersprachen]] besser geeignet.
- **Semantische Lücken**: Die Notation ist präzise, aber die Interpretation hängt vom Kontext ab (z. B. [[Multiplizität|Multiplizitäten]] in [[Assoziation|Assoziationen]] oder die Bedeutung von [[Stereotyp|Stereotypen]]). Ohne klare Konventionen können [[Modell|Modelle]] mehrdeutig werden.
- **Übermodellierung**: Zu detaillierte [[Diagramm|Diagramme]] (z. B. zu viele [[Aktivitätsdiagramm|Aktivitätsdiagramme]] für triviale Abläufe) können die Lesbarkeit beeinträchtigen und den Aufwand ohne Mehrwert erhöhen. UML sollte gezielt eingesetzt werden, um [[Komplexität]] zu reduzieren, nicht zu erhöhen.
- **Toolabhängigkeit**: Unterschiedliche UML-Tools unterstützen nicht alle Notationselemente gleich (z. B. [[Komponentendiagramm|Komponentendiagramm]]-Erweiterungen oder domänenspezifische Profile). Dies kann zu Inkompatibilitäten oder eingeschränkter Austauschbarkeit führen.
- **Kein Ersatz für Code oder Tests**: UML_Notation ersetzt keine [[Testfall|Testfälle]], [[Implementierung]] oder [[Debugging]]-Prozesse. Sie ergänzt diese, indem sie eine abstrakte Sicht auf das [[System]] bietet, aber keine funktionalen oder nicht-funktionalen [[Anforderung|Anforderungen]] validiert.
- **Einsatzgrenzen**: UML eignet sich weniger für nicht-objektorientierte [[Systeme]] (z. B. prozedurale oder funktionale [[Programmierung]]) oder wenn der Modellierungsaufwand den Nutzen übersteigt (z. B. in kleinen oder kurzlebigen Projekten). In solchen Fällen sind informelle Skizzen oder textuelle [[Dokumentation]] oft effizienter.
- **Lernkurve**: Die korrekte Anwendung der UML_Notation erfordert Einarbeitung und Disziplin, insbesondere bei der Nutzung fortgeschrittener Konzepte wie [[OCL]] (Object Constraint Language) oder [[Profil|Profilen]].
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

**Erläuterung des Klassendiagramms**:
- Das [[Klassendiagramm]] zeigt die strukturelle Beziehung zwischen `Vereinsmanager`, `Mitglied` und `MailClient`.
- Die Notation `1 --> *` beschreibt eine [[Assoziation]] mit [[Multiplizität]] (ein `Vereinsmanager` verwaltet viele [[Mitglied|Mitglieder]]).
- Der `note`-Block verweist auf den [[Use-Case]] aus dem Kontext und illustriert die Verbindung zwischen [[Use-Case-Diagramm|Use-Case-Diagramm]] und Klassendiagramm.

```uml
@startuml
left to right direction
actor Vereinsmanager
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
}
Vereinsmanager --> UC1
UC1 <|-- UC2
UC1 <|-- UC3
@enduml
```

**Erläuterung des Use-Case-Diagramms**:
- Das [[Use-Case-Diagramm]] modelliert die [[Funktionalität]] des Systems `MyClub` aus Sicht des [[Akteur|Akteurs]] `Vereinsmanager`.
- Die Beziehungen zwischen den [[Use-Case|Use-Cases]] (`UC1`, `UC2`, `UC3`) zeigen die hierarchische Struktur der [[Anforderung|Anforderungen]] (z. B. "Mitglied anlegen" ist ein Spezialfall von "Mitglieder verwalten").
- Die `left to right direction`-Anweisung verbessert die Lesbarkeit des Diagramms.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 6b
- **Vorgänger / Parent:** [[UML]]
- **Folgezettel / Unterzettel:**
  - [[Notationselemente]]
  - [[Notationsregeln]]
- **Querverweise:**
  - [[UML]]
  - [[Modellierung]]
