---
id: 07d6645c-3cbb-4316-8824-9f350ecb15db
title: "HLS: Einfügen"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensauflösung
  - hierarchische_benennung
  - baumstruktur
  - adressierung
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[HLS: Einfügen]]

- **Kernkonzept:** Das [[Konzept|Konzept]] des Einfügens in [[Hierarchisches Lineares System|HLS]] beschreibt, wie eine [[Entität|Entität]] in einen [[Baum|Baum]]-basierten [[Namensraum|Namensraum]] integriert wird, indem eine [[Kette|Kette]] von [[Weiterleitungen|Weiterleitungen]] bis zum passenden [[Blattknoten|Blattknoten]] erzeugt wird.
- **Nutzen & Zweck:** Es löst das [[Problem|Problem]] der dynamischen Erweiterung eines hierarchischen [[Adressierungssystems|Adressierungssystems]], indem es [[Einträge|Einträge]] für neue [[Entitäten|Entitäten]] effizient in die bestehende [[Struktur|Struktur]] einfügt und dabei die [[Invarianten|Invarianten]] des [[Baums|Baums]] (z. B. Wurzelkenntnis aller [[Entitäten|Entitäten]]) erhält.
- **Abgrenzung & Grenzen:** Nicht geeignet für flache [[Benennungssysteme|Benennungssysteme]], da diese keine hierarchische [[Organisation|Organisation]] voraussetzen. Im Vergleich zu [[DNS|DNS]]-basierten Systemen fehlt hier die [[Verteilung|Verteilung]] auf mehrere [[Server|Server]]-Ebenen. Alternativen wie [[Hash-Tabellen|Hash-Tabellen]] bieten schnellere [[Suche|Suchoperationen]], aber keine hierarchische [[Strukturierung|Strukturierung]].
- **Beispiel / Code:** 1. Einfügeanfrage für Entität E wird an einen [[Knoten|Knoten]] M gesendet.
2. M kennt E nicht → Anfrage wird an [[Elternknoten|Elternknoten]] weitergeleitet.
3. Ein [[Knoten|Knoten]] N kennt E → erzeugt [[Standorteintrag|Standorteintrag]] und speichert die [[Adresse|Adresse]] von E.
4. Falls N kein [[Blattknoten|Blattknoten]] ist, wird ein [[Zeiger|Zeiger]] auf den [[Kindknoten|Kindknoten]] erzeugt, der E enthält.

Beispiel: Einfügen von "/home/max/keys" in einen [[Namensbaum|Namensbaum]]:
- Anfrage startet bei Wurzel → weiter zu "/home" → weiter zu "/home/max" → Eintrag für "/keys" wird im [[Blattknoten|Blattknoten]] "/home/max" gespeichert.
