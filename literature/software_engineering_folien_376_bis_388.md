# Lektürenotiz: SWE Vorlesung Folien 376 bis 388
- **QUELLE:** `subjects/software_engineering/slides/SWE.txt` (Slide 376-388)
- **AUTOR/AUTOREN:** Prof. Dr. Thomas Fuchß
- **KEY_INSIGHTS:**
  - Die Oberfläche einer Software sollte sich an den Use Cases orientieren, wobei für jeden Use Case mindestens eine View (ggf. mit zusätzlichen Views für verschiedene Zustände) sowie ein Hauptfenster und bei Bedarf Wizards implementiert werden.
  - Im MVC-Pattern (Model-View-Controller) übernimmt eine explizite Zustandsmaschine die Rolle des Subjekts, um die Zustände der Anwendung zu verwalten und Änderungen an die Observer (Views und Controller) zu kommunizieren.
  - Zustände organisieren die GUI, indem jedem Zustand ein Default-View zugewiesen wird und eine ViewFactory die passende View basierend auf dem aktuellen Zustand erstellt, wobei Views in mehreren Zuständen genutzt werden können.
  - Die Persistenzschicht wird typischerweise mit einem OR-Mapper (z. B. Hibernate) umgesetzt, der Datenbanktabellen auf Klassen abbildet und den Zugriff auf die Datenbank thread-sicher gestaltet, um Probleme mit Locks zu vermeiden.
  - Der Designprozess folgt einem iterativen Ansatz (z. B. Spiralmodell), bei dem Ziele definiert, Alternativen evaluiert, Risiken minimiert und das Produkt schrittweise entwickelt, getestet und verfeinert werden.

---
- **Zugehörige Zettel:**
  - [[Model_View_Controller_(MVC)]]
  - [[Observer_Pattern]]
  - [[Zustandsmaschine]]
  - [[ViewFactory]]
  - [[Object-Relational_Mapping_(ORM)]]
  - [[Spiralmodell]]
  - [[Lose_Kopplung]]
  - [[Schnittstelle]]
