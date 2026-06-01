---
id: 70ca0331-35e2-446e-a734-5a9e4e22c5eb
title: "Domain Name (DNS)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensauflösung
  - netzwerk
  - hierarchie
  - skalierbarkeit
  - protokoll
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Domain Name (DNS)]]

- **Kernkonzept:** Das Domain Name System (DNS) ist ein hierarchisch organisierter [[Namensraum|Namensräume]], der [[Domain|Domains]] und [[Host|Hosts]] in einem [[Netzwerk]] durch menschenlesbare Namen (z. B. `example.com`) auf [[IP-Adresse|IP-Adressen]] abbildet. Es ermöglicht die skalierbare Auflösung von Namen in verteilten [[System|Systemen]].
- **Nutzen & Zweck:** DNS löst das [[Skalierbarkeitsproblem]] der manuellen Verwaltung von [[IP-Adresse|IP-Adressen]] in großen [[Netzwerk|Netzwerken]] wie dem Internet. Es ermöglicht [[Namensauflösung]] über geographische Distanzen hinweg und unterstützt verschiedene [[Dienst|Dienste]] (z. B. E-Mail, Web) durch spezifische [[Eintragstyp|Eintragstypen]] wie MX oder SRV.
- **Abgrenzung & Grenzen:** DNS eignet sich nicht für [[attributbasierte Suche|attributbasierte Suchen]], da es auf hierarchischen [[Struktur|Strukturen]] basiert. Alternativen wie [[LDAP]] oder [[Verzeichnisdienst|Verzeichnisdienste]] sind besser für komplexe Abfragen nach Attributen geeignet. DNS ist zudem nicht für dynamische oder häufig wechselnde [[Zuordnung|Zuordnungen]] optimiert (z. B. mobile Geräte).
- **Beispiel / Code:** Ein DNS-Eintrag für einen Webserver in der Zone `example.com`:
```
example.com.    IN  A      192.0.2.1      ; IPv4-Adresse des Hosts
            IN  MX     10 mail.example.com. ; Mailserver für die Domain
            IN  NS     ns1.example.com.    ; Nameserver für die Zone
```

Auflösung von `www.example.com`:
1. Client fragt rekursiv seinen lokalen [[Nameserver]].
2. Falls nicht im Cache, leitet der Nameserver die Anfrage iterativ an Root-, TLD- und autoritative Nameserver weiter.
3. Der autoritative Nameserver für `example.com` antwortet mit der IP-Adresse.
