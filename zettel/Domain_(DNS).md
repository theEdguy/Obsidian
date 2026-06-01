---
id: ebd70619-6187-444c-ae32-fcef49b25587
title: "Domain (DNS)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - netzwerk
  - namensauflösung
  - verteilte-systeme
  - hierarchie
  - skalierbarkeit
  - protokoll
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Domain (DNS)]]

- **Kernkonzept:** Das [[Domain Name System|DNS]] ist ein hierarchisch organisierter [[Namensraum|Namensraum]], der [[Domain|Domains]] und deren [[Knoten|Knoten]] (z. B. [[Host|Hosts]]) durch strukturierte [[Benennung|Benennungen]] wie `example.com` abbildet. Es ermöglicht die Auflösung von menschenlesbaren [[Namen]] in maschinenverarbeitbare [[Adresse|Adressen]] (z. B. [[IP-Adresse|IP-Adressen]]).
- **Nutzen & Zweck:** Das [[DNS]] löst das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] der [[Namensauflösung]] in [[verteilten Systemen]] durch eine dezentrale, hierarchische Struktur. Es ermöglicht die effiziente Abbildung von [[Namen]] auf [[Adresse|Adressen]] über große geographische Distanzen, ohne zentrale [[Datenbank|Datenbanken]] oder manuelle [[Konfiguration|Konfigurationen]].
- **Abgrenzung & Grenzen:** DNS eignet sich nicht für [[attributbasierte Abfragen]], da es primär auf hierarchische [[Benennung]] ausgelegt ist. Für komplexe [[Suche|Suchanfragen]] nach [[Attribut|Attributen]] (z. B. "alle Server in Amsterdam") sind [[Verzeichnisdienst|Verzeichnisdienste]] wie [[LDAP]] besser geeignet. Zudem ist DNS nicht für dynamische oder häufig wechselnde [[Zuordnung|Zuordnungen]] optimiert, da Änderungen sich erst nach [[Cache|Caching]]-Zeiten global ausbreiten.
- **Beispiel / Code:** Ein typischer DNS-Eintrag in einer Zonendatei:
```
example.com.    IN  SOA   ns1.example.com. admin.example.com. (
                        2023100101 ; Serial
                        3600       ; Refresh
                        1800       ; Retry
                        604800     ; Expire
                        86400 )    ; Minimum TTL

example.com.    IN  A      192.0.2.1
www             IN  CNAME  example.com.
mail            IN  MX     10 mail.example.com.
```
Hier definiert `SOA` die [[Zone]], `A` die [[IP-Adresse]] des [[Hosts]], `CNAME` einen [[Alias]] und `MX` den [[Mailserver]].
