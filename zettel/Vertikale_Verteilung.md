---
id: c817bf60-5b69-4db6-9eed-18036376eb74
title: "Vertikale Verteilung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - schichtenmodell
  - middleware
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Vertikale Verteilung]]

- **Kernkonzept:** Die [[Verteilung|vertikale Verteilung]] unterteilt [[verteilte Systeme]] in drei logische [[Schicht]]en (Präsentation, Anwendung, Datenhaltung), die auf separaten [[Server]]n oder [[Maschine]]n ausgeführt werden, um eine klare Trennung der Verantwortlichkeiten zu erreichen.
- **Nutzen & Zweck:** Sie löst das Problem der [[Skalierbarkeit]] und [[Wartbarkeit]] in komplexen [[System]]en, indem sie [[Komponente]]n nach funktionalen [[Schicht]]en trennt. Dies ermöglicht unabhängige [[Skalierung]] einzelner [[Schicht]]en und vereinfacht die [[Integration]] neuer [[Technologie]]n oder [[Dienst]]e.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Systeme]] mit hoher [[Latenz]]-Empfindlichkeit oder einfacher [[Anwendung]]slogik, da die zusätzliche Kommunikation zwischen [[Schicht]]en Overhead erzeugt. Unterscheidet sich von [[horizontale Verteilung|horizontaler Verteilung]], die [[Komponente]]n nach Datenpartitionen statt funktionalen [[Schicht]]en aufteilt.
- **Beispiel / Code:** Dreischichtige Architektur mit separaten [[Server]]n:
1. **Präsentationsschicht** (Client): User Interface (z. B. Webbrowser auf R1).
2. **Anwendungsschicht** (R3): Geschäftslogik (z. B. Webserver mit REST-API).
3. **Datenhaltungsschicht** (R4): Datenbank (z. B. MySQL-Server).

Beispiel-Code (Pseudocode):
```
// Client (R1) sendet Request an Anwendungsserver (R3)
fetch('http://R3/api/data', { method: 'GET' })
  .then(response => response.json())
  .then(data => displayUI(data));

// Anwendungsserver (R3) fragt Datenbankserver (R4) ab
app.get('/api/data', async (req, res) => {
  const result = await db.query('SELECT * FROM table', [], R4);
  res.json(result.rows);
});
```
