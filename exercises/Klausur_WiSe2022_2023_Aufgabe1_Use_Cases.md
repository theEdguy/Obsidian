---
id: f93f59e1-afd2-4878-8b99-bd536e31659f
title: "Klausur_WiSe2022_2023_Aufgabe1_Use_Cases"
date: 2026-05-30
tags:
  - software_engineering
  - wise2022_2023
  - exercise
  - draft
source: "SWE 2022-2023 mit Loesung.pdf"
---

# [[Klausur_WiSe2022_2023_Aufgabe1_Use_Cases]]

- **Aufgabenstellung:** 
  - **a:** (3 Punkte) Wann spricht man bei Use Cases von einer Extend-Beziehung und wann von einer Include-Beziehung? Was versteht man unter einem Extension Point?
  - **b:** (3 Punkte) Inwiefern sind moderne, agile Entwicklungsprozesse use-case-driven?
  - **c:** (2 Punkte) Oftmals ist eine detaillierte Beschreibung einzelner Use Cases von Vorteil. Welches typische UML-Diagramm würden Sie zur detaillierten Beschreibung eines einzelnen Use Cases heranziehen und warum?
  - **d:**
  (10 Punkte) Skizzieren Sie den folgenden Sachverhalt aus Sicht des Entwicklungsteams mithilfe eines Use-Case-Diagramms:
  
  Von der neuen App verspricht sich unser Vertrieb deutliche Impulse für eine verbesserte Kundenbindung. Unser Ziel ist es, den bestehenden Bestellprozess zu optimieren. Immer wieder gibt es Schwierigkeiten bei der Auslieferung und Aufstellung der bestellten Produkte. Adressen werden nicht gefunden, Ansprechpartner sind nicht erreichbar, Wege sind zu schmal für unsere Transporter, Aufstellorte sind unpräzise und vage. Diese Probleme erzeugen nicht nur Frust bei unseren Kunden und Mitarbeitern, sondern auch noch enorme Kosten. 
  
  Was ich mir vorstelle, ist eine App, die den bisherigen Web-basierten Bestellprozess revolutioniert, indem sie dem, für die Bestellung verantwortlichen Mitarbeiter unseres Kunden, nicht nur eine schnelle Übersicht über die von ihm betreuten Bestellungen gibt, sondern auch eine einzigartige Möglichkeit bietet, Bestellungen individuell zu präzisieren. Aufstellungsorte für die anzuliefernden Geräte könnten mit Fotos und Geokoordinaten präzisiert werden. Ich kenne kein Handy, das diese Funktionalität nicht bietet. Darüber hinaus könnten wir frei verfügbares Kartenmaterial nutzen, um uns ggf. Routen für die letzte Meile bestätigen oder durch den Kunden selbst planen zu lassen. Gerade gestern wurde wieder ein völlig falsches Werkstor angefahren, nur weil es laut Fahrer-Navi auf dem kürzesten Weg lag.
  
  Damit dies alles reibungslos funktioniert, sollte im Rahmen der Installation der App auch eine Personalisierung stattfinden. Mit anderen Worten eine eindeutige Zuordnung und Authentisierung des Anwenders hinsichtlich der Firma für die er oder sie tätig ist und ein entsprechender Datenabgleich mit den bei uns hinterlegten Daten. Diese Personalisierung sollte problemlos sein, da Handys typischerweise persönliche Geräte sind und manche unserer Kunden ihre Mitarbeiter mit Dienst-Handys versehen. Von einer ständigen Authentisierung müssten wir also absehen können, wenn wir entsprechende Credentials auf dem Gerät hinterlegen.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **Include-Beziehung:** Eine Include-Beziehung liegt vor, wenn die Aktionen eines Use Cases (B) vollständig in einen anderen Use Case (A) eingebunden werden. Dies wird im Use-Case-Diagramm durch einen gestrichelten Pfeil mit dem Stereotyp `<<include>>` von A zu B dargestellt. Der eingebundene Use Case (B) ist dabei ein obligatorischer Bestandteil des Basis-Use-Cases (A).
    - **Extend-Beziehung:** Eine Extend-Beziehung liegt vor, wenn die Aktionen eines Use Cases (A) unter bestimmten Bedingungen in einen anderen Use Case (B) integriert werden. Dies wird durch einen gestrichelten Pfeil mit dem Stereotyp `<<extend>>` von A zu B dargestellt. Der erweiternde Use Case (A) ist dabei optional und wird nur unter spezifischen Bedingungen ausgeführt.
    - **Extension Point:** Ein Extension Point ist ein definierter Punkt im Ablauf eines Use Cases, an dem entschieden wird, ob ein erweiternder Use Case (via `<<extend>>`) eingebettet wird. Er markiert die Stelle, an der die Bedingung für die Erweiterung geprüft wird.
  - **b:**
  Moderne, agile Entwicklungsprozesse sind use-case-driven, weil:
  1. **Kundenzentrierung**: Jeder Sprint liefert ein nutzbares Ergebnis, das direkt auf Kundenbedürfnisse abzielt. Use Cases gruppieren Funktionalitäten in sinnvolle, nutzbare Einheiten mit hoher [[Kohäsion|Kohäsion]].
  2. **Strukturierung**: Use Cases bieten eine übergeordnete Struktur, die sich an typischen Nutzungsabläufen orientiert. Kunden denken in Use Cases, was die Kommunikation und Priorisierung erleichtert.
  3. **Iterative Entwicklung**: Use Cases ermöglichen eine schrittweise Verfeinerung und Anpassung an sich ändernde Anforderungen, was agilen Prinzipien entspricht.
  - **c:**
  Zur detaillierten Beschreibung eines einzelnen Use Cases eignet sich ein **[[Aktivitätsdiagramm|Aktivitätsdiagramm]]**, weil:
  - Es Workflows und Abläufe graphisch darstellt, die den typischen Nutzungsprozess eines Use Cases abbilden.
  - **Swimlanes** die Trennung zwischen Akteur und System visualisieren.
  - **Actions** elementare Aufgaben innerhalb des Use Cases präzise beschreiben und so die Interaktionen zwischen Akteur und System klar aufschlüsseln.
  - **d:**
  - **beschreibung:**
  Das Use-Case-Diagramm sollte folgende Akteure und Use Cases enthalten:
  
  **Akteure:**
  - Kunde (Mitarbeiter des Kundenunternehmens, verantwortlich für Bestellungen)
  - Vertrieb (internes Team)
  - Logistik (internes Team, zuständig für Auslieferung)
  
  **Use Cases:**
  1. **Bestellung verwalten** (Basis-Use Case)
     - <<include>> **Bestellung präzisieren**
     - <<include>> **Authentisierung durchführen**
  2. **Bestellung präzisieren**
     - <<extend>> **Aufstellort mit Foto/Geokoordinaten festlegen** (Extension Point: "Präzisierung erforderlich")
     - <<extend>> **Route planen** (Extension Point: "Route unklar")
  3. **Authentisierung durchführen**
     - <<include>> **Datenabgleich mit Kundendaten**
  4. **Auslieferung vorbereiten** (für Logistik)
     - <<include>> **Route bestätigen**
  
  **Beziehungen:**
  - Der Kunde interagiert mit **Bestellung verwalten**, **Bestellung präzisieren** und **Authentisierung durchführen**.
  - Die Logistik interagiert mit **Auslieferung vorbereiten** und **Route bestätigen**.
  
  **Hinweis:**
  - Die Personalisierung (Authentisierung) wird als Include-Beziehung modelliert, da sie obligatorisch ist.
  - Die Präzisierung von Aufstellorten und Routenplanung wird als Extend-Beziehung modelliert, da sie optional sind und von Bedingungen abhängen.
    - **diagramm_skizze:**
  ```plantuml
  @startuml
  left to right direction
  actor Kunde
  actor Logistik
  actor Vertrieb
  
  rectangle App {
    usecase "Bestellung verwalten" as UC1
    usecase "Bestellung präzisieren" as UC2
    usecase "Authentisierung durchführen" as UC3
    usecase "Aufstellort mit Foto/Geokoordinaten festlegen" as UC4
    usecase "Route planen" as UC5
    usecase "Datenabgleich mit Kundendaten" as UC6
    usecase "Auslieferung vorbereiten" as UC7
    usecase "Route bestätigen" as UC8
  }
  
  Kunde --> UC1
  Kunde --> UC2
  Kunde --> UC3
  Logistik --> UC7
  Logistik --> UC8
  
  UC1 --> UC2 : <<include>>
  UC1 --> UC3 : <<include>>
  UC2 --> UC4 : <<extend>> (Präzisierung erforderlich)
  UC2 --> UC5 : <<extend>> (Route unklar)
  UC3 --> UC6 : <<include>>
  UC7 --> UC8 : <<include>>
  @enduml
  ```
  - **theoretischer_bezug:**
  - [[Use_Case_Diagramm|Use-Case-Diagramme]]
    - [[Include_Beziehung|Include-Beziehung]]
    - [[Extend_Beziehung|Extend-Beziehung]]
    - [[Extension_Point]]
    - [[Aktivitätsdiagramm|Aktivitätsdiagramme]]
    - [[Kohäsion]]
    - [[Agile_Entwicklung|Agile Entwicklungsprozesse]]
    - [[Swimlane]]
  - **stolpersteine:**
  - Verwechslung von Include- und Extend-Beziehungen: Include ist obligatorisch, Extend ist optional und bedingungsabhängig.
    - Unklare Abgrenzung der Akteure: Oft werden interne Teams (z. B. Logistik) vergessen oder fälschlich als externe Akteure modelliert.
    - Fehlende Extension Points: Ohne klare Definition der Bedingungen für Extend-Beziehungen wird das Diagramm unpräzise.
    - Überladene Use Cases: Zu viele Details in einem Use Case führen zu geringer [[Kohäsion|Kohäsion]] und schlechter Lesbarkeit.
    - Vernachlässigung der Personalisierung: Die Authentisierung wird oft als trivialer Use Case übersehen, obwohl sie für die Funktionalität essenziell ist.
    - Falsche Modellierung von Workflows: Use Cases beschreiben *was* das System leistet, nicht *wie* (dies sollte in [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] oder [[Sequenzdiagramm|Sequenzdiagrammen]] erfolgen).
  - **tags:**
  - klausur_ws_2022_2023
    - use_case
    - uml
    - anforderungsanalyse
    - agile_entwicklung
    - software_engineering
- **Theoretischer Bezug:** 
- **Stolpersteine / Fehlerquellen:** 
