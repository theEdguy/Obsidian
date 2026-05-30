---
id: f66dce2c-9f6f-4904-8561-f35120cb9c05
title: "User_Story"
date: 2026-05-30
tags:
  - software_engineering
  - agile_entwicklung
  - anforderungsmanagement
  - scrum
  - product_backlog
  - akzeptanzkriterien
  - draft
source: "Klausur_Referenz"
---

# [[User_Story]]

- **Kernkonzept:** Eine [[User_Story]] ist eine kurze, informelle Beschreibung einer Softwarefunktionalität aus der Perspektive des Endbenutzers. Sie folgt typischerweise der Struktur: *"Als [Rolle] möchte ich [Funktionalität], um [Nutzen] zu erreichen."* User Stories sind ein zentrales Artefakt in agilen Entwicklungsmethoden wie [[Scrum]] oder [[Kanban]] und dienen als Platzhalter für Gespräche über Anforderungen, ohne technische Details vorwegzunehmen. Im Gegensatz zu [[Use_Case]]s sind sie weniger formal und fokussieren sich auf den *Wert* für den Nutzer, nicht auf Systeminteraktionen.
- **Nutzen & Zweck:** User Stories werden verwendet, um: 
1. **Anforderungen nutzerzentriert** zu erfassen und Prioritäten im [[Product_Backlog]] zu setzen.
2. **Kommunikation** zwischen Entwicklern, Product Ownern und Stakeholdern zu vereinfachen, indem sie technische Komplexität abstrahieren.
3. **Flexibilität** in der Entwicklung zu ermöglichen, da sie leicht angepasst oder neu priorisiert werden können.
4. **Akzeptanzkriterien** als Grundlage für [[Test_Driven_Development]] oder [[Behavior_Driven_Development]] zu definieren.

Sie fördern die Zusammenarbeit im Team und reduzieren Missverständnisse durch klare Fokussierung auf den Nutzen.
- **Abgrenzung & Grenzen:** **Abgrenzung zu [[Use_Case]]s:** 
- User Stories sind *kurz und wertorientiert*, während Use Cases detaillierte Interaktionsabläufe beschreiben (z. B. mit Akteuren, Vor-/Nachbedingungen).
- User Stories sind *kein Ersatz* für technische Spezifikationen, sondern ergänzen diese (z. B. durch [[Technical_Spike]]s oder [[Architekturentscheidungen]]).

**Grenzen/Stolpersteine:**
- *Zu vage Formulierungen* führen zu unklaren Anforderungen (z. B. fehlende Akzeptanzkriterien).
- *Technische Abhängigkeiten* werden oft ignoriert (z. B. Anbindung an [[Datenbank]]en oder [[Schnittstelle]]n zu Drittsystemen).
- *Skalierung* ist schwierig: Bei großen Projekten sind User Stories allein oft nicht ausreichend (hier helfen [[Epics]] oder [[Feature]]s als übergeordnete Strukturen).
- *Nicht-funktionale Anforderungen* (z. B. Performance, Sicherheit) lassen sich schwer als User Stories formulieren und erfordern separate [[Qualitätsattribute]].
- **Beispiel / Code:** {'textuell': 'Beispiel für eine User Story im Projekt *MyClub* (aus dem Kontext):\n\n**Titel:** Mitglied verwalten\n**Beschreibung:** *"Als Vereinsadministrator möchte ich Mitglieder hinzufügen, bearbeiten und löschen können, um die Mitgliederdaten aktuell zu halten."*\n**Akzeptanzkriterien:**\n1. Ein neues Mitglied kann mit Name, E-Mail und Mitgliedsstatus angelegt werden.\n2. Änderungen an bestehenden Mitgliedern werden in der [[Datenbank]] persistiert.\n3. Ein Mitglied kann nur gelöscht werden, wenn es keine offenen Rechnungen hat.\n4. Die Aktion erfordert eine Authentifizierung (siehe [[Authenticate_User]]).\n\n**Verknüpfung zu Schichten (aus dem Kontext):**\n- **Präsentationsschicht:** UI-Formular zur Eingabe der Mitgliederdaten.\n- **Logikschicht:** Validierung der Eingaben und Business-Regeln (z. B. Löschbeschränkung).\n- **Persistenzschicht:** Speicherung in der Datenbank (z. B. über [[Repository_Pattern]]).\n\n**Mermaid-Diagramm (Ablauf der User Story):**\n```mermaid\nsequenceDiagram\n    actor Admin as Vereinsadministrator\n    participant UI as Präsentationsschicht\n    participant Logic as Logikschicht\n    participant DB as Persistenzschicht\n    \n    Admin->>UI: Mitgliedsdaten eingeben\n    UI->>Logic: Daten validieren\n    Logic->>DB: Mitglied speichern\n    DB-->>Logic: Bestätigung\n    Logic-->>UI: Erfolgreiche Speicherung\n    UI-->>Admin: Bestätigungsmeldung\n```', 'code': None}
