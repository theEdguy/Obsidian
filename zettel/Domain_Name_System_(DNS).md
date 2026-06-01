---
id: 5b39d675-8966-49a0-a9d7-bbcc088060dd
title: "Domain Name System (DNS)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensauflösung
  - netzwerk
  - hierarchie
  - skalierbarkeit
  - verteilte-systeme
  - protokoll
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Domain Name System (DNS)]]

- **Kernkonzept:** Das [[Domain Name System|DNS]] ist ein hierarchisch organisierter [[Namensraum|Namensräume]], der [[Domain|Domains]] und [[Host|Hosts]] in [[Netzwerk|Netzwerken]] durch menschenlesbare Namen statt numerischer [[IP-Adresse|IP-Adressen]] identifiziert. Es ermöglicht die [[Auflösung|Auflösungen]] von [[Domainname|Domainnamen]] in [[IP-Adresse|IP-Adressen]] und umgekehrt.
- **Nutzen & Zweck:** DNS löst das [[Skalierbarkeitsproblem|Skalierbarkeitsprobleme]] der [[Namensauflösung]] in [[verteilte Systeme|verteilten Systemen]], indem es eine dezentrale, hierarchische Struktur nutzt. Es vermeidet [[Ortsabhängigkeit]] und ermöglicht effiziente [[Kommunikation]] über große geographische Distanzen, ohne dass [[Client|Clients]] alle [[Namensserver|Nameserver]] kennen müssen.
- **Abgrenzung & Grenzen:** DNS ist nicht geeignet für [[attributbasierte Abfragen]], da es auf hierarchischen [[Pfadname|Pfadnamen]] basiert. Alternativen wie [[LDAP]] oder [[Verzeichnisdienst|Verzeichnisdienste]] eignen sich besser für komplexe [[Attribut|Attribut-basierte]] Suchen, z. B. in [[Unternehmensnetzwerk|Unternehmensnetzwerken]]. DNS skaliert jedoch besser für globale [[Namensauflösung|Namensauflösungen]] und ist weniger rechenintensiv.
- **Beispiel / Code:** Ein [[Client]] fragt iterativ oder rekursiv nach der [[IP-Adresse]] von `example.com`:
1. [[Root-Nameserver]] verweist auf [[Top-Level-Domain|TLD]]-Server für `.com`.
2. TLD-Server verweist auf [[autoritativer Nameserver]] für `example.com`.
3. Autoritativer Server liefert die [[IP-Adresse]] `93.184.216.34`.

DNS-Eintrag (Zone-Datei):
```
example.com.  IN  A  93.184.216.34
example.com.  IN  MX 10 mail.example.com.
```
