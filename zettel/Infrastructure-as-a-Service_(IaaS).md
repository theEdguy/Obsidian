---
id: d93473bc-5380-4597-b185-a626d2e032e3
title: "Infrastructure-as-a-Service (IaaS)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - cloud-computing
  - virtualisierung
  - infrastruktur
  - verteilte-systeme
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Infrastructure-as-a-Service (IaaS)]]

- **Kernkonzept:** Infrastructure-as-a-Service (IaaS) stellt virtualisierte [[Rechenressource|Rechenressourcen]] wie [[Server]], [[Speicher]] und [[Netzwerk]] über das Internet bereit, wobei [[Kunde|Kunden]] auf Basis von [[Virtualisierung]] isolierte [[Umgebung|Umgebungen]] nutzen, ohne physische [[Hardware]] verwalten zu müssen.
- **Nutzen & Zweck:** IaaS löst das Problem der Skalierbarkeit und Flexibilität von [[IT-Infrastruktur|IT-Infrastrukturen]], indem es [[Organisation|Organisationen]] ermöglicht, [[Ressource|Ressourcen]] bedarfsgerecht zu mieten und zu verwalten, ohne in physische [[Hardware]] investieren zu müssen. Es reduziert [[Betriebskosten]] und beschleunigt die Bereitstellung von [[Dienst|Diensten]].
- **Abgrenzung & Grenzen:** IaaS sollte nicht genutzt werden, wenn volle Kontrolle über die physische [[Hardware]] oder spezifische [[Compliance]]-Anforderungen erforderlich sind. Im Vergleich zu [[Platform-as-a-Service (PaaS)]] und [[Software-as-a-Service (SaaS)]] bietet IaaS weniger Abstraktion und erfordert mehr manuelle Verwaltung. Für einfache Anwendungsfälle oder hochspezialisierte [[Workload|Workloads]] kann der [[Overhead]] der Virtualisierung nachteilig sein.
- **Beispiel / Code:** Ein typisches Beispiel für IaaS ist die Bereitstellung einer virtuellen Maschine (VM) bei einem Cloud-Anbieter wie AWS oder Azure. Ein Nutzer kann eine VM mit vordefinierter [[Hardware]]-Spezifikation (z. B. 4 vCPUs, 16 GB RAM) starten und ein [[Betriebssystem]] seiner Wahl installieren:

```bash
# Beispiel: Starten einer VM über die AWS CLI
aws ec2 run-instances --image-id ami-0abcdef1234567890 --instance-type t2.medium --key-name MyKeyPair --security-group-ids sg-0abcdef1234567890
```

Die VM läuft isoliert auf der [[Hardware]] des Anbieters und teilt sich ggf. physische [[Ressource|Ressourcen]] mit anderen [[Kunde|Kunden]].
