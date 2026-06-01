---
id: 5f3086f8-f27c-4850-8975-94aff22afe7b
title: "Namen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - adressierung
  - skalierbarkeit
  - netzwerk
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Namen]]

- **Kernkonzept:** In [[Verteilte Systeme|verteilten Systemen]] dienen [[Name|Namen]] als abstrakte Referenzen auf [[Entität|Entitäten]], um [[Zugriffspunkt|Zugriffspunkte]] unabhängig von deren [[Adresse|Adressen]] zu identifizieren. Sie ermöglichen die Trennung von logischer Identität und physischer Lokation.
- **Nutzen & Zweck:** [[Name|Namen]] lösen das Problem der ortsunabhängigen Referenzierung von [[Entität|Entitäten]] in [[Verteilte Systeme|verteilten Systemen]]. Sie ermöglichen [[Namensauflösung|Namensauflösungen]], um benutzerfreundliche Bezeichner in technische [[Adresse|Adressen]] zu überführen, und unterstützen so die Skalierbarkeit und Flexibilität der Systeme.
- **Abgrenzung & Grenzen:** [[Name|Namen]] sind nicht geeignet, wenn direkte Adressierung (z. B. in lokalen Netzwerken) effizienter ist oder wenn die [[Entität|Entitäten]] keine dynamische Lokation benötigen. Im Gegensatz zu [[Bezeichner|Bezeichnern]] tragen sie oft semantische Bedeutung, was die Eindeutigkeit oder Persistenz einschränken kann. Für flache Namensräume sind [[Verteilte Hash-Tabelle|verteilte Hash-Tabellen]] oder hierarchische Ansätze wie DNS besser skalierbar.
- **Beispiel / Code:** Beispiel für eine einfache Namensauflösung in einem verteilten System:

```
// Namensdienst-Tabelle (Name → Adresse)
namensdienst = {
    "datei-server-1": "192.168.1.10:8080",
    "datenbank-master": "10.0.0.5:3306"
}

// Auflösung eines Namens
function loese_auf(name) {
    return namensdienst[name];
}

// Nutzung
adresse = loese_auf("datei-server-1"); // Gibt "192.168.1.10:8080" zurück
```

Beispiel für einen [[Bezeichner]] (eindeutig und persistent):
- UUID: `550e8400-e29b-41d4-a716-446655440000`
