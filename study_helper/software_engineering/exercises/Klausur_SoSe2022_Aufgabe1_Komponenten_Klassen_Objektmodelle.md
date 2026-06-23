---
id: 0f17cbc6-f322-4361-93a7-2a1754fbe95e
title: "Klausur_SoSe2022_Aufgabe1_Komponenten_Klassen_Objektmodelle"
date: 2026-05-30
tags:
  - software_engineering
  - sose2022
  - klausur_sose_2022
  - komponenten
  - klassendiagramm
  - schichtenarchitektur
  - objektmodellierung
  - exercise
  - draft
source: "SWE 2022 mit Loesung.pdf"
---

# [[Klausur_SoSe2022_Aufgabe1_Komponenten_Klassen_Objektmodelle]]

- **Aufgabenstellung:** 
  - **a:** Die Komponenten A und B sind unterschiedlichen Schichten zugeordnet. Was müssen Sie beachten, wenn Sie diese beiden Komponenten miteinander verbinden möchten?
  - **b:** Wann macht es Sinn, eine [[Assoziation]] zwischen zwei [[Klasse|Klassen]] durch eine eigene dritte [[Klasse]] zu implementieren? Geben Sie ein einfaches Beispiel.
  - **c:**
  Stellen Sie folgenden Sachverhalt mithilfe eines [[Klassendiagramm|Klassendiagramms]] dar:
  
  Bei Insekten unterscheidet man zwischen Apterygota und Pterygota (ungeflügelte und geflügelte Insekten). Zu letzteren gehören Bienen und Fliegen. Allen Fluginsekten gemein ist, dass sie vier Flügel (zwei Flügelpaare) besitzen, die von zahlreichen Tracheen durchzogen sind. Flügelpaare können auch verkümmert sein, dann sind die Flügel nur noch Schwingkölbchen.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **hinweis:** Gehen Sie davon aus, dass Komponente A der höheren und B der niederen Schicht zugeordnet ist.
    - **loesung:**
  - **Schichtenarchitektur-Prinzip**: Höhere [[Schicht|Schichten]] nutzen tiefere [[Schicht|Schichten]], niemals umgekehrt (1 Punkt).
  - **Schnittstellen-Nutzung**: Komponente A kann das [[Schnittstelle|Interface]] nutzen, das B anbietet (1 Punkt). Komponente B darf jedoch nicht das [[Schnittstelle|Interface]] von A nutzen.
  - **Informationsfluss von B zu A**: Falls B Informationen an A weitergeben muss, kann dies entweder über:
    - Rückgabewerte der durch A aufgerufenen Methoden oder
    - Benachrichtigungsmechanismen (z. B. [[Observer_Pattern|Observer-Pattern]] ähnlich wie in [[MVC|MVC]]) erfolgen (1 Punkt).
  - **b:**
  - **loesung:**
  - Eine eigene [[Klasse]] für eine [[Assoziation]] ist sinnvoll, wenn:
    - Es sich um eine komplexe **n-zu-m-Beziehung** handelt (1 Punkt).
    - Die [[Assoziation]] selbst [[Attribut|Attribute]] besitzt, die keiner der beteiligten [[Klasse|Klassen]] zugeordnet werden können (1 Punkt).
  
  **Beispiel**:
  - Beziehung zwischen [[Verein]] und [[Person]]: Ein [[Verein]] hat mehrere [[Mitglied|Mitglieder]], eine [[Person]] kann in mehreren [[Verein|Vereinen]] Mitglied sein (n-zu-m-Beziehung).
  - Die [[Assoziation]] selbst hat [[Attribut|Attribute]] wie Mitgliedsnummer, Eintrittsdatum oder Mitgliedsstatus.
  - Lösung: Eine eigene [[Klasse]] `Mitgliedschaft` modellieren, die die [[Assoziation]] zwischen [[Verein]] und [[Person]] verkörpert (2 Punkte).
  - **c:**
  - **loesung:**
  ```mermaid
  classDiagram
      class Insekt {
          <<abstract>>
      }
      
      class Apterygota {
          +ungeflügelt()
      }
      
      class Pterygota {
          <<abstract>>
          +flügelpaare: Flügel[2]
      }
      
      class Biene {
          +flügelpaare: Flügel[2]
      }
      
      class Fliege {
          +flügelpaare: Flügel[2]
          +schwingkölbchen: boolean
      }
      
      class Flügel {
          +tracheen: Trachee[]
          +verkümmert: boolean
      }
      
      Insekt <|-- Apterygota
      Insekt <|-- Pterygota
      Pterygota <|-- Biene
      Pterygota <|-- Fliege
      Pterygota "1" *-- "2" Flügel
  ```
  
  **Erläuterung**:
  - `Insekt` ist eine abstrakte [[Klasse]], von der `Apterygota` (ungeflügelt) und `Pterygota` (geflügelt) erben.
  - `Pterygota` ist ebenfalls abstrakt und enthält zwei [[Flügel]]-Objekte (Flügelpaare).
  - `Biene` und `Fliege` erben von `Pterygota`.
  - `Fliege` hat zusätzlich ein [[Attribut]] `schwingkölbchen` für verkümmerte Flügel.
  - Die [[Klasse]] `Flügel` enthält [[Attribut|Attribute]] wie `tracheen` und `verkümmert`.
  - Die Beziehung zwischen `Pterygota` und `Flügel` ist eine [[Komposition]] (ausgefüllte Raute).
