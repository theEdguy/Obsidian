---
id: d13ce96a-56d4-46f9-a0e4-d05e61114e53
title: "Klausur_SoSe2024_Aufgabe1_Moderne_Entwicklungsprozesse_und_Use_Cases"
date: 2026-05-30
tags:
  - software_engineering
  - sose2024
  - klausur_sose_2024
  - use_case_analyse
  - empfehlungssysteme
  - agile_entwicklung
  - anforderungsmodellierung
  - ki_in_software
  - use_case_diagramm
  - exercise
  - draft
source: "SWE-SoSe-2024 - (Loesung).pdf"
---

# [[Klausur_SoSe2024_Aufgabe1_Moderne_Entwicklungsprozesse_und_Use_Cases]]

- **Aufgabenstellung:** 
  - **a:** Welche Eigenschaften verbinden Sie mit einem modernen Entwicklungsprozess und inwiefern sind Use Cases hilfreich für die Strukturierung und Organisation des Entwicklungsprozesses? (5 Punkte)
  - **b:**
  Für einen bestehenden Web-Shop soll ein ergänzendes Empfehlungssystem entwickelt werden, dessen späterer Einsatz stets durch den Web-Shop selbst angestoßen wird.
  
  Skizzieren Sie den folgenden Sachverhalt (aus Sicht des Entwicklungsteams für das Empfehlungssystem) in Form eines Use-Case-Diagramms. Welche Akteure interagieren mit diesem Empfehlungssystem und warum? (12 Punkte)
  
  Hinweis: Nutzen Sie die Aussagen von Herrn Maier (Product Owner) als Grundlage für Ihre Analyse:
  
  'Unser Ziel ist es, unsere Kunden während ihres Einkaufs mit weiteren Kaufempfehlungen zu versorgen, die abgestimmt sind auf ihr bisheriges Kaufverhalten, ihre aktuellen Suchanfragen, unsere Lagerbestände usw., um auf diesem Weg Zusatzkäufe zu generieren. Ich kann mir dabei unterschiedlichste Ansätze vorstellen. Im ersten Schritt genügt sicher eine einfache Lösung, die sich nur an der Art der gesuchten Produkte, deren Preis und eventuell ausgewählten Präferenzen orientiert. Im zweiten Schritt würde ich mich gerne auf eine KI-gestützte Lösung mit neuronalen Netzen fokussieren, die sich durch wiederholtes Training stetig verbessert. Dabei sollte der Trainingsvorgang nicht nur manuell, sondern besser automatisiert angestoßen werden, wenn die Qualität der Empfehlungen sinkt. Als KI-Framework würde ich TensorFlow vorschlagen, da es über alle APIs verfügt, die wir benötigen...'
  - **hinweis:** Hilfsmittel sind keine erlaubt.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **eigenschaften_moderner_entwicklungsprozesse:**
  - Agilität und Iterativität: Kurze Entwicklungszyklen (Sprints) mit regelmäßigen Feedbackschleifen.
      - Einbindung des Auftraggebers: Stakeholder sind aktiv in Entscheidungsprozesse eingebunden, um Anforderungen kontinuierlich zu validieren.
      - Flexibilität: Anpassungsfähigkeit an sich ändernde Anforderungen oder Prioritäten.
      - Kontinuierliche Verbesserung: Regelmäßige Retrospektiven zur Optimierung des Prozesses.
      - Transparenz: Klare Kommunikation und Sichtbarkeit des Fortschritts für alle Beteiligten.
    - **rolle_von_use_cases:**
  - Nutzerzentrierte Perspektive: Use Cases beschreiben Anforderungen aus Sicht der Endnutzer oder Systemakteure, was die Fokussierung auf den Mehrwert für den Nutzer fördert.
      - Kommunikationsgrundlage: Sie erleichtern die Verständigung zwischen Entwicklern, Product Ownern und anderen Stakeholdern, indem sie konkrete Szenarien und Interaktionen definieren.
      - Strukturierung der Entwicklung: Use Cases dienen als Ausgangspunkt für die Planung von Sprints, da sie funktionale Anforderungen in handhabbare Einheiten unterteilen.
      - Aufdeckung von Abhängigkeiten: Durch die Modellierung von Beziehungen zwischen Use Cases werden Abhängigkeiten und Wechselwirkungen zwischen Systemfunktionen sichtbar.
      - Priorisierung: Use Cases ermöglichen eine klare Priorisierung von Features, da sie direkt mit Nutzerbedürfnissen verknüpft sind.
  - **b:**
  - **akteure:**
  - - **name:** Kunde
        - **beschreibung:** Interagiert mit dem Web-Shop und erhält Empfehlungen basierend auf seinem Verhalten (z. B. Suchanfragen, Kaufhistorie). Der Kunde ist ein indirekter Akteur, da die Interaktion mit dem Empfehlungssystem über den Web-Shop erfolgt.
      - - **name:** Web-Shop (System)
        - **beschreibung:** Stößt die Generierung von Empfehlungen an, sobald ein Kunde im Shop aktiv ist. Der Web-Shop übermittelt relevante Daten (z. B. Suchanfragen, Kaufhistorie) an das Empfehlungssystem und erhält im Gegenzug Empfehlungen, die dem Kunden angezeigt werden.
      - - **name:** Product Owner / Administrator
        - **beschreibung:** Verantwortlich für die manuelle Initiierung von Trainingsvorgängen (z. B. bei Qualitätsverlust der Empfehlungen) und die Konfiguration des Empfehlungssystems (z. B. Auswahl des KI-Frameworks wie TensorFlow).
      - - **name:** Empfehlungssystem (selbst)
        - **beschreibung:** Kann als sekundärer Akteur betrachtet werden, wenn es automatisierte Trainingsvorgänge durchführt (z. B. bei sinkender Empfehlungsqualität).
      - use_case_diagramm_beschreibung_und_skizze_anleitung:
      - beschreibung_der_use_cases:
      - - **name:** Empfehlungen generieren (einfache Lösung)
        - **beschreibung:** Generiert Empfehlungen basierend auf Produktart, Preis und Kundenpräferenzen. Wird vom Web-Shop angestoßen, sobald ein Kunde im Shop aktiv ist.
        - **akteure:**
  - Web-Shop
          - Kunde (indirekt)
      - - **name:** Empfehlungen generieren (KI-gestützte Lösung)
        - **beschreibung:** Generiert Empfehlungen mithilfe eines neuronalen Netzes, das auf Kaufverhalten, Suchanfragen und Lagerbeständen trainiert ist. Wird vom Web-Shop angestoßen.
        - **akteure:**
  - Web-Shop
          - Kunde (indirekt)
      - - **name:** Modell manuell trainieren
        - **beschreibung:** Manuelles Anstoßen eines Trainingsvorgangs durch den Product Owner/Administrator, z. B. bei Qualitätsverlust der Empfehlungen.
        - **akteure:** - Product Owner / Administrator
      - - **name:** Modell automatisch trainieren
        - **beschreibung:** Automatisiertes Training des neuronalen Netzes, wenn die Qualität der Empfehlungen unter einen definierten Schwellenwert fällt. Wird vom Empfehlungssystem selbst angestoßen.
        - **akteure:** - Empfehlungssystem (selbst)
    - **skizze_anleitung:**
  - **schritte:**
  - Zeichnen Sie das Empfehlungssystem als zentrales System (Rechteck mit der Bezeichnung 'Empfehlungssystem').
        - Platzieren Sie die Akteure (Kunde, Web-Shop, Product Owner/Administrator) als Strichmännchen außerhalb des Systems.
        - Verbinden Sie die Akteure mit den entsprechenden Use Cases (Ovale) durch Assoziationslinien.
        - Nutzen Sie <<include>>-Beziehungen, um gemeinsame Funktionalitäten darzustellen (z. B. könnte 'Empfehlungen generieren (einfache Lösung)' und 'Empfehlungen generieren (KI-gestützte Lösung)' eine gemeinsame Basisfunktionalität nutzen).
        - Zeichnen Sie eine Systemgrenze um das Empfehlungssystem, um die Verantwortungsbereiche klar abzugrenzen.
        - Hinweis: Der Kunde interagiert nicht direkt mit dem Empfehlungssystem, sondern über den Web-Shop. Dies sollte durch eine Notiz oder eine gestrichelte Linie verdeutlicht werden.
      - **beispiel_diagramm_elemente:**
  - **system:** Empfehlungssystem
        - **akteure:**
  - Kunde
          - Web-Shop
          - Product Owner / Administrator
        - **use_cases:**
  - Empfehlungen generieren (einfache Lösung)
          - Empfehlungen generieren (KI-gestützte Lösung)
          - Modell manuell trainieren
          - Modell automatisch trainieren
        - **beziehungen:**
  - **Web-Shop:**
  - Empfehlungen generieren (einfache Lösung)
            - Empfehlungen generieren (KI-gestützte Lösung)
          - **Product Owner / Administrator:** - Modell manuell trainieren
          - **Empfehlungssystem (selbst):** - Modell automatisch trainieren
