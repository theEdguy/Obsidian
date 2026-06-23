---
id: 7cf419a7-5116-415a-a653-849e98e5738a
title: "Klausur_WiSe2022_2023_Aufgabe3_Komponenten_und_Klassendiagramme"
date: 2026-05-30
tags:
  - software_engineering
  - wise2022_2023
  - klausur_ws_2022_2023
  - uml_diagramme
  - komponentendiagramm
  - klassendiagramm
  - entwurfsmuster
  - oop
  - modellierung
  - exercise
  - draft
source: "SWE 2022-2023 mit Loesung.pdf"
---

# [[Klausur_WiSe2022_2023_Aufgabe3_Komponenten_und_Klassendiagramme]]

- **Aufgabenstellung:** 
  - **a:**
  Skizzieren Sie ein [[Komponentendiagramm]] zu folgender Beschreibung:
  
  Eine Komponente A verfügt über die Ports B und C. Am Port B stellt sie die [[Schnittstelle|Schnittstellen]] D und E bereit. Am Port C greift sie über einen [[Assembly_Connector|Assembly Connector]] auf die Komponente F zu.
  - **b:**
  - **i:**
  Stellen Sie folgendes Code-Fragment in Form eines [[Klassendiagramm|Klassendiagramms]] dar:
  
  ```java
  class A implements B { @Override public B op() { return new C(); } }
  ```
    - **ii:**
  Stellen Sie folgendes Code-Fragment in Form eines [[Klassendiagramm|Klassendiagramms]] dar:
  
  ```java
  class A { private B[] myB = new B[] {new B(), new B(), new B()}; }
  ```
    - **iii:**
  Stellen Sie folgende Code-Fragmente in Form von [[Klassendiagramm|Klassendiagrammen]] dar:
  
  ```java
  class A extends B { protected List<B> myB = new ArrayList<>(); }
  class C extends A { public C() { this.myB.add(this); } }
  ```
  - **c:**
  Stellen Sie folgenden Sachverhalt mithilfe eines [[Klassendiagramm|Klassendiagramms]] dar:
  
  Eine Zelle besteht aus vielen Zellorganellen und ist von der Zellmembran begrenzt, die die im Zytoplasma eingebetteten Organellen umschließt. Bei den Organellen unterscheidet man zwischen Organellen mit und ohne Membran. Die wichtigsten Zellorganellen mit Membran sind die Mitochondrien, die Lysosomen, die Vesikel und der Zellkern selbst. Zu den Organellen ohne Membran zählen unter anderem die Ribosomen und der Nucleolus, letzterer ist Teil des Zellkerns.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  Das [[Komponentendiagramm]] sollte folgende Elemente enthalten:
  - Komponente A mit zwei Ports: B und C.
  - Port B stellt die [[Schnittstelle|Schnittstellen]] D und E bereit (Provided Interfaces).
  - Port C nutzt einen [[Assembly_Connector|Assembly Connector]], um auf Komponente F zuzugreifen (Required Interface).
  - Komponente F wird als separate Komponente dargestellt, die über den Assembly Connector mit Port C verbunden ist.
    - **skizze:**
  - **komponente_a:**
  - **ports:**
  - **port_b:**
  - **provided_interfaces:**
  - D
              - E
          - **port_c:** - **required_interface:** F
      - **komponente_f:** - **beschreibung:** Komponente F wird über einen Assembly Connector mit Port C von Komponente A verbunden.
  - **b:**
  - **i:**
  - **beschreibung:**
  Das [[Klassendiagramm]] zeigt:
  - Klasse A implementiert [[Schnittstelle]] B.
  - Methode `op()` in Klasse A gibt ein neues Objekt der Klasse C zurück, das ebenfalls [[Schnittstelle]] B implementiert (implizit oder explizit).
  - Beziehung: A → B (Implementierung), A → C (Rückgabewert der Methode).
      - **diagramm_elemente:**
  - **klassen:**
  - A
          - B
          - C
        - **beziehungen:**
  - - **quelle:** A
            - **ziel:** B
            - **typ:** Implementierung
            - **notation:** gestrichelte Linie mit geschlossenem Pfeil
          - - **quelle:** A
            - **ziel:** C
            - **typ:** Abhängigkeit (Rückgabewert der Methode `op()`)
            - **notation:** gestrichelte Linie mit offenem Pfeil
    - **ii:**
  - **beschreibung:**
  Das [[Klassendiagramm]] zeigt:
  - Klasse A enthält ein Array von Objekten der Klasse B.
  - Beziehung: A → B (Aggregation, da B unabhängig von A existieren kann).
      - **diagramm_elemente:**
  - **klassen:**
  - A
          - B
        - **beziehungen:**
  - - **quelle:** A
            - **ziel:** B
            - **typ:** Aggregation
            - **notation:** Linie mit leerer Raute an A
            - **multiplizitaet:** 1..* (Array mit drei Instanzen)
    - **iii:**
  - **beschreibung:**
  Das [[Klassendiagramm]] zeigt:
  - Klasse A erbt von Klasse B.
  - Klasse A enthält eine Liste von Objekten der Klasse B (Aggregation).
  - Klasse C erbt von Klasse A und fügt sich selbst in die Liste `myB` ein.
  - Beziehung: A → B (Vererbung), A → B (Aggregation), C → A (Vererbung).
      - **diagramm_elemente:**
  - **klassen:**
  - A
          - B
          - C
        - **beziehungen:**
  - - **quelle:** A
            - **ziel:** B
            - **typ:** Vererbung
            - **notation:** durchgezogene Linie mit geschlossenem Pfeil
          - - **quelle:** A
            - **ziel:** B
            - **typ:** Aggregation
            - **notation:** Linie mit leerer Raute an A
            - **attribut:** myB: List<B>
            - **multiplizitaet:** 0..*
          - - **quelle:** C
            - **ziel:** A
            - **typ:** Vererbung
            - **notation:** durchgezogene Linie mit geschlossenem Pfeil
  - **c:**
  - **beschreibung:**
  Das [[Klassendiagramm]] modelliert die biologische Struktur einer Zelle mit folgenden Elementen:
  - **Zelle**: Enthält Zytoplasma, Zellmembran und viele Zellorganellen (Komposition).
  - **Zellorganell**: Abstrakte Oberklasse für Organellen mit und ohne Membran.
  - **OrganellMitMembran**: Unterklasse von Zellorganell (z. B. Mitochondrien, Lysosomen, Vesikel, Zellkern).
  - **OrganellOhneMembran**: Unterklasse von Zellorganell (z. B. Ribosomen, Nucleolus).
  - **Zellkern**: Spezialisierung von OrganellMitMembran, enthält Nucleolus (Komposition).
  - **Zytoplasma**: Enthält Zellorganellen (Aggregation).
  - **Zellmembran**: Begrenzt die Zelle (Assoziation).
    - **diagramm_elemente:**
  - **klassen:**
  - Zelle
        - Zellmembran
        - Zytoplasma
        - Zellorganell
        - OrganellMitMembran
        - OrganellOhneMembran
        - Mitochondrium
        - Lysosom
        - Vesikel
        - Zellkern
        - Ribosom
        - Nucleolus
      - **beziehungen:**
  - - **quelle:** Zelle
          - **ziel:** Zellmembran
          - **typ:** Assoziation
          - **notation:** durchgezogene Linie
          - **beschreibung:** Zellmembran begrenzt die Zelle.
        - - **quelle:** Zelle
          - **ziel:** Zytoplasma
          - **typ:** Komposition
          - **notation:** Linie mit ausgefüllter Raute an Zelle
          - **multiplizitaet:** 1
        - - **quelle:** Zytoplasma
          - **ziel:** Zellorganell
          - **typ:** Aggregation
          - **notation:** Linie mit leerer Raute an Zytoplasma
          - **multiplizitaet:** 1..*
        - - **quelle:** Zellorganell
          - **ziel:** OrganellMitMembran
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** Zellorganell
          - **ziel:** OrganellOhneMembran
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** OrganellMitMembran
          - **ziel:** Mitochondrium
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** OrganellMitMembran
          - **ziel:** Lysosom
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** OrganellMitMembran
          - **ziel:** Vesikel
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** OrganellMitMembran
          - **ziel:** Zellkern
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** Zellkern
          - **ziel:** Nucleolus
          - **typ:** Komposition
          - **notation:** Linie mit ausgefüllter Raute an Zellkern
          - **multiplizitaet:** 1
        - - **quelle:** OrganellOhneMembran
          - **ziel:** Ribosom
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
        - - **quelle:** OrganellOhneMembran
          - **ziel:** Nucleolus
          - **typ:** Vererbung
          - **notation:** durchgezogene Linie mit geschlossenem Pfeil
