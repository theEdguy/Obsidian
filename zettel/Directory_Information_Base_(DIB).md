---
id: 8d0206cc-cdd3-4634-861d-90643068f5b2
title: "Directory Information Base (DIB)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verzeichnisdienst
  - ldap
  - attributbasierte_benennung
  - skalierbarkeit
  - hierarchische_datenstruktur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Directory Information Base (DIB)]]

- **Kernkonzept:** Die [[Directory Information Base|Directory Information Base (DIB)]] ist eine strukturierte Sammlung von [[Verzeichniseintrag|Verzeichniseinträgen]] in [[Verzeichnisdienst|Verzeichnisdiensten]] wie LDAP, die [[Attribut|Attribute]] und [[Wert|Werte]] von [[Entität|Entitäten]] hierarchisch organisiert und durchsuchbar macht.
- **Nutzen & Zweck:** Die DIB löst das Problem der effizienten [[Abfrage|Abfragen]] und Verwaltung von [[Entität|Entitäten]] anhand ihrer [[Attribut|Attribute]] in großen, verteilten Systemen. Sie ermöglicht skalierbare [[Suche|Suchoperationen]] ohne vollständige Durchmusterung aller [[Eintrag|Einträge]], indem sie eine hierarchische [[Struktur|Strukturierung]] (z. B. als [[Directory Information Tree|Directory Information Tree]]) nutzt.
- **Abgrenzung & Grenzen:** Die DIB eignet sich nicht für unstrukturierte oder hochdynamische [[Datenbestand|Datenbestände]], bei denen [[Attribut|Attribute]] häufig wechseln oder keine klare Hierarchie vorliegt. Im Vergleich zu [[relationalen Datenbank|relationalen Datenbanken]] fehlen komplexe [[Transaktion|Transaktionsmechanismen]] oder [[Joins|Join-Operationen]]. Alternativen wie [[DNS]] sind für reine [[Namensauflösung|Namensauflösungen]] optimiert, während die DIB attributbasierte [[Abfrage|Abfragen]] priorisiert.
- **Beispiel / Code:** Ein LDAP-Eintrag in der DIB könnte wie folgt strukturiert sein:
```
dn: CN=Main Server,OU=Computer Science,O=VU University,C=NL
objectClass: top
objectClass: organizationalUnit
CN: Main Server
HostName: star
HostAddress: 192.31.231.42
```
Eine Abfrage nach allen Servern der [[Organisationseinheit|Organisationseinheit]] 'Computer Science' würde lauten:
```
search("(C=NL)(O=VU University)(OU=Computer Science)")
```
