---
id: 920d6aed-d7bc-4207-b0a9-60622b3e775b
title: "Hard Link"
date: 2026-06-02
tags:
  - verteilte_systeme
  - benennung
  - namensraum
  - verteilte-systeme
  - dateisysteme
  - namensauflösung
  - datenstrukturen
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hard Link]]

- **Kernkonzept:** Ein [[Hard Link|Hard Link]] ist ein [[Verweis|Verweis]] in einem [[Namensraum|Namensraum]], der direkt auf eine [[Entität]] im [[Benennungsgraph|Benennungsgraphen]] zeigt. Er ermöglicht die [[Namensauflösung]] durch das Folgen eines festen [[Pfad|Pfades]] von einem [[Knoten]] zum nächsten, ohne zusätzliche [[Inhalt|Inhalte]] auslesen zu müssen.
- **Nutzen & Zweck:** Ein [[Hard Link|Hard Link]] löst das [[Problem]] der effizienten und direkten [[Adressierung]] von [[Entitäten]] in hierarchischen [[Namensräumen]]. Er ermöglicht eine schnelle [[Auflösung]] von [[Namen]] ohne zusätzliche [[Indirektion]], was die [[Performance]] und [[Konsistenz]] in [[Verteilten Systemen]] verbessert.
- **Abgrenzung & Grenzen:** Ein [[Hard Link|Hard Link]] sollte nicht genutzt werden, wenn [[Flexibilität]] bei der [[Namensauflösung]] erforderlich ist, z. B. bei [[mobilen Entitäten]] oder häufigen [[Änderungen]] der [[Adresse]]. Im Gegensatz zu [[Soft Link|Soft Links]] kann er keine [[Verweise]] auf [[Namen]] außerhalb des [[Namensgraphen]] erstellen und führt bei [[Löschung]] der [[Zielentität]] zu [[defekten Verweisen]].
- **Beispiel / Code:** In einem [[Dateisystem]] unter Unix/Linux wird ein [[Hard Link]] mit dem Befehl `ln` erstellt:
```bash
ln /pfad/zur/ursprungsdatei /pfad/zum/hardlink
```
Beide [[Pfade]] verweisen auf dieselbe [[Inode]] (Datenstruktur), sodass Änderungen an einer [[Datei]] auch in der anderen sichtbar sind. Im Gegensatz dazu würde ein [[Soft Link]] (symbolischer Link) mit `ln -s` nur den [[Pfad]] zur [[Zieldatei]] speichern.
