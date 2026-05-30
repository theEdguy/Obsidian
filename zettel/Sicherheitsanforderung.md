---
id: 4fef48cf-dad0-4123-98ce-37227778f28f
title: "Sicherheitsanforderung"
date: 2026-05-30
tags:
  - software_engineering
  - security
  - requirements_engineering
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Sicherheitsanforderung]]

- **Kernkonzept:** Eine [[Sicherheitsanforderung]] ist eine [[nicht-funktionale_Anforderung]], die [[Schutzmaßnahme|Schutzmaßnahmen]] gegen [[Bedrohung|Bedrohungen]] wie [[unbefugter_Zugriff]], [[Datenverlust]] oder [[Manipulation]] definiert. Sie umfasst z. B. [[Verschlüsselung]], [[Authentisierung]] und [[Zugriffskontrolle]].
- **Nutzen & Zweck:** Sie stellt sicher, dass [[sensible_Daten]] vor [[Missbrauch]] geschützt werden und das System [[compliant]] mit [[Datenschutzgesetz|Datenschutzgesetzen]] (z. B. [[DSGVO]]) ist. Ohne sie besteht das Risiko von [[Datenpanne|Datenpannen]] und [[Reputationsschaden]].
- **Abgrenzung & Grenzen:** Im Gegensatz zu [[funktionale_Anforderung|funktionalen Anforderungen]] (z. B. "[[Passwort_ändern]]") beschreibt sie keine konkrete [[Funktionalität]], sondern [[Qualitätsmerkmal|Qualitätsmerkmale]] wie [[Vertraulichkeit]] oder [[Integrität]]. Sie sollte nicht mit [[Implementierungsdetail|Implementierungsdetails]] (z. B. "[[AES-256]]") verwechselt werden.
- **Beispiel / Code:** ```plaintext
A1.1: Der Zugriff auf [[Mitgliederdaten]] ist nur nach erfolgreicher [[Authentisierung]] mit [[Zwei-Faktor-Authentisierung]] erlaubt.
```
