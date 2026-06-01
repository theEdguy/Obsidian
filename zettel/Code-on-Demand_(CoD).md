---
id: b3ef2a85-e53f-42de-9976-d6895849e30b
title: "Code-on-Demand (CoD)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code-migration
  - verteilte-systeme
  - client-server
  - mobilität
  - dynamische-ladung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Code-on-Demand (CoD)]]

- **Kernkonzept:** Code-on-Demand (CoD) ist ein [[Migrationsmodell|Migrationsmodelle]] in [[Verteiltes System|Verteilten Systemen]], bei dem ein [[Client]] zur Laufzeit [[Code]] vom [[Server]] anfordert und lokal ausführt, um [[Ressource|Ressourcen]] dynamisch zu erweitern.
- **Nutzen & Zweck:** CoD löst das Problem der statischen [[Funktionalität|Funktionalitäten]]-Bereitstellung, indem es [[Client|Clients]] ermöglicht, [[Code]] bedarfsgerecht nachzuladen. Dies reduziert initiale [[Ladezeit|Ladezeiten]], spart [[Netzwerk]]-Bandbreite und erlaubt flexible Anpassungen ohne [[Server]]-Neustart oder manuelle Updates.
- **Abgrenzung & Grenzen:** CoD sollte nicht genutzt werden, wenn [[Sicherheit]] kritisch ist (z. B. bei unsicheren [[Code]]-Quellen) oder wenn der [[Client]] keine [[Ausführungsumgebung]] für den empfangenen [[Code]] bietet. Alternativen wie [[Mobile Agent|Mobile Agents]] (MA) verschieben den gesamten [[Ausführungszustand]], während CoD nur [[Code]] und [[Daten]] überträgt (schwache [[Mobilität]]). In heterogenen Systemen ist eine [[Abstrakte Maschine]] (z. B. [[Java Virtual Machine|JVM]]) erforderlich.
- **Beispiel / Code:** Ein Webbrowser lädt JavaScript-Code von einem [[Server]] nach, um eine interaktive Benutzeroberfläche zu ermöglichen:
```javascript
// Client fordert Code dynamisch an
const script = document.createElement('script');
script.src = 'https://server.com/dynamic_feature.js';
document.body.appendChild(script);
```
Der geladene [[Code]] wird sofort im [[Client]]-Kontext ausgeführt, ohne dass der [[Server]] den [[Ausführungszustand]] verwaltet.
