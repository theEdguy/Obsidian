---
id: 00ee94f2-883c-4740-a067-b5946dee2cc0
title: "Iterative und rekursive Namensauflösung"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensauflösung
  - dns
  - hierarchische-benennung
  - netzwerk-architektur
  - skalierbarkeit
  - caching
  - hierarchische-strukturen
  - netzwerkprotokolle
  - client-server-architektur
  - netzwerk
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Iterative und rekursive Namensauflösung]]

- **Kernkonzept:** Die [[iterative Namensauflösung|iterative]] und [[rekursive Namensauflösung|rekursive Namensauflösung]] sind zwei grundlegende [[Verfahren]] zur Auflösung von [[Pfadname|Pfadnamen]] in [[hierarchischen Benennung|hierarchischen Benennungssystemen]] wie dem [[Domain Name System (DNS)|DNS]]. Bei der iterativen [[Namensauflösung]] steuert der [[Client]] den Prozess, indem er schrittweise [[Anfrage|Anfragen]] an verschiedene [[Nameserver]] stellt, während bei der rekursiven [[Namensauflösung]] ein [[Nameserver]] die vollständige Auflösung übernimmt und das Ergebnis an den [[Client]] zurückgibt. Die iterative Methode reduziert die [[Last]] auf den [[Nameserver|Nameservern]], während die rekursive Methode die [[Latenz]] für den [[Client]] verringert und durch [[Caching]] die Effizienz steigert.
- **Nutzen & Zweck:** Beide [[Verfahren]] adressieren das [[Skalierbarkeitsproblem]] in [[verteilten Systemen|verteilten Systemen]] durch Lastverteilung auf mehrere [[Nameserver]]. Die iterative [[Namensauflösung]] bietet dem [[Client]] mehr Kontrolle, reduziert die [[Last]] auf den [[Nameserver|Nameservern]] und vermeidet [[Langstreckenkommunikation|Langstreckenkommunikationen]] durch schrittweise Abfrage lokaler [[Nameserver]]. Dies macht sie besonders effizient für große geographische [[Distanz|Distanzen]] und [[Namensraum|Namensräume]] wie das [[DNS]] oder [[Verzeichnisdienst|Verzeichnisdienste]] wie [[LDAP]]. Die rekursive [[Namensauflösung]] hingegen verringert die [[Latenz]] für den [[Client]], da sie die Komplexität der Auflösung an spezialisierte [[Nameserver]] delegiert. Durch [[Caching]] von Zwischenergebnissen wird die Effizienz weiter gesteigert, was sie ideal für [[Client|Clients]] mit begrenzten Ressourcen oder in Umgebungen mit hohen Anforderungen an die Antwortzeit macht. Beide Ansätze sind essenziell, um [[Skalierbarkeit]] und [[Verfügbarkeit]] in großen [[Namensraum|Namensräumen]] zu gewährleisten.
- **Abgrenzung & Grenzen:** Die iterative [[Namensauflösung]] ist weniger geeignet, wenn [[Latenz]] oder [[Netzwerkauslastung]] kritisch sind, da sie mehrere [[Rundreise|Rundreisen]] zwischen [[Client]] und [[Nameserver|Nameservern]] erfordert und zu erhöhtem [[Netzwerkverkehr]] führen kann. Im Gegensatz zur rekursiven Methode übernimmt der [[Client]] hier die Koordination, was zwar die [[Last]] auf den [[Nameserver|Nameservern]] verringert, aber die Komplexität auf [[Client]]-Seite erhöht. Für einfache oder lokale [[Namensraum|Namensräume]] kann die iterative Methode unnötig aufwendig sein. Die rekursive [[Namensauflösung]] belastet hingegen die [[Nameserver]] stärker, insbesondere bei häufigen Änderungen in der [[Namensstruktur]], da [[Caching]] zu [[Inkonsistenz|Inkonsistenzen]] führen kann. Für [[mobilen Entitäten|mobile Entitäten]] oder stark dynamische [[Namensraum|Namensräume]] sind beide [[Verfahren]] nur bedingt geeignet. Während die rekursive Methode durch [[Caching]]-Mechanismen besser skaliert, ist sie anfälliger für veraltete [[Daten]]. In lokalen oder einfachen [[Namensraum|Namensräumen]] kann die iterative [[Namensauflösung]] effizienter sein, da sie keine zusätzliche [[Serverlast]] verursacht.
- **Beispiel / Code:** ### Iterative Namensauflösung (Beispiel für Pfadnamen `[nl, vu, cs, ftp]`):
```
1. Client sendet resolve([nl, vu, cs, ftp]) an Root-Nameserver.
2. Root-Nameserver gibt Adresse des nl-Nameservers zurück.
3. Client sendet resolve([vu, cs, ftp]) an nl-Nameserver.
4. nl-Nameserver gibt Adresse des vu-Nameservers zurück.
5. Client sendet resolve([cs, ftp]) an vu-Nameserver.
6. vu-Nameserver gibt Adresse des cs-Nameservers zurück.
7. Client sendet resolve([ftp]) an cs-Nameserver.
8. cs-Nameserver gibt finale Adresse des ftp-Knotens zurück.
```

### Iterative Namensauflösung im [[DNS]]-Kontext (Beispiel für `example.com`):
```
1. Client fragt lokalen Nameserver nach der Adresse von 'example.com'.
2. Lokaler Nameserver kennt die Adresse nicht und verweist auf einen Root-Nameserver.
3. Client fragt Root-Nameserver, der auf den Nameserver für '.com' verweist.
4. Client fragt Nameserver für '.com', der auf den Nameserver von 'example.com' verweist.
5. Client fragt Nameserver von 'example.com' und erhält die IP-Adresse.
```

### Rekursive Namensauflösung (Beispiel für Pfadnamen `[nl, vu, cs, ftp]` im [[DNS]]-Kontext):
```
1. Client sendet Anfrage an lokalen Nameserver (z. B. resolve(www.example.com)).
2. Lokaler Nameserver leitet Anfrage an Root-Nameserver weiter.
3. Root-Nameserver verweist auf den [[Top-Level-Domain-Nameserver]] (z. B. `.com`).
4. Top-Level-Domain-Nameserver verweist auf den autoritativen Nameserver für `example.com`.
5. Autoritativer Nameserver liefert die [[IP-Adresse]] zurück.
6. Ergebnis wird schrittweise über die Serverkette an den Client zurückgegeben.
```

**Hinweis zu [[Caching]]:** Jeder [[Nameserver]] speichert Zwischenergebnisse (z. B. [[IP-Adresse|IP-Adressen]] von `cs` oder `vu,cs,ftp`), um zukünftige [[Anfrage|Anfragen]] zu beschleunigen und die [[Last]] auf den [[Nameserver|Nameservern]] zu reduzieren.
