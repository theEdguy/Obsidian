---
id: 0b260dcd-6b29-46e6-af62-ac02afbed695
title: "Mehrschichtige Architekturen (Einschichtig, Zweischichtig, Dreischichtig)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - software-design
  - client-server
  - schichtenmodell
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Mehrschichtige Architekturen (Einschichtig, Zweischichtig, Dreischichtig)]]

- **Kernkonzept:** Mehrschichtige [[Architektur|Architekturen]] strukturieren [[Verteiltes System|verteilte Systeme]] in logische [[Schicht|Schichten]], um [[Komplexität]] zu reduzieren und [[Trennung der Verantwortlichkeiten|getrennte Verantwortlichkeiten]] zu ermöglichen. Typische Varianten sind einschichtig (monolithisch), zweischichtig (Client-Server) und dreischichtig (Client-Anwendung-Datenbank).
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der [[Skalierbarkeit]], [[Wartbarkeit]] und [[Flexibilität]] in [[Software|Softwaresystemen]], indem es [[Funktionalität]] in klar abgegrenzte [[Schicht|Schichten]] unterteilt. Es ermöglicht [[Wiederverwendbarkeit]] von [[Komponente|Komponenten]] und vereinfacht die [[Anpassung]] an sich ändernde Anforderungen.
- **Abgrenzung & Grenzen:** Mehrschichtige [[Architektur|Architekturen]] sind nicht geeignet für hochgradig [[dezentralisierte Systeme]], wie [[Peer-to-Peer-Systeme]], da sie eine [[zentralisierte Steuerung]] oder [[Hierarchie]] voraussetzen. Bei einfachen Anwendungen kann der [[Overhead]] der [[Schicht|Schichten]] die [[Performance]] unnötig beeinträchtigen. Alternativen wie [[Microservices]] oder [[Event-driven Architecture|ereignisgesteuerte Architekturen]] bieten mehr [[Flexibilität]] in dynamischen Umgebungen.
- **Beispiel / Code:** Dreischichtige Architektur am Beispiel einer Webanwendung:

1. **Präsentationsschicht (Client)**:
   - HTML/CSS/JavaScript (z. B. React oder Angular)
   - Läuft auf dem [[Endgerät]] des Nutzers (z. B. Browser).

2. **Anwendungsschicht (Server)**:
   ```python
   # Beispiel: Flask (Python) als Anwendungsserver
   from flask import Flask, request, jsonify
   app = Flask(__name__)

   @app.route('/api/data', methods=['GET'])
   def get_data():
       # Logik zur Datenverarbeitung
       return jsonify({'message': 'Daten erfolgreich abgerufen'})
   ```

3. **Datenhaltungsschicht (Datenbankserver)**:
   - SQL-Datenbank (z. B. PostgreSQL) oder NoSQL (z. B. MongoDB).
   - Speichert und verwaltet die [[Daten|Datenbestände]].
