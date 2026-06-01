---
id: 5a6fc219-22e1-4c80-ae8d-36e83559b26e
title: "Attributbasierte Benennung"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensdienste
  - ldap
  - attributbasierte_suche
  - skalierbarkeit
  - verzeichnisdienste
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Attributbasierte Benennung]]

- **Kernkonzept:** Attributbasierte Benennung ermöglicht das Auffinden von [[Entität|Entitäten]] in [[Verteilte Systeme|verteilten Systemen]] durch Abfrage ihrer [[Attribut|Attribute]] statt fester [[Name|Namen]] oder [[Pfad|Pfade]]. Sie nutzt [[Verzeichnisdienst|Verzeichnisdienste]] wie LDAP, um [[Objekt|Objekte]] anhand von [[Eigenschaft|Eigenschaften]] zu identifizieren.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der inflexiblen [[Namensauflösung]] in [[Hierarchische Benennung|hierarchischen Systemen]] wie DNS. Es erlaubt [[Suche|Suchanfragen]] nach dynamischen Kriterien (z. B. "alle Server in Amsterdam mit FTP-Dienst") und reduziert die Abhängigkeit von starren [[Struktur|Strukturen]]. Besonders nützlich für [[Skalierbarkeit|skalierbare]] und [[Dynamik|dynamische]] Umgebungen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Eindeutigkeit]] oder [[Performance]] kritisch sind: Attributbasierte [[Abfrage|Abfragen]] können [[Kosten|kostenintensiv]] sein, da sie potenziell alle [[Eintrag|Einträge]] prüfen müssen. Im Gegensatz zu [[Hierarchische Benennung|hierarchischen Systemen]] (z. B. DNS) fehlt eine feste [[Ordnung]], was bei einfachen [[Zugriff|Zugriffen]] ineffizient sein kann. Alternativen wie [[DHT|verteilte Hash-Tabellen]] bieten oft schnellere [[Auflösung]] für bekannte [[Schlüssel|Schlüssel]].
- **Beispiel / Code:** LDAP-Suchanfrage nach Servern der VU University in den Niederlanden:
```
search("(C=NL)(O=VU University)(OU=Computer Science)(CN=Main server)")
```
Ergebnis: Ein [[Eintrag]] mit Attributen wie `HostName=star` und `HostAddress=192.31.231.42`. Jeder [[Knoten]] im [[Directory Information Tree]] repräsentiert ein [[Objekt]] mit (Attribut, Wert)-Paaren, z. B. `(Locality=Amsterdam, Organization=VU University)`.
