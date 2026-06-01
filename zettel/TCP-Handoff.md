---
id: ad874f48-ac7c-4ca0-8b97-7a730e2d36b3
title: "TCP-Handoff"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - server-cluster
  - lastverteilung
  - tcp
  - performanz
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[TCP-Handoff]]

- **Kernkonzept:** TCP-Handoff ist ein Verfahren in [[Server-Cluster|Server-Clustern]], bei dem eine bestehende [[TCP-Verbindung|TCP-Verbindung]] von einem [[Logischer Schalter|logischen Schalter]] an einen [[Server]] weitergegeben wird, um die Lastverteilung zu optimieren und Engpässe zu vermeiden.
- **Nutzen & Zweck:** TCP-Handoff löst das [[Problem]] der Überlastung des [[Logischer Schalter|logischen Schalters]] in [[Server-Cluster|Server-Clustern]], indem es die direkte Kommunikation zwischen [[Client]] und [[Server]] ermöglicht, ohne dass der Schalter als Mittler fungieren muss. Dies verbessert die [[Skalierbarkeit]] und [[Performanz]] des Systems.
- **Abgrenzung & Grenzen:** TCP-Handoff sollte nicht genutzt werden, wenn die [[Sicherheit]] oder [[Zustandsverwaltung]] der [[TCP-Verbindung|TCP-Verbindungen]] kritisch ist, da die Weitergabe der Verbindung zusätzliche Komplexität und potenzielle Sicherheitsrisiken mit sich bringt. Alternativen wie [[Load Balancing]] mit [[NAT]] oder [[Reverse Proxy|Reverse-Proxies]] sind einfacher zu implementieren, bieten aber nicht dieselbe [[Performanz]]-Optimierung.
- **Beispiel / Code:** Ein typischer Ablauf von TCP-Handoff:
1. Der [[Client]] baut eine [[TCP-Verbindung]] zum [[Logischer Schalter|logischen Schalter]] auf.
2. Der Schalter entscheidet, welcher [[Server]] den [[Request]] bearbeiten soll.
3. Der Schalter übergibt die [[TCP-Verbindung]] an den ausgewählten [[Server]], der direkt mit dem [[Client]] kommuniziert.
4. Der [[Server]] sendet die [[Response]] direkt an den [[Client]], ohne den Schalter erneut zu involvieren.
