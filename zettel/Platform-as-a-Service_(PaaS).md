---
id: 6294bbde-86b6-47ba-9645-5c2dc1d3ef8a
title: "Platform-as-a-Service (PaaS)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - cloud-computing
  - verteilte-systeme
  - entwicklung
  - plattform
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Platform-as-a-Service (PaaS)]]

- **Kernkonzept:** Platform-as-a-Service (PaaS) stellt eine [[Cloud-Computing|Cloud-Computing]]-Dienstleistung dar, die Entwickler:innen eine vorgefertigte [[Plattform]] zur Entwicklung, Ausführung und Verwaltung von [[Anwendung|Anwendungen]] ohne Verwaltung der zugrundeliegenden [[Infrastruktur]] bietet.
- **Nutzen & Zweck:** PaaS löst das [[Problem]] der komplexen Einrichtung und Wartung von [[Entwicklungsumgebung|Entwicklungsumgebungen]] und [[Infrastruktur]]. Es ermöglicht schnelle Bereitstellung von [[Anwendung|Anwendungen]], Skalierbarkeit und Fokus auf [[Geschäftslogik]] statt auf Betrieb.
- **Abgrenzung & Grenzen:** PaaS ist nicht geeignet für [[Anwendung|Anwendungen]], die spezifische Hardware- oder Betriebssystemanpassungen erfordern. Im Vergleich zu [[Infrastructure-as-a-Service (IaaS)]] bietet es weniger Kontrolle über die [[Infrastruktur]], während es im Gegensatz zu [[Software-as-a-Service (SaaS)]] keine fertigen [[Anwendung|Anwendungen]] bereitstellt, sondern nur die [[Plattform]] zur Entwicklung.
- **Beispiel / Code:** Ein Beispiel für PaaS ist die Nutzung von **Heroku** zur Bereitstellung einer Node.js-Anwendung:
```javascript
// Einfache Express-Anwendung
const express = require('express');
const app = express();
app.get('/', (req, res) => res.send('Hello World!'));
app.listen(process.env.PORT || 3000);
```
Die Anwendung wird mit einem `git push`-Befehl auf Heroku deployed, ohne dass Server oder Middleware manuell konfiguriert werden müssen.
