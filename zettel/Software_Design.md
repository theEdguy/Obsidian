---
id: 4d7fab59-d45a-4d27-865f-124b911be660
title: "Software_Design"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - uml
  - entwurfsmuster
  - objektorientierung
  - systementwurf
  - use_case
  - klassendiagramm
  - zustandsdiagramm
  - draft
source: "Klausur_Referenz"
---

# [[Software_Design]]

- **Kernkonzept:** Software-Design ist die Phase im [[Softwareentwicklungsprozess]], in der auf Basis der [[Anforderungsanalyse]] und des [[Systementwurfs]] konkrete Lösungsstrukturen für die Umsetzung eines Softwaresystems entworfen werden. Es umfasst sowohl den [[Architekturentwurf]] (z. B. Aufteilung in [[Subsysteme]], Steuerungs- und Datenhaltungsstrategien) als auch den [[Objektentwurf]] (z. B. Definition von [[Klassen]], [[Schnittstellen]] und deren Beziehungen). Ziel ist die Transformation abstrakter Modelle (wie [[Use_Cases]] oder [[Analyse_Objektmodell]]) in technische Spezifikationen, die direkt implementierbar sind. Typische Artefakte sind [[Klassendiagramme]], [[Zustandsdiagramme]] und [[Mockups]].
- **Nutzen & Zweck:** 1. **Brücke zwischen Analyse und Implementierung**: Design übersetzt fachliche Anforderungen in technische Strukturen, z. B. durch die Verfeinerung von [[Use_Cases]] zu [[System_Use_Cases]] mit Input-Output-Terminologie. 
2. **Komplexitätsmanagement**: Durch die Aufteilung in [[Subsysteme]] und die Anwendung von [[Entwurfsmustern]] (z. B. [[MVC_Pattern]]) wird die Wartbarkeit und Skalierbarkeit des Systems verbessert. 
3. **Risikominimierung**: Iterative Prototypen (z. B. [[Mockups]]) und [[UML]]-Diagramme ermöglichen frühzeitiges Feedback und Korrekturen. 
4. **Standardisierung**: Designentscheidungen werden dokumentiert (z. B. via [[Klassendiagramm]]), was die Zusammenarbeit im Team und die spätere Erweiterung erleichtert.
- **Abgrenzung & Grenzen:** 1. **Keine Implementierung**: Design beschreibt *wie* etwas umgesetzt wird, nicht die konkrete Code-Realisierung (vgl. [[Implementierungsphase]]). 
2. **Keine Analyse**: Während die [[Anforderungsanalyse]] das *Was* (z. B. Use Cases) definiert, fokussiert Design das *Wie* (z. B. [[Objektentwurf]]). 
3. **Technische vs. fachliche Sicht**: Design berücksichtigt technische Rahmenbedingungen (z. B. Performance, [[Datenhaltung]]), während die Analyse fachliche Anforderungen priorisiert. 
4. **Stolpersteine**: 
   - **Über-Engineering**: Zu frühe Festlegung auf komplexe [[Entwurfsmuster]] ohne Notwendigkeit. 
   - **Unklare Schnittstellen**: Fehlende oder inkonsistente Definition von [[Schnittstellen]] zwischen [[Subsystemen]]. 
   - **Vernachlässigung der Architektur**: Fokus auf Details (z. B. einzelne Klassen) statt auf [[Architekturmuster]] (z. B. [[Schichtenarchitektur]]). 
   - **Iterationsbedarf**: Design ist kein linearer Prozess – Änderungen in späteren Phasen (z. B. durch neue Anforderungen) erfordern Anpassungen.
- **Beispiel / Code:** ```mermaid
classDiagram
    class Bestellung {
        -bestellNr: String
        -datum: Date
        +berechneGesamtpreis() double
    }
    
    class Kunde {
        -kundenNr: String
        -name: String
        +getAdresse() Adresse
    }
    
    class Artikel {
        -artikelNr: String
        -preis: double
        +getBeschreibung() String
    }
    
    Bestellung "1" *-- "1..*" Artikel : enthält
    Bestellung "1" --> "1" Kunde : gehört zu
    
    note for Bestellung "Design-Entscheidung:\n- Aggregation für Artikel (Bestellung existiert unabhängig).\n- Assoziation zu Kunde (Kunde kann mehrere Bestellungen haben)."
```

**Erläuterung**: 
- Das [[Klassendiagramm]] zeigt den [[Objektentwurf]] für ein Bestellsystem. 
- Die Beziehung zwischen `Bestellung` und `Artikel` ist eine *Aggregation* (lose Kopplung), während `Bestellung` und `Kunde` eine *Assoziation* darstellen. 
- Methoden wie `berechneGesamtpreis()` sind bereits auf Design-Ebene spezifiziert, aber noch nicht implementiert.
