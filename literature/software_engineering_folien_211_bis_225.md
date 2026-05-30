# Lektürenotiz: SWE Vorlesung Folien 211 bis 225
- **QUELLE:** `subjects/software_engineering/slides/SWE.txt` (Slide 211-225)
- **AUTOR/AUTOREN:** Prof. Dr. Thomas Fuchß
- **KEY_INSIGHTS:**
  - Verteilungsdiagramme (Deployment Diagrams) visualisieren die Laufzeitkonfiguration eines Systems, indem sie die Verteilung von Softwarekomponenten auf physische Knoten (z. B. Rechner, Prozessoren) und deren Kommunikationsbeziehungen darstellen.
  - Das Drei-Schichtenmodell (Präsentationsschicht, Logikschicht, Persistenzschicht) ist ein zentrales Architekturprinzip, das die klare Trennung von Zuständigkeiten in Softwareanwendungen ermöglicht und unabhängig vom Anwendungstyp (Client-Server oder Desktop) eingesetzt wird.
  - Architekturelle Schichten folgen einer strikten Hierarchie: Höhere Schichten nutzen tiefere Schichten, aber niemals umgekehrt, um Abhängigkeiten zu minimieren und die Wartbarkeit zu erhöhen.
  - Die Logikschicht ist ausschließlich für die Umsetzung der Geschäftslogik verantwortlich, während die Präsentationsschicht nur die Interaktion mit dem Nutzer steuert und die Persistenzschicht die Anbindung an externe Systeme (z. B. Datenbanken) übernimmt.
  - Das Model-View-Controller-Muster (MVC) strukturiert interaktive Anwendungen durch die Trennung von Datenmodell (Model), Darstellung (View) und Steuerung (Controller), um eine lose Kopplung und bessere Erweiterbarkeit zu erreichen.

---
- **Zugehörige Zettel:**
  - [[Verteilungsdiagramm]]
  - [[Drei-Schichtenmodell]]
  - [[Trennung_von_Zuständigkeiten]]
  - [[Model-View-Controller]]
  - [[Push-vs-Pull-Kommunikation]]
  - [[Schichtenabhängigkeit]]
  - [[Use-Case-getriebene_Architektur]]
  - [[Komponentenbasierte_Architektur]]
