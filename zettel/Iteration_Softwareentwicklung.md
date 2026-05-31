---
aliases:
- Iteration
date: 2026-05-30
id: 5763b02a-946d-4e54-b542-633849e1824e
source: Klausur_Referenz
tags:
- software_engineering
- agile_entwicklung
- software_prozessmodell
- scrum
- inkrementelle_entwicklung
- testgetriebene_entwicklung
- uml_aktivitaetsdiagramm
- draft
title: Iteration_Softwareentwicklung
---

# [[Iteration_Softwareentwicklung]]

- **Kernkonzept:** Eine **Iteration** (auch **Sprint** genannt, besonders im [[Scrum]]) ist ein zeitlich begrenzter Entwicklungszyklus in der [[Agile_Softwareentwicklung]], in dem ein funktionsfähiges, inkrementelles Ergebnis (z. B. ein [[Software_Increment]]) durch die Phasen [[Anforderungsanalyse]], [[Software_Design]], [[Implementierung]] und [[Softwaretest]] entsteht. Jede Iteration bildet ein **Mini-Projekt**, das ein klar definiertes Ziel verfolgt und idealerweise ein auslieferbares Teilprodukt liefert. Design und Implementierung sind dabei eng verzahnt und werden oft nicht strikt getrennt, um Flexibilität und schnelle Anpassungen zu ermöglichen.
- **Nutzen & Zweck:** Iterationen dienen mehreren zentralen Zwecken in der Softwareentwicklung:

1. **Risikominimierung**: Durch kurze Zyklen werden Fehler früh erkannt und korrigiert, bevor sie sich in späteren Phasen auswirken (vgl. [[Fail_Fast_Prinzip]]).
2. **Flexibilität**: Anforderungen können nach jeder Iteration priorisiert und angepasst werden, was besonders in dynamischen Umfeldern (z. B. [[Startups]]) entscheidend ist.
3. **Transparenz**: Regelmäßige [[Review]]s und [[Retrospektive]]n fördern die Zusammenarbeit zwischen Entwicklern, [[Product_Owner]] und Stakeholdern.
4. **Kontinuierliche Lieferung**: Jede Iteration liefert potenziell nutzbare Funktionalität, was die [[Continuous_Delivery]] unterstützt.
5. **Lernprozess**: Das Team reflektiert nach jeder Iteration über Verbesserungspotenziale (z. B. in der [[Definition_of_Done]]).

Iterationen sind ein Kernbestandteil agiler Methoden wie [[Extreme_Programming]] oder [[Kanban]], aber auch in hybriden Ansätzen (z. B. [[V-Modell_XT]]) adaptierbar.
- **Abgrenzung & Grenzen:** 1. **Kein Wasserfallmodell**: Im Gegensatz zum [[Wasserfallmodell]] sind Iterationen **nicht linear** – Phasen wie Design und Implementierung überlappen sich und werden ggf. wiederholt.
2. **Umfang vs. Dauer**: Eine Iteration sollte kurz genug sein (typisch 1–4 Wochen), um Flexibilität zu wahren, aber lang genug, um sinnvolle Fortschritte zu erzielen. Zu kurze Iterationen führen zu Overhead (z. B. durch häufige [[Planning]]-Meetings), zu lange zu Trägheit.
3. **Kein Ersatz für Architektur**: Iteratives Vorgehen ersetzt keine grundlegende [[Softwarearchitektur]] – diese muss frühzeitig skizziert werden (vgl. [[Architekturstil]]), um technische Schulden zu vermeiden.
4. **Stolpersteine**:
   - **Scope Creep**: Unklare Ziele oder nachträgliche Anforderungsänderungen während einer Iteration gefährden das Ergebnis.
   - **Technische Schulden**: Wenn Tests oder Refactoring vernachlässigt werden, häufen sich Probleme (vgl. [[Code_Smell]]).
   - **Teamgröße**: Zu große Teams erschweren die Koordination (vgl. [[Brooks_Law]]).
5. **Nicht für alle Projekte geeignet**: Iterative Ansätze eignen sich weniger für Projekte mit stabilen, klar definierten Anforderungen (z. B. eingebettete Systeme mit Sicherheitszertifizierung).
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Aktivitätsdiagramm (Mermaid-Syntax) veranschaulicht den Ablauf einer Iteration in einem agilen Projekt:', 'diagramm': '```mermaid\nflowchart TD\n    A[Iteration Start] --> B[Planning: Backlog priorisieren]\n    B --> C[Anforderungsanalyse: User Stories verfeinern]\n    C --> D[Design: Architektur & Schnittstellen skizzieren]\n    D --> E[Implementierung: Code schreiben]\n    E --> F[Test: Unit- & Integrationstests]\n    F --> G[Review: Stakeholder-Feedback]\n    G --> H[Retrospektive: Prozess verbessern]\n    H --> I[Iteration Ende: Increment ausliefern]\n    I -->|Nächste Iteration| B\n    style A fill:#f9f,stroke:#333\n    style I fill:#bbf,stroke:#333\n```', 'codebeispiel': {'sprache': 'Java', 'beschreibung': 'Beispiel für eine iterative Implementierung einer einfachen Bankanwendung (vereinfacht): Jede Iteration fügt eine neue Funktion hinzu, während bestehende Tests erhalten bleiben.', 'code': '// Iteration 1: Grundgerüst mit Kontoklasse\npublic class Konto {\n    private double saldo;\n    \n    public void einzahlen(double betrag) {\n        saldo += betrag;\n    }\n    \n    public double getSaldo() {\n        return saldo;\n    }\n}\n\n// Iteration 2: Abheben-Funktion mit Test\npublic class Konto {\n    // ... (vorheriger Code)\n    \n    public void abheben(double betrag) throws IllegalArgumentException {\n        if (betrag > saldo) {\n            throw new IllegalArgumentException("Saldo zu niedrig");\n        }\n        saldo -= betrag;\n    }\n}\n\n// JUnit-Test (wird in jeder Iteration erweitert)\nimport org.junit.jupiter.api.Test;\nimport static org.junit.jupiter.api.Assertions.*;\n\nclass KontoTest {\n    @Test\n    void testEinzahlen() {\n        Konto konto = new Konto();\n        konto.einzahlen(100.0);\n        assertEquals(100.0, konto.getSaldo());\n    }\n    \n    @Test\n    void testAbheben() {\n        Konto konto = new Konto();\n        konto.einzahlen(200.0);\n        konto.abheben(50.0);\n        assertEquals(150.0, konto.getSaldo());\n    }\n    \n    @Test\n    void testAbhebenFehler() {\n        Konto konto = new Konto();\n        assertThrows(IllegalArgumentException.class, () -> konto.abheben(100.0));\n    }\n}'}}
