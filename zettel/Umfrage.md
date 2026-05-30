---
id: 83062da8-924e-4e94-ba49-8480082186e1
title: "Umfrage"
date: 2026-05-30
tags:
  - software_engineering
  - forschung
  - methode
  - empirische_forschung
  - quantitative_methode
  - draft
source: "SWE Slides (Folien 16-30)"
---

# [[Umfrage]]

- **Kernkonzept:** Eine [[empirische_Methode|empirische Methode]], bei der [[Daten]] durch [[Fragebogen|Fragebögen]] oder [[Interview|Interviews]] systematisch aus einer großen [[Stichprobe|Stichprobe]] gesammelt werden, um [[Meinung|Meinungen]], [[Verhalten]], [[Erfahrung|Erfahrungen]] oder [[Software-Engineering|Software-Engineering]]-Praktiken quantitativ oder qualitativ zu erfassen.
- **Nutzen & Zweck:** Ermöglicht die [[Erhebung]] von [[Daten]] zu [[Fragestellung|Fragestellungen]], die nicht durch [[Beobachtung]] oder [[Experiment|Experimente]] zugänglich sind. Besonders nützlich zur Erfassung von [[Benutzerfeedback|Benutzerfeedback]], [[Entwicklererfahrung|Entwicklererfahrungen]] oder [[Markttrend|Markttrends]], um [[Werkzeug|Werkzeuge]], [[Methodik|Methodiken]] oder [[Projektmanagement|Projektmanagement]]-Ansätze zu bewerten. Skalierbar und kostengünstig einsetzbar.
- **Abgrenzung & Grenzen:** Ergebnisse können durch [[Verzerrung|Verzerrungen]] (z. B. [[Selbstauskunft|Selbstauskunftsfehler]]) oder eine unzureichende [[Stichprobenauswahl]] beeinflusst werden. Keine kausalen Aussagen möglich; für Ursache-Wirkungs-Analysen sind [[Kontrolliertes_Experiment|kontrollierte Experimente]] besser geeignet. Die Qualität der [[Frage|Fragestellung]] ist entscheidend für valide Ergebnisse.
- **Beispiel / Code:** ```markdown
# Beispiel: Umfrage zur Nutzung von [[Continuous_Integration|CI]]-Tools
1. Welches CI-Tool nutzen Sie? (Single-Choice)
   - Jenkins
   - GitHub Actions
   - GitLab CI
   - Sonstiges: _______
2. Wie zufrieden sind Sie mit der Integration in Ihren [[Entwicklungsprozess|Entwicklungsprozess]]? (Skala 1-5)
   - 1 (sehr unzufrieden)
   - 2
   - 3
   - 4
   - 5 (sehr zufrieden)
3. Welche [[Herausforderung|Herausforderungen]] sehen Sie bei der Nutzung von CI-Tools? (Freitext)
```

**Anwendungsfall:** [[Fragebogen]] zur [[Zufriedenheit]] von [[Entwickler|Entwicklern]] mit einem neuen [[Entwicklungswerkzeug]] oder zur Evaluation von [[Agile_Praktiken|agilen Praktiken]] in einem Team.
