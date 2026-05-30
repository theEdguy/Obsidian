---
aliases:
- System_Sequenzdiagramm
- Sequenzdiagramm
- Systemsequenzdiagramm
date: 2026-05-30
id: 7c58df1e-19bc-4969-bd9f-a017f7c4183b
source: SWE Slides (Folien 301-315)
tags:
- software_engineering
- uml
- anforderungsanalyse
- modellierung
- draft
title: System-Sequenz-Diagramm
---

# [[System-Sequenz-Diagramm]]

- **Kernkonzept:** Ein [[System-Sequenz-Diagramm]] ist eine spezielle Form des [[Sequenzdiagramm|Sequenzdiagramms]], das die Interaktion zwischen einem [[Akteur]] und dem [[System]] auf hoher Ebene darstellt, ohne interne [[Komponente|Komponenten]] zu zeigen.
- **Nutzen & Zweck:** Dient der Modellierung von [[Anwendungsfall|Anwendungsfällen]] aus der Perspektive des [[Akteur|Akteurs]], um die [[Schnittstelle]] des [[System|Systems]] zu definieren und [[Anforderung|Anforderungen]] zu klären.
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung interner [[Ablauf|Abläufe]] oder [[Kommunikation|Kommunikation]] zwischen [[Komponente|Komponenten]]. Für detaillierte [[Interaktion|Interaktionen]] besser [[Sequenzdiagramm|Sequenzdiagramme]] nutzen.
- **Beispiel / Code:** ```uml
:Akteur -> System: Systemoperation(parameter)
System -> Akteur: Antwort()
```
