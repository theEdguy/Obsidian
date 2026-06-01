---
id: 972b9f33-1b8d-493f-84c1-707cc7188458
title: "Lastverteilung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - skalierbarkeit
  - performanz
  - server_architektur
  - netzwerk
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Lastverteilung]]

- **Kernkonzept:** Lastverteilung bezeichnet die [[Verteilung|Verteilung]] von [[Berechnungslast|Berechnungslasten]] oder [[Anfrage|Anfragen]] auf mehrere [[Server|Server]] oder [[Ressource|Ressourcen]], um [[Überlastung|Überlastungen]] zu vermeiden und die [[Effizienz]] zu steigern.
- **Nutzen & Zweck:** Das Konzept existiert, um die [[Auslastung]] von [[System|Systemen]] zu optimieren, [[Antwortzeit|Antwortzeiten]] zu verkürzen und [[Skalierbarkeit]] in verteilten [[System|Systemen]] zu ermöglichen. Es löst das Problem ungleichmäßiger [[Last|Lasten]] und verhindert [[Engpass|Engpässe]].
- **Abgrenzung & Grenzen:** Lastverteilung sollte nicht genutzt werden, wenn die [[Komplexität]] des [[System|Systems]] unnötig erhöht wird oder wenn die [[Latenz]] durch zusätzliche [[Koordination]] die [[Performanz]] verschlechtert. Alternativen wie [[Caching]] oder [[Replikation]] können in einfachen Fällen ausreichen.
- **Beispiel / Code:** Ein einfacher Round-Robin-Algorithmus in Python zur Lastverteilung auf drei Server:

```python
servers = ['server1', 'server2', 'server3']
current_server = 0

def get_next_server():
    global current_server
    server = servers[current_server]
    current_server = (current_server + 1) % len(servers)
    return server
```

In verteilten Systemen wird oft ein [[Load Balancer]] wie Nginx oder HAProxy eingesetzt, um Anfragen dynamisch zu verteilen.