- **Deine Bearbeitung (Notizen & Skizze):**
  - **(a) Schichten-Verbindung:** A > B. B kann Teil von A sein, nicht umgekehrt. B hat alle Abhängigkeiten von A, aber nicht umgekehrt. B gibt Infos an A weiter, A nicht an B.
  - **(b) Assoziationsklasse:** Wenn eine Schnittstelle/Sprachrohr benötigt wird, weil beide Klassen hierarchisch gleich sind und Informationen weitergeben wollen.
  - **(c) Insekten-Klassendiagramm:**
    * Insekten -> Apterygota / Pterygota {disjoint} (Generalisierung).
    * Pterygota -> Fliegen / Bienen {disjoint} (Generalisierung).
    * Pterygota "besitzt" Flügelpaar.
    * Flügelpaar -> Verkümmerte Flügelpaare (hat schwingkölbchen) / Unverkümmerte Flügelpaare (hat 1..* Tracheen) {disjoint} (Generalisierung).
- **Feedback & Optimierung für die Klausur:**
  > [!IMPORTANT]
  > **(a) Schichten-Verbindung (Korrektur):**
  > * In einer Schichtenarchitektur hängt die **höhere Schicht (A) von der tieferen Schicht (B) ab** (`A -> B`).
  > * Das bedeutet: A ruft B auf (A gibt Daten/Parameter nach unten). B darf A nicht kennen (lose Kopplung).
  > * B liefert Daten nur über **Rückgabewerte** nach oben oder benachrichtigt A passiv via **Observer-Pattern / Callbacks** (Events).
  > 
  > **(b) Assoziationsklasse (Korrektur):**
  > * Eine Assoziationsklasse wird bei einer **n-zu-m (Many-to-Many) Beziehung** verwendet, wenn die Beziehung selbst **eigene Attribute** hat (z. B. Klasse `Mitgliedschaft` mit `eintrittsdatum` zwischen `Person` und `Verein`).
  > 
  > **(c) Insekten-Klassendiagramm (Feedback):**
  > * Deine Vererbungshierarchien mit `{disjoint}` sind **absolut genial und fehlerfrei** gezeichnet!
  > * Die Spezialisierung des Flügelpaars in `Verkümmert` und `Unverkümmert` ist ein exzellenter objektorientierter Entwurf (besser als die Musterlösung, die nur ein Boolean-Flag nutzt!).
  > * *Klausur-Tipp:* Trage an der Beziehung von `Pterygota` zu `Flügelpaar` die Multiplizität **2** ein (da sie 2 Flügelpaare besitzen).
  > * *Klausur-Tipp:* Da Flügel existenzabhängig vom Insekt sind (Teil-Ganzes), verwende eine **Komposition** (schwarze Raute bei `Pterygota`).
  > 
  > **Mermaid-Code deiner bereinigten Skizze:**
  > ```mermaid
  > classDiagram
  >   class Insekt { <<abstract>> }
  >   class Apterygota
  >   class Pterygota { <<abstract>> }
  >   class Biene
  >   class Fliege
  >   
  >   class Fluegelpaar { <<abstract>> }
  >   class VerkuemmertesFluegelpaar {
  >       +istSchwingkoelbchen: boolean
  >   }
  >   class UnverkuemmertesFluegelpaar
  >   class Trachee
  > 
  >   Insekt <|-- Apterygota
  >   Insekt <|-- Pterygota
  >   Pterygota <|-- Biene
  >   Pterygota <|-- Fliege
  > 
  >   %% Komposition: Pterygota besitzt genau 2 Flügelpaare
  >   Pterygota "1" *-- "2" Fluegelpaar
  > 
  >   Fluegelpaar <|-- VerkuemmertesFluegelpaar
  >   Fluegelpaar <|-- UnverkuemmertesFluegelpaar
  > 
  >   UnverkuemmertesFluegelpaar "1" *-- "1..*" Trachee
  > ```
- **Theoretischer Bezug:** 
  - [[Schichtenarchitektur]]
  - [[Schnittstelle]]
  - [[Lose_Kopplung]]
  - [[Observer_Pattern]]
  - [[MVC]]
  - [[Assoziation]]
  - [[Klasse]]
  - [[Klassendiagramm]]
  - [[Vererbung]]
  - [[Komposition]]
  - [[Attribut]]
- **Stolpersteine / Fehlerquellen:** 
  - - **Schichtenarchitektur**: Verwechslung der Richtung der Abhängigkeiten (höhere [[Schicht|Schichten]] dürfen nicht von tieferen abhängen).
  - - **Assoziation vs. eigene Klasse**: Unnötige Modellierung einer dritten [[Klasse]] bei einfachen 1-zu-n-Beziehungen ohne zusätzliche [[Attribut|Attribute]].
  - - **Klassendiagramm**: Falsche Verwendung von [[Vererbung]] (z. B. `Apterygota` und `Pterygota` als Unterklassen von `Insekt` statt als Spezialisierungen).
  - - **Komposition vs. Aggregation**: Verwechslung der Rauten-Symbole (ausgefüllte Raute für [[Komposition]], leere für [[Aggregation]]).
  - - **Abstrakte Klassen**: Vergessen, `Insekt` oder `Pterygota` als `<<abstract>>` zu kennzeichnen.
  - - **Flügelpaare**: Falsche Modellierung der Flügel als einfache [[Attribut|Attribute]] statt als eigene [[Klasse]] mit [[Attribut|Attributen]].
