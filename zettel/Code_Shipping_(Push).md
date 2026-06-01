---
id: ad486149-f594-4219-ba45-d6c27675a4d4
title: "Code Shipping (Push)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - netzwerk
  - mobilitaet
  - client_server
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Code Shipping (Push)]]

- **Kernkonzept:** Beim [[Code Shipping|Code Shipping (Push)]] wird der [[Code-Segment|Code]] proaktiv vom [[Server]] zum [[Client]] übertragen, um dort ausgeführt zu werden, ohne dass der Client den [[Code]] explizit anfordert.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der effizienten [[Code]]-Verteilung in [[Verteilte Systeme|verteilten Systemen]], indem es die [[Ausführung]] von [[Aufgabe|Aufgaben]] näher am [[Datenbestand]] oder [[Nutzer]] ermöglicht. Es reduziert [[Latenz]] und entlastet den [[Server]], insbesondere bei [[Code-on-Demand]]-Szenarien.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn der [[Client]] keine [[Ressource|Ressourcen]] zur [[Ausführung]] des [[Code]]s besitzt oder wenn [[Sicherheit]]srisiken durch fremden [[Code]] bestehen. Unterscheidet sich von [[Code Fetching (Pull)]], bei dem der [[Client]] den [[Code]] aktiv anfordert. In [[heterogene Systeme|heterogenen Systemen]] kann die [[Portabilität]] des [[Code]]s ein Problem darstellen.
- **Beispiel / Code:** Ein Webserver sendet JavaScript-Code an einen Browser (Client), der diesen lokal ausführt, um dynamische Inhalte ohne erneute Serveranfrage darzustellen:
```javascript
// Beispiel: Code Shipping (Push) via JavaScript
function loadDynamicContent() {
  // Code wird vom Server zum Client 'gepusht'
  const script = document.createElement('script');
  script.src = 'https://server.com/dynamic.js';
  document.body.appendChild(script);
}
```
