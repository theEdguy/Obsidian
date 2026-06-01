---
id: e885839c-3038-4444-9b12-5656823c38a0
title: "Namensräume"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - benennung
  - namensauflösung
  - hierarchische-strukturen
  - skalierbarkeit
  - netzwerk
  - dns
  - graphentheorie
  - ldap
  - hierarchie
  - attributbasiert
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Namensräume]]

- **Kernkonzept:** Ein [[Namensraum]] ist eine strukturierte [[Hierarchie]] oder [[Graph|graphenbasierte Struktur]] zur Organisation und eindeutigen [[Benennung|Benennung]] von [[Entität|Entitäten]] in [[Verteilte Systeme|verteilten Systemen]], die die [[Auflösung|Auflösung]] von [[Name|Namen]] zu [[Adresse|Adressen]] oder [[Ressource|Ressourcen]] ermöglicht. Er kann hierarchisch (z. B. [[Domain Name System|DNS]]) oder attributbasiert (z. B. [[Lightweight Directory Access Protocol|LDAP]]) implementiert sein und unterstützt Mechanismen wie [[Replikation]] oder [[Caching]] zur Verbesserung der [[Skalierbarkeit]] und [[Performance]].
- **Nutzen & Zweck:** [[Namensräume]] lösen das Problem der eindeutigen und skalierbaren [[Benennung|Benennung]] von [[Entität|Entitäten]] in großen, [[Verteilte Systeme|verteilten Systemen]], indem sie [[Name|Namen]] global eindeutig und ortsunabhängig machen. Sie ermöglichen eine strukturierte [[Namensauflösung]], vereinfachen die Verwaltung von [[Ressource|Ressourcen]] und unterstützen die effiziente [[Auflösung]] über große Distanzen. Zudem fördern sie [[Skalierbarkeit]] durch Mechanismen wie [[Partitionierung]], [[Replikation]] und [[Caching]], was die [[Performance]] und [[Verfügbarkeit]] in [[Netzwerk|Netzwerken]] verbessert.
- **Abgrenzung & Grenzen:** [[Namensräume]] sind ungeeignet für einfache Systeme mit flachen [[Adressraum|Adressräumen]], da der Overhead der [[Hierarchie]] oder komplexen [[Attribut|Attributsuche]] unnötig ist. Alternativen wie lineare [[Benennung]] (z. B. einfache [[Tabelle|Tabellen]]) sind effizienter, wenn keine komplexen [[Pfad|Pfade]] oder [[Verzeichnis|Verzeichnisstrukturen]] benötigt werden. Hierarchische [[Namensräume]] erfordern zudem einen [[Closure-Mechanismus]] zur Initialisierung der [[Namensauflösung]], was zusätzliche Komplexität mit sich bringt. Attributbasierte Systeme (z. B. [[Lightweight Directory Access Protocol|LDAP]]) sind ineffizient für einfache [[Namensauflösung|Namensauflösungen]], da sie komplexe [[Suche|Suchoperationen]] erfordern, während hierarchische Systeme (z. B. [[Domain Name System|DNS]]) für unstrukturierte oder dynamische [[Abfrage|Abfragen]] nach [[Attribut|Attributen]] ungeeignet sind.
- **Beispiel / Code:** ### Hierarchische Auflösung im [[Domain Name System|DNS]]:
```
// Beispiel: Auflösung des Pfadnamens 'www.example.com'
1. Client fragt rekursiv/iterativ Nameserver:
   - Root-Nameserver verweist auf '.com'-Nameserver.
   - '.com'-Nameserver verweist auf 'example.com'-Nameserver.
   - 'example.com'-Nameserver liefert IP-Adresse (z. B. 93.184.216.34).
```

### Attributbasierte Suche in [[Lightweight Directory Access Protocol|LDAP]]:
```
// Beispiel: Suche nach einem Server mit spezifischen Attributen
LDAP-Abfrage:
(&(C=NL)(O=VU University)(OU=*)(CN=Main server))
// Ergebnis: Liste von Einträgen mit passenden Attributen.
```

### Verzeichnisstruktur in einem hierarchischen [[Namensraum]]:
```
// Pfadname: /home/steen/keys
// Auflösungsschritte:
1. Starte bei der Wurzel (z. B. lokaler Verzeichnisknoten).
2. Folge dem Pfad: Wurzel → 'home' → 'steen' → 'keys'.
3. Der Blattknoten 'keys' enthält die Adresse der Ressource.

// Verzeichnisknoten 'steen' könnte folgende Tabelle enthalten:
{
  "keys": Zeiger_auf_Knoten_n5,
  "mbox": Zeiger_auf_Knoten_mbox
}
```
