---
id: c2a1fc3e-a7e4-4852-8e4f-604577e39973
title: "Namensverweise (Name Linking)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - namensdienste
  - namensauflösung
  - datenstruktur
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Namensverweise (Name Linking)]]

- **Kernkonzept:** Namensverweise ermöglichen die flexible Verknüpfung von [[Namensraum|Namensräumen]] durch [[Verweis|Verweise]], die entweder als *Hard Links* (direkte Pfadauflösung) oder *Soft Links* (symbolische [[Verweis|Verweise]] auf andere [[Knoten|Knoten]]) realisiert werden. Sie erweitern die [[Namensauflösung]] um indirekte Zugriffe.
- **Nutzen & Zweck:** Das Konzept löst das Problem der starren [[Pfadbindung|Pfadbindungen]] in hierarchischen [[Namensraum|Namensräumen]], indem es dynamische [[Verweis|Verweise]] zwischen [[Knoten|Knoten]] erlaubt. Dadurch können [[Entität|Entitäten]] mehrfach referenziert oder umorganisiert werden, ohne ihre physische [[Adresse]] zu ändern.
- **Abgrenzung & Grenzen:** Namensverweise sollten nicht genutzt werden, wenn [[Konsistenz]] oder [[Performance]] kritisch sind: *Soft Links* erfordern zusätzliche [[Namensauflösung|Auflösungsschritte]] und können zu [[Zyklus|Zyklen]] oder veralteten [[Verweis|Verweisen]] führen. *Hard Links* sind auf hierarchische Strukturen beschränkt und nicht für verteilte Systeme mit unabhängigen [[Namensraum|Namensräumen]] geeignet.
- **Beispiel / Code:** Symbolischer Link (Soft Link) in einem [[Benennungsgraph|Benennungsgraphen]]:
```
Knoten n5: "/keys" → enthält den Namen "/home/steen/keys"
Auflösung:
1. Pfad "/keys" führt zu n5.
2. Inhalt von n5 wird gelesen → neuer Pfad "/home/steen/keys".
3. Namensauflösung startet erneut bei der Wurzel für "/home/steen/keys".
```
