---
id: ebf53df5-c4db-4788-8f9a-e1e5b9707169
title: "Request Dispatching"
date: 2026-06-01
tags:
  - verteilte_systeme
  - server
  - nebenläufigkeit
  - verteilte-systeme
  - architektur
  - netzwerk
  - koordination
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Request Dispatching]]

- **Kernkonzept:** Request [[Dispatching|Dispatching]] ist ein Mechanismus in [[Server|Servern]] von [[Verteilte Systeme|verteilten Systemen]], bei dem eingehende [[Request|Requests]] an separate [[Prozess|Prozesse]] oder [[Thread|Threads]] weitergeleitet werden, um eine nebenläufige Verarbeitung zu ermöglichen.
- **Nutzen & Zweck:** Es löst das [[Problem]] der effizienten und skalierbaren Bearbeitung mehrerer [[Request|Requests]] in [[Server|Servern]], insbesondere bei blockierenden [[Operation|Operationen]] wie [[Datenbank]]-Zugriffen. Dadurch wird die [[Auslastung]] der [[Ressource|Ressourcen]] optimiert und die [[Antwortzeit]] reduziert.
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Anwendung|Anwendungen]] mit geringem [[Request]]-Aufkommen, da der [[Overhead]] für [[Thread]]- oder [[Prozess]]-Verwaltung die [[Performanz]] beeinträchtigen kann. Alternativ können iterative [[Server]] genutzt werden, die [[Request|Requests]] sequenziell abarbeiten, wenn Nebenläufigkeit nicht erforderlich ist.
- **Beispiel / Code:** Ein typischer Aufbau eines nebenläufigen [[Server|Servers]] mit Request [[Dispatching|Dispatching]]:

```
// Pseudocode für einen Dispatcher in einem Server
while (true) {
    Request request = waitForIncomingRequest();
    Thread workerThread = new Thread(() -> processRequest(request));
    workerThread.start();
}
```

Hier wird jeder eingehende [[Request]] an einen neuen [[Thread]] weitergeleitet, der die Verarbeitung übernimmt.
