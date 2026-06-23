---
id: 2c502bc4-fc8e-45a6-b372-62c03c00d016
title: "Fallstudie"
date: 2026-06-24
tags:
  - software_engineering
  - empirie
  - praxis
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Fallstudie]]

- **Kernkonzept:** Eine [[empirische_Methode|empirische]] und [[explorative_Forschungsmethode|explorative Forschungsmethode]], bei der ein reales [[Projekt]] oder [[Software-System|Software-System]] in seinem natürlichen [[Kontext]] detailliert untersucht wird, um [[Erkenntnis|Erkenntnisse]] über [[Software-Entwicklungsprozess|Software-Entwicklungsprozesse]], [[Herausforderung|Herausforderungen]], [[Erfolg|Erfolge]], [[Anforderung|Anforderungen]] und [[Lösungsansatz|Lösungsansätze]] zu gewinnen. Sie liefert [[Praxiswissen]] aus realen [[Projekt|Projekten]], das in [[Kontrolliertes_Experiment|kontrollierten Experimenten]] nicht abbildbar ist, und ist besonders wertvoll für [[Prozessverbesserung]] und [[Risikomanagement]].
- **Nutzen & Zweck:** Fallstudien liefern tiefe [[Einblicke]] in komplexe [[Zusammenhang|Zusammenhänge]] und [[Kontext|Kontexte]] von [[Software-System|Software-Systemen]] oder [[Projektmanagement|Projektmanagement]]-Herausforderungen. Sie dienen als Grundlage für die Identifikation von [[Best_Practice|Best Practices]] oder [[Anti-Pattern|Anti-Patterns]] und ermöglichen die Ableitung von Handlungsempfehlungen für ähnliche [[Projekt|Projekte]]. Besonders wertvoll sind sie, um [[Prozess|Prozesse]] in realen Umgebungen zu analysieren, wo [[Kontrolliertes_Experiment|kontrollierte Experimente]] nicht durchführbar sind. Darüber hinaus verankern Fallstudien theoretische [[Konzept|Konzepte]] in realistischen [[Szenario|Szenarien]] und vermitteln [[Lernende|Lernenden]] sowie [[Praktiker|Praktikern]] ein greifbares Verständnis für komplexe [[Ablauf|Abläufe]], wie z. B. [[Akteur|Akteursidentifikation]], [[Datenfluss|Datenflüsse]] oder [[Entscheidungslogik|Entscheidungslogik]]. Sie fördern die kritische [[Reflexion]] über [[Design-Entscheidung|Design-Entscheidungen]] und [[Trade-off|Trade-offs]] und lösen das Problem der [[Abstraktion|Abstraktheit]] in der Lehre, indem sie konkrete [[Herausforderung|Herausforderungen]] aufzeigen und [[Lösungsmuster|Lösungsmuster]] für ähnliche [[Projekt|Projekte]] ableitbar machen. Fallstudien sind zudem essenziell für [[Prozessverbesserung]] und [[Risikomanagement]], da sie reale [[Erfahrung|Erfahrungen]] dokumentieren und [[Lessons_Learned|Lessons Learned]] für zukünftige [[Projekt|Projekte]] bereitstellen.
- **Abgrenzung & Grenzen:** Ergebnisse von [[Fallstudie|Fallstudien]] sind kontextabhängig und nicht generalisierbar, da sie keine kausalen Aussagen oder [[Ursache-Wirkungs-Beziehung|Ursache-Wirkungs-Beziehungen]] ermöglichen. Für kausale [[Analyse|Analysen]] eignen sich besser [[Kontrolliertes_Experiment|kontrollierte Experimente]] oder [[quantitative_Methode|quantitative Methoden]]. Die Methode erfordert umfassende [[Dokumentation]] und [[Zugang]] zum untersuchten [[Projekt]] oder [[System]]. Zudem kann die [[Subjektivität]] der [[Beobachter|Beobachter]] oder [[Interpretation|Interpretationen]] die Ergebnisse beeinflussen. Im Vergleich zu [[Umfrage|Umfragen]] oder [[Post-Mortem_Analyse|Post-Mortem-Analysen]] bietet sie jedoch eine höhere [[Tiefe]] der [[Erkenntnis|Erkenntnisse]]. Fallstudien sollten nicht genutzt werden, wenn allgemeingültige [[Regel|Regeln]] oder formale [[Spezifikation|Spezifikationen]] benötigt werden, da sie stets kontextspezifisch sind. Sie eignen sich nicht für [[Hypothesenvalidierung]] und ersetzen keine [[empirische_Studie|empirischen Studien]] oder [[Benchmark|Benchmarks]], wenn eine [[quantitative_Validierung|quantitative Validierung]] erforderlich ist. Im Gegensatz zu generischen [[Leitfaden|Leitfäden]] oder [[Entwurfsmuster|Pattern-Katalogen]] (z. B. [[Singleton|Singleton]] oder [[Observer_Pattern|Observer]]) bieten sie keine universell übertragbaren [[Lösung|Lösungen]], sondern illustrieren spezifische [[Anwendungsfall|Anwendungsfälle]]. Für die frühe Phase der [[Anforderungsanalyse]] sind sie weniger geeignet als systematische [[Erhebungsmethode|Erhebungsmethoden]] wie [[Interview|Interviews]] oder [[Workshop|Workshops]].
- **Beispiel / Code:** # Beispiel: Fallstudie zur Einführung von [[Test-Driven_Development|TDD]] in einem [[Team]]
- **Kontext:** Analyse eines [[Projekt|Projekts]] mit 10 [[Entwickler|Entwicklern]] über 6 Monate.
- **Beobachtung:** Reduktion der [[Bug-Rate|Bug-Rate]] um 30% im Vergleich zu früheren [[Projekt|Projekten]] ohne TDD.
- **Herausforderungen:** Anfangs höhere [[Aufwand|Aufwände]] für [[Testfall|Testfälle]], aber langfristige Steigerung der [[Code-Qualität]].
- **Zielabgleich:** Gegenüberstellung der erwarteten vs. tatsächlichen [[Produktivitätssteigerung|Produktivitätssteigerungen]].

