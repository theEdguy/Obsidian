---
id: 9229004d-7f88-4c8e-80e0-3f6b225c43e4
title: "Software-as-a-Service (SaaS)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - cloud-computing
  - verteilte-systeme
  - softwarearchitektur
  - dienstmodelle
  - virtualisierung
  - client-server
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Software-as-a-Service (SaaS)]]

- **Kernkonzept:** Software-as-a-Service (SaaS) bezeichnet ein [[Verteilungsmodell|Verteilungsmodelle]], bei dem [[Anwendung|Anwendungen]] über das [[Internet]] bereitgestellt und von [[Nutzer|Nutzern]] als Dienst genutzt werden, ohne lokale Installation oder Wartung.
- **Nutzen & Zweck:** SaaS löst das Problem der aufwendigen [[Softwareverteilung|Softwareverteilungen]], [[Aktualisierung|Aktualisierungen]] und [[Skalierung|Skalierungen]] durch zentrale Bereitstellung. Es ermöglicht [[Kosteneffizienz]], globale [[Verfügbarkeit]] und vereinfacht die [[Zusammenarbeit]] in [[verteilten Systemen]].
- **Abgrenzung & Grenzen:** SaaS eignet sich nicht für [[Anwendung|Anwendungen]] mit hohen [[Latenzanforderung|Latenzanforderungen]], strengen [[Datenschutz|Datenschutzvorgaben]] oder spezifischen [[Hardwareanbindung|Hardwareanbindungen]]. Alternativen wie [[Infrastructure-as-a-Service (IaaS)|IaaS]] oder [[Platform-as-a-Service (PaaS)|PaaS]] bieten mehr Kontrolle, erfordern aber auch mehr [[Verwaltungsaufwand]].
- **Beispiel / Code:** Ein typisches SaaS-Beispiel ist Google Workspace (ehemals G Suite). Nutzer greifen über einen Webbrowser auf Anwendungen wie Google Docs zu:
```
// Client-seitiger Aufruf einer SaaS-Anwendung (JavaScript)
function loadGoogleDocs() {
  window.location.href = 'https://docs.google.com';
  // Keine lokale Installation nötig; Daten werden in der Cloud gespeichert.
}
```
Die gesamte Logik, Speicherung und Verarbeitung erfolgt serverseitig.
