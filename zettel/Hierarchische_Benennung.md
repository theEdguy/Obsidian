---
id: f2bf508d-8ba6-4dcd-b0eb-8cce3dd96162
title: "Hierarchische Benennung"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensauflösung
  - netzwerk
  - architektur
  - skalierbarkeit
  - dns
  - benennungssysteme
  - namensverwaltung
  - hierarchie
  - koordination
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hierarchische Benennung]]

- **Kernkonzept:** Die hierarchische Benennung ist ein [[Benennungssystem|Benennungssystem]], das [[Entität|Entitäten]] in einer [[Baumstruktur|Baumstruktur]] organisiert, um [[Adresse|Adressen]] und [[Standort|Standorte]] effizient zu verwalten und aufzulösen. Sie ermöglicht die Abbildung von [[Namensraum|Namensräumen]] durch [[Verzeichnisknoten|Verzeichnisknoten]] und [[Blattknoten|Blattknoten]] und unterstützt eine skalierbare [[Adressierung|Adressierung]] durch rekursive oder iterative [[Namensauflösung|Namensauflösungen]].
- **Nutzen & Zweck:** Dieses Konzept löst das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] in großen, geografisch verteilten [[System|Systemen]], indem es die [[Komplexität]] der [[Namensverwaltung]] reduziert und die [[Latenz]] bei der [[Suche]] minimiert. Es schafft eine klare [[Struktur]] für die [[Zuordnung]] von [[Ressource|Ressourcen]] zu [[Adresse|Adressen]], vermeidet [[Kollision|Kollisionen]] durch eindeutige [[Pfadangabe|Pfadangaben]] und ermöglicht die [[Verteilung]] von [[Namensraum|Namensräumen]] auf mehrere [[Server|Server]], um [[Skalierbarkeit]] und [[Verfügbarkeit]] zu gewährleisten.
- **Abgrenzung & Grenzen:** Hierarchische Benennung eignet sich nicht für flache oder dynamisch veränderliche [[Struktur|Strukturen]], da der [[Overhead]] für die Verwaltung der [[Baumstruktur|Baumstruktur]] zu hoch wird. Alternativen wie lineare (flache) Benennung oder dezentrale [[Hash-Tabelle|Hash-Tabellen]] (z. B. [[Verteilte_Hash-Tabelle|DHTs]]) sind in solchen Fällen effizienter. Zudem ist sie weniger geeignet für [[System|Systeme]], in denen [[Entität|Entitäten]] dynamisch oder attributbasiert gesucht werden müssen, da sie keine flexible [[Abfrage]] nach [[Eigenschaft|Eigenschaften]] unterstützt. Hier sind [[attributbasierte Benennung|attributbasierte Benennungssysteme]] (z. B. [[Lightweight_Directory_Access_Protocol|LDAP]]) vorzuziehen. Die hierarchische Benennung ist außerdem anfällig für [[Engpass|Engpässe]] bei häufigen [[Änderung|Änderungen]] in oberen Ebenen des [[Baum|Baums]] und kann bei globaler Verteilung zu [[Performance|Performanceproblemen]] führen, wenn die [[Hierarchie]] nicht optimal designed ist.
- **Beispiel / Code:** Ein klassisches Beispiel für hierarchische Benennung ist das [[Domain_Name_System|Domain Name System (DNS)]], das [[Namensraum|Namensräume]] in einer Baumstruktur organisiert:

```
example.com.       IN  SOA   ns1.example.com. admin.example.com. (
                          2023080101 ; Serial
                          3600       ; Refresh
                          1800       ; Retry
                          604800     ; Expire
                          86400 )    ; Minimum TTL

; Nameserver-Einträge
example.com.       IN  NS    ns1.example.com.
example.com.       IN  NS    ns2.example.com.

; A-Einträge für Hosts
ns1.example.com.   IN  A     192.0.2.1
ns2.example.com.   IN  A     192.0.2.2
www.example.com.   IN  A     192.0.2.10
```

Der [[Namensraum]] ist in eine Baumstruktur unterteilt (z. B. `www.example.com`), wobei jeder Knoten (z. B. `com`, `example`, `www`) einen [[Verzeichnisknoten|Verzeichnisknoten]] oder [[Blattknoten|Blattknoten]] repräsentiert. Die [[Namensauflösung]] erfolgt durch iterative oder rekursive Abfrage von [[Nameserver|Nameservern]], beginnend bei der Wurzel. Ein einfacher DNS-Eintrag zur Abbildung eines [[Pfadname|Pfadnamens]] auf eine [[IP-Adresse]] sieht wie folgt aus:

```
example.com.    IN    A    192.0.2.1
```
