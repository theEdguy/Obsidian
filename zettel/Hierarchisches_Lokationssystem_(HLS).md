---
id: 9b140590-aaab-48ed-837d-451a6e86c78d
title: "Hierarchisches Lokationssystem (HLS)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - lokationsmanagement
  - namensauflösung
  - baumstruktur
  - netzwerkarchitektur
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hierarchisches Lokationssystem (HLS)]]

- **Kernkonzept:** Das Hierarchische Lokationssystem (HLS) ist ein [[Baum|baumartiger]] [[Ansatz|Ansatz]] zur [[Organisation|Organisation]] von [[Adresse|Adressen]] in [[Verteilte Systeme|verteilten Systemen]], bei dem [[Entität|Entitäten]] in [[Blattknoten]] gespeichert werden und [[Zwischenknoten]] [[Zeiger]] auf [[Kindknoten]] enthalten, die relevante [[Adresse|Adressen]] verwalten.
- **Nutzen & Zweck:** HLS löst das [[Problem]] der [[Skalierbarkeit|skalierbaren]] und [[Effizienz|effizienten]] [[Lokation|Lokation]] von [[Entität|Entitäten]] in großen [[Verteilte Systeme|verteilten Systemen]]. Es ermöglicht eine strukturierte [[Suche]], [[Einfügen|Einfügung]] und [[Verwaltung]] von [[Adresse|Adressen]] durch hierarchische [[Organisation]], wodurch die [[Komplexität]] der [[Namensauflösung]] reduziert wird.
- **Abgrenzung & Grenzen:** HLS ist nicht geeignet für [[Systeme]], die eine flache oder hochdynamische [[Adressierung]] erfordern, da die hierarchische [[Struktur]] zu [[Overhead]] bei häufigen [[Änderung|Änderungen]] führen kann. Im Vergleich zu [[Lineare Benennung|linearen Benennungssystemen]] oder [[Verteilte Hash-Tabellen|DHTs]] ist HLS weniger flexibel, aber besser für [[Systeme]] mit stabilen [[Hierarchie|Hierarchien]] und klaren [[Domäne|Domänengrenzen]] geeignet.
- **Beispiel / Code:** ```
// Beispiel: Suche nach einer Entität E im HLS
function sucheEntitaet(knoten, E) {
    if (knoten.kenntEntitaet(E)) {
        // Folge Zeiger abwärts zum Blattknoten
        return folgeZeiger(knoten, E);
    } else if (knoten.istWurzel()) {
        return null; // Entität nicht gefunden
    } else {
        // Gehe zum Elternknoten
        return sucheEntitaet(knoten.elternKnoten, E);
    }
}
```