- **Theoretischer Bezug:** 
  - [[Komponentendiagramm]]
  - [[Klassendiagramm]]
  - [[Schnittstelle]]
  - [[Assembly_Connector]]
  - [[Vererbung]]
  - [[Aggregation]]
  - [[Komposition]]
  - [[UML_Notation]]
  - [[Liskovsches_Substitutionsprinzip|Liskovsches Substitutionsprinzip]] (für Teilaufgabe b.iii)
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung von [[Provided_Interface|Provided]] und [[Required_Interface|Required Interfaces]] im [[Komponentendiagramm]].
  - Falsche Darstellung von [[Aggregation]] vs. [[Komposition]] (z. B. bei Zellorganellen in Teilaufgabe c).
  - Unklare Multiplizitäten in [[Klassendiagramm|Klassendiagrammen]] (z. B. Array in Teilaufgabe b.ii).
  - Vermischung von [[Vererbung]] und [[Implementierung]] (z. B. `implements` vs. `extends` in Teilaufgabe b.i).
  - Fehlende oder falsche Notation für [[Assembly_Connector|Assembly Connectors]] in Teilaufgabe a.
  - Übersehen der Selbstreferenz in Teilaufgabe b.iii (Klasse C fügt sich selbst in die Liste ein).
  - Unvollständige Modellierung der biologischen Hierarchie in Teilaufgabe c (z. B. Nucleolus als Teil des Zellkerns).
