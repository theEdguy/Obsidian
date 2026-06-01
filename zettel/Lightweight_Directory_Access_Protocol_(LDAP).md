---
id: d52d087a-a110-4bbc-9c32-b28e2d8c70aa
title: "Lightweight Directory Access Protocol (LDAP)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - verzeichnisdienst
  - netzwerkprotokoll
  - attributbasierte-benennung
  - hierarchische-struktur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Lightweight Directory Access Protocol (LDAP)]]

- **Kernkonzept:** LDAP ist ein [[Protokoll|Protokolle]] zur Abfrage und Verwaltung von [[Verzeichnisdienst|Verzeichnisdiensten]], das [[Attribut|Attribute]]-basierte [[Benennung|Benennungen]] in einer hierarchischen Struktur ermöglicht. Es vereinfacht das Nachschlagen von [[Entität|Entitäten]] durch eindeutige [[Namensraum|Namensräume]] und [[Attribut-Wert-Paar|Attribut-Wert-Paare]].
- **Nutzen & Zweck:** LDAP löst das [[Problem]] der skalierbaren Suche in [[Verzeichnisdienst|Verzeichnisdiensten]], indem es [[Attribut|Attribute]] effizient abfragt – ohne alle [[Entität|Entitäten]] prüfen zu müssen. Es eignet sich für [[Organisation|Organisationen]], die [[Benutzer|Benutzerdaten]], [[Ressource|Ressourcen]] oder [[Dienst|Dienste]] zentral verwalten und schnell zugänglich machen wollen.
- **Abgrenzung & Grenzen:** LDAP ist nicht für hochdynamische [[Datenbestand|Datenbestände]] oder komplexe [[Transaktion|Transaktionen]] geeignet, da es primär für Leseoperationen optimiert ist. Im Vergleich zu [[Datenbank|Datenbanken]] fehlen [[ACID-Eigenschaft|ACID-Eigenschaften]]. Alternativen wie [[DNS]] sind besser für reine [[Namensauflösung|Namensauflösungen]] geeignet, während [[SQL-Datenbank|SQL-Datenbanken]] flexiblere Abfragen ermöglichen.
- **Beispiel / Code:** Ein LDAP-Eintrag für einen Server könnte so aussehen:
```
dn: CN=Main Server,OU=Computer Science,O=VU University,C=NL
objectClass: top
objectClass: organizationalUnit
CN: Main Server
HostName: star
HostAddress: 192.31.231.42
```
Eine Abfrage für alle Server der Informatik-Fakultät:
`(OU=Computer Science)`
