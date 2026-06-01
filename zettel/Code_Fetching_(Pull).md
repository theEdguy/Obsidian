---
id: df03b033-afa9-44e3-8d74-4661938e2159
title: "Code Fetching (Pull)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - netzwerk
  - dynamische_erweiterung
  - client_server
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Code Fetching (Pull)]]

- **Kernkonzept:** Beim [[Code Fetching|Code-Fetching]] (Pull) fordert ein [[Client|Clienten]]-System aktiv [[Code|Code]] von einem [[Server|Server]] an, um ihn lokal auszuführen. Dies ermöglicht dynamische [[Erweiterung|Erweiterungen]] der Funktionalität ohne vorherige Installation.
- **Nutzen & Zweck:** Das Konzept löst das Problem der statischen [[Bereitstellung|Bereitstellungen]] von [[Funktionalität|Funktionalitäten]] in [[Verteilte Systeme|verteilten Systemen]]. Es ermöglicht flexible Anpassungen zur Laufzeit, reduziert den initialen [[Ressourcen|Ressourcen]]-Bedarf und unterstützt [[Lastverteilung|Lastverteilungen]] durch bedarfsgesteuerte [[Code]]-Ausführung.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Echtzeit|Echtzeit]]-Anforderungen oder deterministische [[Ausführung|Ausführungen]] kritisch sind, da [[Netzwerk]]-Latenzen die [[Code]]-Anforderung verzögern können. Unterscheidet sich von [[Code Shipping|Code-Shipping]] (Push), bei dem der [[Server]] aktiv [[Code]] an [[Client|Clienten]] sendet. In heterogenen [[Umgebung|Umgebungen]] ist eine [[Abstrakte Maschine|abstrakte Maschine]] (z. B. [[Java Virtual Machine|JVM]]) erforderlich, um [[Portabilität|Portabilität]] zu gewährleisten.
- **Beispiel / Code:** Ein Webbrowser lädt JavaScript-Code von einem [[Server]] nach, um eine interaktive Benutzeroberfläche dynamisch zu erweitern:
```javascript
// Client-seitiger Pull-Mechanismus
fetch('https://example.com/script.js')
  .then(response => response.text())
  .then(code => eval(code));
```
Hierbei wird [[Code]] erst bei Bedarf angefordert und lokal im Browser ausgeführt.
