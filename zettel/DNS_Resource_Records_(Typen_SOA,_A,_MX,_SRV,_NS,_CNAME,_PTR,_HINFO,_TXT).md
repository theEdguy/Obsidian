---
id: 31cb4775-d1f0-42da-b335-435944f53afb
title: "DNS Resource Records (Typen: SOA, A, MX, SRV, NS, CNAME, PTR, HINFO, TXT)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - netzwerk
  - namensauflösung
  - verteilte-systeme
  - dns
  - infrastruktur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[DNS Resource Records (Typen: SOA, A, MX, SRV, NS, CNAME, PTR, HINFO, TXT)]]

- **Kernkonzept:** DNS Resource Records sind strukturierte [[Datensatz|Datensätze]], die in einem [[Namensraum|Namensraum]] wie dem [[Domain Name System|DNS]] Informationen zu [[Domäne|Domänen]] und [[Host|Hosts]] speichern. Sie definieren [[Typ|Typen]] von Einträgen, die für die [[Namensauflösung]] und [[Dienst|Dienste]]-Zuordnung essenziell sind.
- **Nutzen & Zweck:** Sie lösen das [[Problem]] der [[Skalierbarkeit]] und [[Ortsabhängigkeit]] in [[verteilten Systemen]] durch hierarchische [[Strukturierung]] von [[Name|Namen]] und [[Adresse|Adressen]]. Ohne sie wäre die effiziente [[Auflösung]] von [[Domain|Domänennamen]] zu [[IP-Adresse|IP-Adressen]] oder die [[Weiterleitung]] von [[E-Mail|E-Mails]] nicht möglich.
- **Abgrenzung & Grenzen:** DNS Resource Records sind nicht für [[attributbasierte Benennung]] geeignet, wie sie z. B. in [[LDAP]] verwendet wird. Sie eignen sich nicht für komplexe [[Abfrage|Abfragen]] nach [[Attribut|Attributen]] oder für dynamische [[Daten|Datenbestände]], die häufige Änderungen erfordern. Alternativen wie [[Verzeichnisdienst|Verzeichnisdienste]] bieten hier mehr Flexibilität, sind aber weniger effizient für einfache [[Namensauflösung|Namensauflösungen]].
- **Beispiel / Code:** ```
example.com.    IN  SOA   ns1.example.com. admin.example.com. (
                    2023100101 ; Serial
                    3600       ; Refresh
                    1800       ; Retry
                    604800     ; Expire
                    86400      ; Minimum TTL
)
example.com.    IN  A      192.0.2.1
example.com.    IN  MX     10 mail.example.com.
_ldap._tcp.example.com. IN SRV  10 60 389 ldap.example.com.
```
