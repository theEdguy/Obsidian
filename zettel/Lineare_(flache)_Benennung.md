---
id: b43e09ed-99f3-42ab-95e8-4e27e5fa0dbf
title: "Lineare (flache) Benennung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - adressierung
  - namensraum
  - datenstruktur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Lineare (flache) Benennung]]

- **Kernkonzept:** Die lineare (flache) Benennung ist ein [[Benennungssystem|Benennungssystem]], das [[Entität|Entitäten]] in einem [[Verteilte Systeme|verteilten System]] durch eindeutige, nicht-hierarchische [[Adresse|Adressen]] identifiziert. Im Gegensatz zu hierarchischen Ansätzen werden [[Knoten|Knoten]] in einer flachen Struktur organisiert, wobei die [[Wurzel]] alle [[Entität|Entitäten]] kennt.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der einfachen und direkten [[Adressierung]] von [[Entität|Entitäten]] in [[Verteilte Systeme|verteilten Systemen]], ohne komplexe [[Namensauflösung]] oder hierarchische Pfade. Es ermöglicht schnelle [[Suche]] und [[Einfügen|Einfügeoperationen]] durch direkte Zeiger auf [[Knoten]].
- **Abgrenzung & Grenzen:** Lineare (flache) Benennung eignet sich nicht für große oder dynamische Systeme, da die [[Wurzel]] zum [[Flaschenhals]] werden kann. Im Vergleich zu [[Hierarchische Benennung|hierarchischen Benennungssystemen]] fehlt die Skalierbarkeit und Flexibilität bei der Verwaltung von [[Namensraum|Namensräumen]]. Alternativen wie [[DNS]] oder [[Verzeichnisdienst|Verzeichnisdienste]] sind besser für komplexe Strukturen geeignet.
- **Beispiel / Code:** Ein einfaches Beispiel für lineare Benennung:

- **Struktur**: Jeder [[Knoten]] enthält einen [[Standorteintrag]] mit einer [[Adresse]].
- **Suche**: Beginne bei einem lokalen [[Blattknoten]]. Kenne der [[Knoten]] die [[Entität]] nicht, gehe zum [[Elternknoten]] aufwärts bis zur [[Wurzel]].
- **Einfügen**: Leite die Anfrage zum ersten [[Knoten]], der die [[Entität]] kennt, und speichere die [[Adresse]] im [[Blattknoten]].

Beispiel-Darstellung:
```
Domäne D1: [Knoten M → Adresse von E]
Domäne D2: [Knoten N → Zeiger auf M]
```