# Beispiel: Fallstudie zur [[Einführung]] von [[DevOps]] in einem [[Unternehmen]]
- **Fokus:** Auswirkungen auf die [[Release-Frequenz]] und [[Zusammenarbeit]] zwischen [[Entwicklung]] und [[Betrieb]].
- **Ergebnis:** Verdopplung der [[Release|Releases]] pro Monat bei gleichzeitiger Reduktion der [[Ausfallzeit|Ausfallzeiten]].
- **Lessons Learned:** Identifikation von [[Best_Practice|Best Practices]] für [[Continuous_Integration|Continuous Integration]] und [[Continuous_Deployment|Continuous Deployment]].

# Beispiel: Fallstudie 'MyClub' – Mitgliederverwaltung mit [[Use_Case|Use Cases]] und [[UML-Diagramm|UML-Diagrammen]]
- **Kontext:** Entwicklung eines Vereinsverwaltungssystems mit Fokus auf [[Mitgliederverwaltung]].
- **Anforderungen:** Verwaltung von [[Mitglied|Mitgliedern]], automatisierte [[Benachrichtigung|Benachrichtigungen]] bei Ein- und Austritt, [[Datenfluss|Datenflüsse]] zwischen [[Akteur|Akteuren]].
- **Lösungsansatz:** Anwendung von [[iterative_Entwicklung|iterativer Entwicklung]] und [[Modellierung]] mit [[Klassendiagramm|Klassendiagrammen]].
- **Herausforderungen:** Identifikation der relevanten [[Akteur|Akteure]], Definition der [[Schnittstelle|Schnittstellen]] zwischen Komponenten, Abbildung der [[Entscheidungslogik|Entscheidungslogik]] für automatisierte Prozesse.
- **Ergebnis:** Erfolgreiche Implementierung eines [[Prototyp|Prototyps]] mit hoher [[Kohäsion]] und [[Lose_Kopplung|lose gekoppelten]] Modulen.

# Beispiel: Fallstudien-Design zur Untersuchung von [[Pair_Programming]]
- **Forschungsfrage:** "Wie beeinflusst [[Pair_Programming]] die [[Code-Qualität]]?"
- **Datenerhebung:** Beobachtung eines [[Team|Teams]] über 6 Monate.
- **Vergleich:** Analyse der [[Code-Qualität]] vor und nach Einführung von [[Pair_Programming]].
- **Ergebnis:** Dokumentation von [[Lessons_Learned|Lessons Learned]] und [[Best_Practice|Best Practices]] für die [[Prozessverbesserung]].

```java
// Beispiel: Vereinfachte Klassenstruktur für die Fallstudie 'MyClub'
// (basierend auf dem Use-Case-Diagramm 'Mitglieder verwalten')
public class Mitglied {
    private String name;
    private String email;
    private LocalDate beitrittsdatum;

    public void austreten() {
        // Logik für Austrittsprozess (z. B. E-Mail-Benachrichtigung)
        System.out.println("[[Mitglied|Mitglied]] " + name + " wurde ausgetragen.");
    }
}

public class Vereinsverwaltung {
    private List<Mitglied> mitglieder;

    public void mitgliedHinzufuegen(Mitglied neuesMitglied) {
        mitglieder.add(neuesMitglied);
        // Szenario: Automatische Willkommens-E-Mail
        sendeEmail(neuesMitglied.getEmail(), "Willkommen im Verein!");
    }

    private void sendeEmail(String empfaenger, String nachricht) {
        // Implementierung der E-Mail-Logik
    }
}
```
