---
id: c1efaee2-7da0-562c-bfa3-4f60d8dce16c
title: "MVC-Initialisierungsreihenfolge"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_11
  - draft
source: "Kapitel 11: MVC-Architektur und das Observer-Muster"
---

# [[MVC-Initialisierungsreihenfolge]]

- **Kernkonzept:** Der strukturierte Ablauf beim Starten einer MVC-Anwendung:
1. Erzeugung des Modells (Model).
2. Erzeugung der Views (und Controller).
3. Views registrieren sich als Observer beim Modell (Subject), um über Zustandsänderungen benachrichtigt zu werden.
4. Controller registrieren sich bei den Views für Benutzer-Events.
5. Der Event-Loop wird gestartet.
- **Nutzen & Zweck:** Der strukturierte Ablauf beim Starten einer MVC-Anwendung:
1. Erzeugung des Modells (Model).
2. Erzeugung der Views (und Controller).
3. Views registrieren sich als Observer beim Modell (Subject), um über Zustandsänderungen benachrichtigt zu werden.
4. Controller registrieren sich bei den Views für Benutzer-Events.
5. Der Event-Loop wird gestartet.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
