---
id: dc1eab56-9fe3-47b7-8194-654a08f3945a
title: "Architektur"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - architekturstil
  - komponenten
  - schnittstellen
  - schichtenmodell
  - rest
  - publish-subscribe
  - objektbasiert
  - service-orientiert
  - software-design
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Architektur]]

- **Kernkonzept:** Die [[Architektur]] eines [[Verteiltes_System|verteilten Systems]] beschreibt den [[Entwurf]] einer [[Lösung]] unter Berücksichtigung von [[Bedingung|Bedingungen]] und [[Einschränkung|Einschränkungen]]. Sie definiert [[Komponente|Komponenten]], deren [[Schnittstelle|Schnittstellen]] und [[Verbindung|Verbindungen]] sowie den [[Datenfluss]] zwischen ihnen und folgt dabei [[Architekturstil|Architekturstilen]], die generelle [[Prinzip|Prinzipien]] für die Gestaltung vorgeben.
- **Nutzen & Zweck:** Eine [[Architektur]] ermöglicht die strukturierte [[Organisation]] von [[Komponente|Komponenten]] und deren [[Interaktion]] in [[Verteilte_Systeme|verteilten Systemen]], um [[Skalierbarkeit]], [[Wartbarkeit]], [[Modularität]] und [[Effizienz]] zu gewährleisten. Durch klare [[Schnittstelle|Schnittstellen]] und [[Konnektor|Konnektoren]] wird die [[Kommunikation]] standardisiert, die [[Komplexität]] reduziert und eine Grundlage für die [[Implementierung]] sowie die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]] geschaffen. Sie löst das [[Problem]] unkontrollierter [[Komplexität]] und fördert die [[Kohäsion]] innerhalb der [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** Eine [[Architektur]] ist nicht sinnvoll, wenn die [[Anforderung|Anforderungen]] stark dynamisch oder unklar sind, da starre [[Architektur|Architekturen]] [[Anpassung|Anpassungen]] erschweren. Alternativen wie [[Monolith]]ische Systeme oder [[Ad-hoc-Entwicklung]] können bei kleinen, trivialen oder kurzlebigen [[System|Systemen]] effizienter sein, da der Aufwand für die [[Planung]] den Nutzen übersteigt. Zudem sind bestimmte [[Architekturstil|Architekturstile]] wie [[REST]] oder [[Publish-Subscribe]] nicht universell einsetzbar, sondern abhängig vom [[Anwendungsfall]]. Hohe [[Flexibilität]] oder häufige [[Anpassung|Anpassungen]] erfordern oft [[Event-gesteuertes_System|Event-gesteuerte Systeme]] oder [[Mikroservice|Mikroservice-Architekturen]].
- **Beispiel / Code:** {'beschreibung': 'Geschichtete [[Architektur]] am Beispiel eines [[Client-Server-Modell|Client-Server-Modells]] mit [[Socket]]-Kommunikation:', 'client': {'code': "```python\nfrom socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.connect((HOST, PORT))\ns.send('Hello, world')\ndata = s.recv(1024)\nprint(data)\ns.close()\n```", 'erläuterung': 'Der [[Client]] sendet eine Nachricht an den [[Server]] über eine [[Socket]]-Verbindung und empfängt eine Antwort. Dies demonstriert die [[Kommunikation]] zwischen [[Komponente|Komponenten]] in einer geschichteten [[Architektur]].'}, 'server': {'code': '```python\nfrom socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.bind((HOST, PORT))\ns.listen(1)\n(conn, addr) = s.accept()\nwhile True:\n    data = conn.recv(1024)\n    if not data: break\n    conn.send(str(data) + "*")\nconn.close()\n```', 'erläuterung': 'Der [[Server]] wartet auf [[Anfrage|Anfragen]], verarbeitet diese und sendet eine modifizierte Antwort zurück. Dies zeigt die [[Verarbeitung]] von [[Datenfluss|Datenflüssen]] in einer [[Schichtenarchitektur|geschichteten Architektur]].'}}
