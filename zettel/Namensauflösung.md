---
id: 841b848c-619e-4931-ae53-81a6b887cd7d
title: "Namensauflösung"
date: 2026-06-02
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - netzwerk
  - namensdienst
  - skalierbarkeit
  - adressierung
  - koordination
  - namensraum
  - namenssysteme
  - dns
  - ldap
  - hierarchie
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Namensauflösung]]

- **Kernkonzept:** Die [[Namensauflösung]] ist der Prozess, bei dem ein [[Bezeichner]] (z. B. ein [[Name|Namen]]) einer [[Entität]] in eine technische [[Adresse]] oder einen [[Standort]] überführt wird, um den [[Zugriffspunkt]] der [[Entität]] in einem [[Verteiltes_System|verteilten System]] zu lokalisieren und die [[Kommunikation]] sowie [[Zugriff|Zugriffe]] zu ermöglichen. Sie trennt benutzerfreundliche [[Bezeichner|Bezeichner]] von technischen [[Adresse|Adressen]] und ist essenziell für die [[Skalierbarkeit]], [[Flexibilität]] und [[Ortsunabhängigkeit]] solcher Systeme, indem sie [[Struktur|strukturierte]] oder attributbasierte [[Zuordnung|Zuordnungen]] von [[Name|Namen]] zu [[Ressource|Ressourcen]] ermöglicht.
- **Nutzen & Zweck:** Die [[Namensauflösung]] löst das [[Problem]] der eindeutigen [[Identifikation]] und [[Lokalisierung]] von [[Entität|Entitäten]] in großen, heterogenen [[Netzwerk|Netzwerken]], indem sie [[Benutzer|Benutzern]] und [[System|Systemen]] die Verwaltung technischer [[Adresse|Adressen]] abnimmt. Ohne sie wäre die direkte [[Adressierung]] von [[Knoten]] über physische [[Adresse|Adressen]] in dynamischen Umgebungen unpraktikabel und fehleranfällig. Sie fördert die [[Abstraktion]] technischer Details, unterstützt die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] und erhöht die [[Wartbarkeit]] durch zentrale Verwaltung von [[Adresse|Adressen]] über [[Namensdienst|Namensdienste]]. Zudem ermöglicht sie [[Skalierbarkeit]] in globalen Systemen durch [[Hierarchische_Ansätze|hierarchische Ansätze]] wie das [[DNS]] und vereinfacht die [[Integration]] heterogener [[Ressource|Ressourcen]] durch attributbasierte [[Suche|Suchanfragen]].
- **Abgrenzung & Grenzen:** Die [[Namensauflösung]] stößt an Grenzen in Systemen mit extrem hoher [[Änderungsrate|Änderungsfrequenz]] von [[Adresse|Adressen]], da die [[Aktualisierung]] der [[Namensraum|Namensräume]] zu [[Latenz|Latenzen]] oder [[Konsistenzproblem|Konsistenzproblemen]] führen kann. In solchen Fällen sind Alternativen wie [[Broadcasting]] oder [[Verteilte_Hash-Tabelle|verteilte Hash-Tabellen]] (DHTs) effizienter, skalieren jedoch schlechter für große [[Netzwerk|Netzwerke]]. [[Hierarchische_Ansätze|Hierarchische Ansätze]] (z. B. [[DNS]]) sind besser für globale Systeme geeignet, erfordern jedoch einen [[Closure-Mechanismus]], der in dezentralen Umgebungen schwer umsetzbar ist. Für [[Flache_Benennung|flache Benennungsmodelle]] in kleinen, stabilen [[Netzwerk|Netzwerken]] ist direkte [[Adressierung]] oder [[Broadcasting]] oft ausreichend. Attributbasierte [[Suche|Suchanfragen]] (z. B. in [[Verzeichnisdienst|Verzeichnisdiensten]] wie [[LDAP]]) können ineffizient sein, wenn keine [[Indexierung]] vorliegt oder die [[Attribut|Attribute]] dynamisch und komplex sind. Zudem erfordert die [[Namensauflösung]] eine [[Infrastruktur]] (z. B. [[Datenbank|Datenbanken]] oder [[Hierarchie|Hierarchien]]), die in einfachen oder hochdynamischen Systemen überdimensioniert sein kann.
- **Beispiel / Code:** ### Beispiel 1: Einfache [[Namensauflösung]] mittels Tabelle
```
Namensdienst-Tabelle:
| Bezeichner (Name)       | Adresse (IP:Port)   |
|-------------------------|---------------------|
| "DatenbankServer"      | 192.168.1.10:5432   |
| "WebService"           | 10.0.0.5:8080       |
```
Ein [[Client]] fragt den [[Namensdienst]] nach dem [[Bezeichner]] "DatenbankServer" und erhält die [[Adresse]] `192.168.1.10:5432`.

### Beispiel 2: Hierarchische [[Namensauflösung]] im [[DNS]]
**Rekursive Auflösung:**
```
1. Ein [[Client]] sendet eine Anfrage für `www.example.com` an einen lokalen [[DNS-Server]].
2. Der [[DNS-Server]] löst den [[Name|Namen]] rekursiv auf:
   - Anfrage an einen [[Root-Nameserver]] für `.com`.
   - Weiterleitung an den [[Nameserver]] für `example.com`.
   - Rückgabe der [[IP-Adresse]] `93.184.216.34` an den [[Client]].
```

**Iterative Auflösung:**
Der [[Client]] führt jeden Schritt selbst durch und kontaktiert nacheinander die [[Nameserver|Nameserver]] für `.com` und `example.com`.

### Beispiel 3: Attributbasierte [[Suche]] mit [[LDAP]]
```
LDAP-Suchanfrage:
search("(C=NL)(O=VU University)(OU=Computer Science)(CN=Main server)")
```
Ergebnis: Ein [[Eintrag]] mit [[Attribut|Attributen]] wie `HostName=star` und `HostAddress=192.31.231.42`.
