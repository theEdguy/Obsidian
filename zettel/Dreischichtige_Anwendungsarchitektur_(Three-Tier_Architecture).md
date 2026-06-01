---
id: 54bd862a-79c1-4048-85fe-0d9ef27f4e84
title: "Dreischichtige Anwendungsarchitektur (Three-Tier Architecture)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - software-design
  - schichtenmodell
  - datenbank
  - benutzerschnittstelle
  - geschäftslogik
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Dreischichtige Anwendungsarchitektur (Three-Tier Architecture)]]

- **Kernkonzept:** Die dreischichtige Anwendungsarchitektur [[Architekturstil|Architekturstile]] unterteilt [[Anwendung|Anwendungen]] in drei logische [[Schicht|Schichten]]: Benutzerschnittstelle, Verarbeitungsebene und Datenebene, um [[Komponente|Komponenten]] klar zu trennen und [[Wartbarkeit|wartbarer]] zu gestalten.
- **Nutzen & Zweck:** Dieser [[Architekturstil]] löst das Problem der engen Kopplung zwischen [[Benutzerinteraktion]], [[Geschäftslogik]] und [[Datenhaltung]] in [[monolithisch|monolithischen]] Systemen. Er ermöglicht [[Skalierbarkeit]], [[Wiederverwendbarkeit]] von [[Komponente|Komponenten]] und vereinfacht die [[Entwicklung]] sowie [[Pflege]] von [[verteilte Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für hochgradig [[performanzkritisch|performanzkritische]] oder [[Echtzeit|Echtzeit-Systeme]], da die Kommunikation zwischen [[Schicht|Schichten]] [[Latenz]] verursachen kann. Unterscheidet sich von [[zweischichtig|zweischichtigen]] Architekturen durch die explizite Trennung der Verarbeitungsebene und von [[Microservices]] durch die stärkere logische (statt physikalische) Trennung.
- **Beispiel / Code:** Beispiel: Einfache Suchmaschine (vereinfacht)

1. **Benutzerschnittstelle (Präsentationsebene)**:
   - HTML-Formular zur Eingabe von Suchbegriffen.
   - Sendet Anfragen an die Verarbeitungsebene.

2. **Verarbeitungsebene (Logikschicht)**:
   ```python
   def generate_query(keyword):
       return f"SELECT * FROM webpages WHERE content LIKE '%{keyword}%';"
   
   def rank_results(results):
       return sorted(results, key=lambda x: x['relevance'], reverse=True)
   ```

3. **Datenebene (Datenhaltungsschicht)**:
   - Datenbank mit Webseiten-Metadaten und Inhalten.
   - Führt Abfragen aus und gibt Rohdaten zurück.
