---
id: 060ccb90-cf74-47cd-b10f-ad1412469d3c
title: "Fallstudie"
date: 2026-05-30
tags:
  - software_engineering
  - forschung
  - methode
  - empirische_forschung
  - qualitative_methode
  - draft
source: "SWE Slides (Folien 16-30)"
---

# [[Fallstudie]]

- **Kernkonzept:** Eine [[empirische_Methode|empirische]] und [[explorative_Forschungsmethode|explorative Forschungsmethode]], bei der ein reales [[Projekt]] oder [[Software-System|Software-System]] in seinem natürlichen [[Kontext]] detailliert untersucht wird, um [[Erkenntnis|Erkenntnisse]] über [[Software-Entwicklungsprozess|Software-Entwicklungsprozesse]], [[Herausforderung|Herausforderungen]] oder [[Erfolg|Erfolge]] zu gewinnen. Ziel ist die Gewinnung praxisnaher [[Einblicke]] in komplexe [[Zusammenhang|Zusammenhänge]], die in [[Labor]]-Experimenten nicht abgebildet werden können.
- **Nutzen & Zweck:** Liefert tiefe [[Einblicke]] in komplexe [[Zusammenhang|Zusammenhänge]] und [[Kontext|Kontexte]] von [[Software-System|Software-Systemen]] oder [[Projektmanagement|Projektmanagement]]-Herausforderungen. Dient als Grundlage für die Identifikation von [[Best_Practice|Best Practices]] oder [[Anti-Pattern|Anti-Patterns]] und ermöglicht die Ableitung von Handlungsempfehlungen für ähnliche [[Projekt|Projekte]]. Besonders wertvoll, um [[Prozess|Prozesse]] in realen Umgebungen zu analysieren, wo [[Kontrolliertes_Experiment|kontrollierte Experimente]] nicht durchführbar sind.
- **Abgrenzung & Grenzen:** Ergebnisse sind kontextabhängig und nicht generalisierbar, da [[Fallstudie|Fallstudien]] keine kausalen Aussagen ermöglichen. Für kausale Analysen eignen sich besser [[Kontrolliertes_Experiment|kontrollierte Experimente]]. Die Methode erfordert umfassende [[Dokumentation]] und [[Zugang]] zum untersuchten [[Projekt]] oder [[System]]. Zudem kann die [[Subjektivität]] der [[Beobachter|Beobachter]] oder [[Interpretation|Interpretationen]] die Ergebnisse beeinflussen. Im Vergleich zu [[Umfrage|Umfragen]] oder [[Post-Mortem_Analyse|Post-Mortem-Analysen]] bietet sie jedoch eine höhere [[Tiefe]] der [[Erkenntnis|Erkenntnisse]].
- **Beispiel / Code:** ```markdown
# Beispiel: Fallstudie zur Einführung von [[Test-Driven_Development|TDD]] in einem [[Team]]
- **Kontext:** Analyse eines [[Projekt|Projekts]] mit 10 [[Entwickler|Entwicklern]] über 6 Monate.
- **Beobachtung:** Reduktion der [[Bug-Rate|Bug-Rate]] um 30% im Vergleich zu früheren [[Projekt|Projekten]] ohne TDD.
- **Herausforderungen:** Anfangs höhere [[Aufwand|Aufwände]] für [[Testfall|Testfälle]], aber langfristige Steigerung der [[Code-Qualität]].
- **Zielabgleich:** Gegenüberstellung der erwarteten vs. tatsächlichen [[Produktivitätssteigerung|Produktivitätssteigerungen]].

# Beispiel: Fallstudie zur [[Einführung]] von [[DevOps]] in einem [[Unternehmen]]
- **Fokus:** Auswirkungen auf die [[Release-Frequenz]] und [[Zusammenarbeit]] zwischen [[Entwicklung]] und [[Betrieb]].
- **Ergebnis:** Verdopplung der [[Release|Releases]] pro Monat bei gleichzeitiger Reduktion der [[Ausfallzeit|Ausfallzeiten]].
- **Lessons Learned:** Identifikation von [[Best_Practice|Best Practices]] für [[Continuous_Integration|Continuous Integration]] und [[Continuous_Deployment|Continuous Deployment]].
```