- **Theoretischer Bezug:** 
  - [[Use_Case_Diagramm|Use-Case-Diagramme]] zur Modellierung von Anforderungen und Akteuren.
  - [[Agile_Softwareentwicklung|Agile Softwareentwicklung]] als Rahmen für moderne Entwicklungsprozesse.
  - [[Stakeholder_Management|Stakeholder-Management]] für die Einbindung des Auftraggebers.
  - [[Iteratives_Entwickeln|Iterative Entwicklung]] zur schrittweisen Verbesserung des Systems.
  - [[Anforderungsanalyse|Anforderungsanalyse]] zur strukturierten Erfassung von Use Cases.
  - [[KI_in_Software_Engineering|KI in Software Engineering]] im Kontext von Empfehlungssystemen und automatisiertem Training.
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von Akteuren und Systemen: Der Kunde ist ein indirekter Akteur, da er nicht direkt mit dem Empfehlungssystem interagiert, sondern über den Web-Shop. Dies muss im Use-Case-Diagramm klar dargestellt werden.
  - Unklare Systemgrenzen: Das Empfehlungssystem sollte als eigenständiges System modelliert werden, nicht als Teil des Web-Shops, um die Verantwortungsbereiche klar zu trennen.
  - Überladung des Diagramms: Vermeiden Sie zu viele Use Cases oder Akteure. Konzentrieren Sie sich auf die im Text genannten Hauptfunktionalitäten (Empfehlungen generieren, Modell trainieren).
  - Fehlende Unterscheidung zwischen manuellen und automatisierten Prozessen: Der Trainingsvorgang kann sowohl manuell als auch automatisch angestoßen werden. Dies muss im Diagramm durch separate Use Cases dargestellt werden.
  - Vernachlässigung von <<include>>- oder <<extend>>-Beziehungen: Nutzen Sie diese, um gemeinsame Funktionalitäten oder optionale Erweiterungen darzustellen (z. B. könnte die KI-gestützte Lösung die einfache Lösung erweitern).
  - Falsche Priorisierung: Die Aussagen des Product Owners deuten auf eine schrittweise Implementierung hin (zuerst einfache Lösung, dann KI). Dies sollte im Diagramm durch klare Trennung der Use Cases reflektiert werden.
