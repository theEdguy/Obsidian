---
id: 30d410ca-dc44-49f1-89e8-8898e0a76026
title: "Hierarchisch organisierter Namensraum"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensverwaltung
  - netzwerk
  - skalierbarkeit
  - dns
  - hierarchie
  - koordination
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hierarchisch organisierter Namensraum]]

- **Kernkonzept:** Ein hierarchisch organisierter [[Namensraum|Namensräume]] strukturiert [[Name|Namen]] in einer Baum- oder Graphenform, um [[Entität|Entitäten]] wie [[Knoten]] oder [[Dienst|Dienste]] eindeutig zu identifizieren und effizient aufzulösen. Jeder [[Knoten]] hat genau eine eingehende [[Kante]], deren Beschriftung seine Position im [[Namensraum]] definiert.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Skalierbarkeitsproblem]] in [[verteilten Systemen]] durch rekursive oder iterative [[Namensauflösung]], um [[Knoten]] über große geographische Distanzen hinweg effizient zu lokalisieren. Es ermöglicht eine klare Trennung von [[Logik]] und [[Ortsabhängigkeit]], reduziert [[Kommunikationsaufwand|Kommunikationsaufwände]] und vereinfacht die Verwaltung komplexer [[Systeme]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]], die flexible, attributbasierte [[Abfrage|Abfragen]] benötigen, da hierarchische [[Namensräume]] starre Strukturen voraussetzen. Alternativen wie [[attributbasierte Benennung]] (z. B. [[LDAP]]) sind besser für dynamische oder unstrukturierte [[Daten]] geeignet, erfordern jedoch höheren [[Rechenaufwand|Rechenaufwand]] für [[Suche|Suchoperationen]]. Bei flachen [[Namensräumen]] oder kleinen [[Systemen]] ist der Overhead der Hierarchie unnötig.
- **Beispiel / Code:** Beispiel: DNS-Namensauflösung für die Domain `example.cs.vu.nl`:
1. Client sendet Anfrage an lokalen [[Nameserver]].
2. Falls nicht bekannt, leitet der [[Nameserver]] die Anfrage iterativ weiter:
   - Root-Server verweist auf `.nl`-Server.
   - `.nl`-Server verweist auf `vu.nl`-Server.
   - `vu.nl`-Server verweist auf `cs.vu.nl`-Server.
3. `cs.vu.nl`-Server liefert die IP-Adresse (z. B. `130.37.20.20`) für `example.cs.vu.nl`.

DNS-Eintrag (Zone-Datei):
```
example.cs.vu.nl.  IN  A  130.37.20.20
cs.vu.nl.        IN  NS ns.cs.vu.nl.
```
