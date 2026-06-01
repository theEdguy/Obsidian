---
id: d06be099-f183-47a7-a4df-3d39dd733218
title: "Dead Letter Queue (DLQ)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte_kommunikation
  - fehlerbehandlung
  - middleware
  - message_queuing
  - ibm_mq
  - architektur
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Dead Letter Queue (DLQ)]]

- **Kernkonzept:** Eine [[Dead Letter Queue|Dead Letter Queue]] (DLQ) ist eine spezielle [[Warteschlange|Warteschlange]] in [[nachrichtenorientierten Systemen|nachrichtenorientierten Systemen]], die [[Nachricht|Nachrichten]] aufnimmt, die nicht erfolgreich verarbeitet oder zugestellt werden konnten.
- **Nutzen & Zweck:** Die DLQ löst das [[Problem]] der [[Fehlerbehandlung]] in [[verteilten Systemen]]: Sie verhindert den Verlust von [[Nachricht|Nachrichten]], die aufgrund von [[Fehler|Fehlern]] (z. B. ungültiges Format, nicht erreichbare [[Zieladresse|Zieladressen]]) nicht verarbeitet werden können. Dadurch ermöglicht sie eine spätere Analyse und manuelle oder automatisierte [[Korrektur]].
- **Abgrenzung & Grenzen:** Eine DLQ sollte nicht für [[Echtzeitverarbeitung]] oder [[kritische Pfade]] genutzt werden, da sie [[Latenz]] einführt. Alternativen wie [[Retry-Mechanismen]] oder [[Transaktionsprotokolle]] (z. B. [[Zweiphasen-Commit]]) sind besser geeignet, wenn [[Fehler]] sofort behoben werden müssen. Die DLQ ist kein Ersatz für [[Monitoring]] oder [[Logging]], sondern ergänzt diese.
- **Beispiel / Code:** ```
// Beispiel: IBM MQ-Konfiguration einer DLQ (Pseudocode)
DEFINE QLOCAL('MY_QUEUE') +
       REPLACE +
       DEFBIND(NOTFIXED) +
       DLQ('SYSTEM.DEAD.LETTER.QUEUE') +
       PUT(ENABLED) +
       GET(ENABLED)

// Fehlercode bei gescheiterter Zustellung (MQRC)
MQPUT(hQueue, message, &msgDesc, &putOptions, &compCode, &reason);
if (compCode == MQCC_FAILED) {
    // Nachricht wird automatisch in die DLQ verschoben
    printf("Fehler: Nachricht in DLQ verschoben. MQRC: %d\n", reason);
}
```
