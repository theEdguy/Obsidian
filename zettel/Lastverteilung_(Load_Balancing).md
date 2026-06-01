---
id: 553ea95f-24d8-4502-b195-c95ed10a2fd4
title: "Lastverteilung (Load Balancing)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - skalierbarkeit
  - netzwerk
  - server
  - performance
  - architektur
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Lastverteilung (Load Balancing)]]

- **Kernkonzept:** Lastverteilung (Load Balancing) bezeichnet die [[Verteilung|Verteilung]] von [[Arbeitslast|Arbeitslasten]] auf mehrere [[Server|Server]] oder [[Ressource|Ressourcen]] in einem [[verteilte System|verteilten System]], um [[Überlastung|Überlastungen]] zu vermeiden und die [[Effizienz]] zu steigern.
- **Nutzen & Zweck:** Das Konzept existiert, um die [[Skalierbarkeit]], [[Verfügbarkeit]] und [[Leistung]] von [[System|Systemen]] zu verbessern. Es löst das [[Problem]] der ungleichmäßigen Auslastung von [[Ressource|Ressourcen]] und verhindert [[Engpass|Engpässe]], die zu [[Ausfall|Ausfällen]] oder [[Verzögerung|Verzögerungen]] führen können.
- **Abgrenzung & Grenzen:** Lastverteilung sollte nicht genutzt werden, wenn die [[Komplexität]] des [[System|Systems]] unnötig erhöht wird oder wenn die [[Kosten]] für die Implementierung den [[Nutzen]] übersteigen. Alternativen wie [[statische Zuweisung]] oder [[manuelle Verteilung]] können in einfachen oder hochspezialisierten [[Umgebung|Umgebungen]] sinnvoller sein. Zudem ist Lastverteilung weniger effektiv, wenn die [[Arbeitslast|Arbeitslasten]] nicht parallelisierbar sind.
- **Beispiel / Code:** Ein einfaches Beispiel für Lastverteilung ist ein Round-Robin-Algorithmus in einem [[Server-Cluster]]:

```python
servers = ["Server1", "Server2", "Server3"]
current_server = 0

def get_next_server():
    global current_server
    server = servers[current_server]
    current_server = (current_server + 1) % len(servers)
    return server
```

Hier wird jede eingehende [[Anfrage]] reihum an den nächsten [[Server]] weitergeleitet.
