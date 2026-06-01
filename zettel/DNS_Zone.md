---
id: 00c71066-fd2d-4bdd-9432-69276b41d45e
title: "DNS Zone"
date: 2026-06-02
tags:
  - verteilte_systeme
  - netzwerk
  - namensauflösung
  - verteilte-systeme
  - dns
  - administration
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[DNS Zone]]

- **Kernkonzept:** Eine [[DNS Zone|DNS-Zone]] ist ein administrativer Bereich innerhalb des [[Domain Name System|DNS]], der einen Teil des hierarchischen [[Namensraum|Namensraums]] verwaltet und die [[Auflösung|Auflösungen]] von [[Domain|Domains]] zu [[IP-Adresse|IP-Adressen]] ermöglicht.
- **Nutzen & Zweck:** Sie löst das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] in [[verteilte Systeme|verteilten Systemen]], indem sie die [[Namensauflösung]] dezentral und effizient organisiert. Dadurch wird die [[Lastverteilung]] verbessert und die [[Ausfallsicherheit]] erhöht.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[attributbasierte Benennung|attributbasierte Abfragen]], da [[DNS]] auf hierarchische [[Struktur]]en ausgelegt ist. Alternativen wie [[LDAP]] oder [[Verzeichnisdienst|Verzeichnisdienste]] eignen sich besser für komplexe [[Attribut|Attribut]]-basierte [[Suche|Suchanfragen]].
- **Beispiel / Code:** ```
$ORIGIN example.com.
@       IN  SOA   ns1.example.com. admin.example.com. (
                  2023100101 ; Serial
                  3600       ; Refresh
                  1800       ; Retry
                  604800     ; Expire
                  86400      ; Minimum TTL
)
        IN  NS    ns1.example.com.
        IN  NS    ns2.example.com.
ns1     IN  A     192.0.2.1
ns2     IN  A     192.0.2.2
www     IN  A     192.0.2.10
```
