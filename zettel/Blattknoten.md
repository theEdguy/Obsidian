---
id: 4fc60874-a735-4e47-8c99-0490985b9bd5
title: "Blattknoten"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensverwaltung
  - datenstruktur
  - hierarchische_benennung
  - namensauflösung
  - baumstruktur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Blattknoten]]

- **Kernkonzept:** Ein [[Blattknoten]] ist ein [[Knoten]] in einem hierarchischen [[Namensraum|Namensraum]] oder [[Baum|Baumstruktur]], der keine weiteren [[Kindknoten|Kindknoten]] besitzt und direkt eine [[Entität]] (z. B. eine Datei oder Ressource) repräsentiert. Er speichert die [[Adresse]] der [[Entität]] und bildet das Ende eines [[Pfad|Pfades]] im [[Benennungsgraph|Benennungsgraphen]].
- **Nutzen & Zweck:** Der [[Blattknoten]] ermöglicht die eindeutige Identifikation und Lokalisierung von [[Entität|Entitäten]] in verteilten Systemen durch hierarchische [[Benennung]]. Er löst das Problem der skalierbaren Organisation und Suche von Ressourcen, indem er die [[Namensauflösung]] strukturiert und effizient gestaltet. Ohne [[Blattknoten|Blattknoten]] wäre eine präzise Adressierung von Daten oder Diensten in komplexen Systemen nicht möglich.
- **Abgrenzung & Grenzen:** [[Blattknoten]] sollten nicht genutzt werden, wenn flache oder nicht-hierarchische [[Benennung|Benennungsstrukturen]] ausreichen (z. B. einfache Schlüssel-Wert-Speicher). Im Gegensatz zu [[Verzeichnisknoten|Verzeichnisknoten]] enthalten sie keine Verweise auf weitere [[Knoten]], sondern nur die eigentlichen Daten oder [[Adresse|Adressen]]. Für dynamische Systeme mit häufigen Änderungen können sie ineffizient sein, da die [[Namensauflösung]] über mehrere Ebenen erfolgen muss.
- **Beispiel / Code:** In einem hierarchischen Dateisystem wie Unix repräsentiert der Pfad `/home/steen/keys` einen [[Blattknoten]] (hier: die Datei `keys`). Der [[Benennungsgraph]] sieht vereinfacht so aus:
```
/home (Verzeichnisknoten)
└── steen (Verzeichnisknoten)
    └── keys (Blattknoten, enthält die Dateidaten oder deren Adresse)
```
Im DNS-System ist ein [[Blattknoten]] z. B. der Eintrag für `ftp.cs.vu.nl`, der die IP-Adresse des FTP-Servers speichert.
