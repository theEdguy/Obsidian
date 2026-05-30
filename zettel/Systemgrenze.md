---
id: 14027fc8-d73b-4a0c-9223-216be421443e
title: "Systemgrenze"
date: 2026-05-30
tags:
  - software_engineering
  - systemdesign
  - analyse
  - anforderungsanalyse
  - architektur
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Systemgrenze]]

- **Kernkonzept:** Die [[Systemgrenze]] definiert die [[Abgrenzung]] zwischen einem [[Softwaresystem]] und seiner [[Umgebung]], also [[Akteur|Akteuren]] oder [[Fremdsystem|Fremdsystemen]]. Sie legt fest, welche [[Funktionalität|Funktionalitäten]] innerhalb des Systems liegen und welche externen [[Akteur|Akteure]] oder Systeme mit dem System interagieren. In [[Use-Case-Diagramm|Use-Case-Diagrammen]] wird sie als Rechteck dargestellt.
- **Nutzen & Zweck:** Die [[Systemgrenze]] klärt den [[Scope]] eines Projekts und verhindert [[Scope_Creep]]. Sie ist essenziell für die [[Use-Case-Analyse]], die Identifikation von [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Schnittstelle|Schnittstellen]] sowie für [[Architekturentscheidung|Architekturentscheidungen]]. Ohne sie entstehen [[Missverständnis|Missverständnisse]] über den Umfang des Systems, was zu unklaren [[Anforderung|Anforderungen]] und fehlerhaften [[Implementierung|Implementierungen]] führen kann.
- **Abgrenzung & Grenzen:** Die [[Systemgrenze]] ist eine [[konzeptionelle_Grenze]] und keine [[technische_Grenze]] wie die [[Netzwerkgrenze]]. Sie ersetzt weder die [[Datenmodellierung]] noch die Definition technischer [[Schnittstelle|Schnittstellen]], sondern beschreibt ausschließlich den funktionalen Umfang. Im Gegensatz zu [[Modulgrenze|Modulgrenzen]], die innerhalb des Systems [[Systemkomponente|Komponenten]] trennen, trennt sie das System von seiner [[Umgebung]].
- **Beispiel / Code:** ```plaintext
Beispiel 1: Use Case "[[Mitglieder_verwalten]]"
Systemgrenze:
- Innerhalb: [[MyClub]]-System (z. B. Mitgliederdatenbank, Berechtigungsmanagement)
- Außerhalb: [[Vereinsmanager]], [[Mail_Client]], externe [[Authentifizierung|Authentifizierungssysteme]]

Beispiel 2: Online-Shop
Systemgrenze:
- Innerhalb: Produktkatalog, Warenkorb, Bestellabwicklung, [[Benutzerverwaltung]]
- Außerhalb: [[Zahlungsdienstleister]], [[Logistikpartner]], externe [[API|APIs]] für Versandstatus
```
