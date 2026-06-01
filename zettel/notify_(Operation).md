---
id: f0e3a5cd-787e-4191-90fc-a44a84d3ec1f
title: "notify (Operation)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte-middleware
  - ereignisgesteuerte-architektur
  - asynchrone-kommunikation
  - message-queuing
  - handler
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[notify (Operation)]]

- **Kernkonzept:** Die [[Operation|Operation]] `notify` ermöglicht in [[nachrichtenorientierte|nachrichtenorientierten]] [[Middleware|Middlewares]] (MOM) die asynchrone Benachrichtigung eines [[Handler|Handlers]], sobald eine [[Nachricht]] in eine [[Warteschlange|Warteschlange]] gestellt wird. Sie blockiert nicht und erlaubt so nicht-blockierende [[Kommunikation]] zwischen [[Komponente|Komponenten]].
- **Nutzen & Zweck:** Die `notify`-Operation löst das [[Problem]] der [[Echtzeit|Echtzeitkommunikation]] ohne aktives [[Polling]] (ständiges Abfragen). Sie ermöglicht [[Ereignis|ereignisgesteuerte]] Architekturen, indem [[Anwendung|Anwendungen]] nur bei relevanten [[Änderung|Änderungen]] reagieren, was [[Ressource|Ressourcen]] schont und die [[Latenz]] reduziert.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Szenario|Szenarien]], die garantierte [[Zustellung]] oder [[Reihenfolge]] erfordern – hier sind blockierende [[Operation|Operationen]] wie `get` oder [[Transaktion|Transaktionen]] vorzuziehen. Im Gegensatz zu `poll` blockiert `notify` nie, kann aber [[Nachricht|Nachrichten]] verpassen, wenn der [[Handler]] nicht rechtzeitig installiert ist. Für [[synchron]]e Kommunikation (z. B. [[RPC]]) ist `notify` ungeeignet.
- **Beispiel / Code:** // Pseudocode: Installation eines Handlers in einer Message-Queuing Middleware
queue.installHandler("myQueue", (message) => {
    console.log("Neue Nachricht erhalten:", message.content);
});

// Nachricht wird asynchron zugestellt, Handler wird automatisch aufgerufen
queue.put("myQueue", { content: "Hallo, Welt!" });
// Ausgabe: "Neue Nachricht erhalten: Hallo, Welt!" (ohne aktives Warten)
