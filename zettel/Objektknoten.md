---
id: c18165d9-0a27-44b1-8962-5e364838d8e3
title: "Objektknoten"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - datenfluss
  - draft
source: "software_engineering_kapitel_08"
---

# [[Objektknoten]]

- **Kernkonzept:** Ein [[Objektknoten]] in einem [[Aktivitätsdiagramm]] modelliert den [[Datenfluss]] zwischen [[Aktion|Aktionen]] und dient als Container für [[Objekt|Objekte]] eines definierten [[Typ|Typs]] mit begrenzter Kapazität. Er repräsentiert konkrete [[Daten]] oder [[Objekt|Objekte]], die während eines [[Prozess|Prozesses]] erzeugt, verändert oder weitergegeben werden, und ermöglicht so die explizite Visualisierung von [[Datenfluss|Datenflüssen]] in [[Ablauf|Abläufen]].
- **Nutzen & Zweck:** [[Objektknoten]] ermöglichen die detaillierte Darstellung des [[Datenfluss|Datenflusses]] in [[Geschäftsprozess|Geschäftsprozessen]] oder [[Algorithmus|Algorithmen]] und helfen, die Verbindung zwischen [[Aktion|Aktionen]] und den verarbeiteten [[Daten]] zu visualisieren. Sie lösen das Problem, dass reine [[Kontrollfluss|Kontrollflüsse]] in [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] keine Informationen über die verarbeiteten [[Daten]] liefern, was besonders bei komplexen [[Prozess|Prozessen]] mit vielen [[Datenabhängigkeit|Datenabhängigkeiten]] entscheidend ist. Zudem unterstützen sie die Modellierung von [[Datenhaltung]] und [[Datenverarbeitung]] und tragen zur Klarheit in der [[Systemarchitektur]] bei.
- **Abgrenzung & Grenzen:** [[Objektknoten]] sind nicht geeignet für die Modellierung von [[Kontrollfluss|Kontrollflüssen]] oder [[Zustandsübergang|Zustandsübergängen]], da hierfür [[Transition|Transitionen]] oder [[Zustandsdiagramm|Zustandsdiagramme]] besser geeignet sind. Sie sollten vermieden werden, wenn der Fokus ausschließlich auf dem [[Kontrollfluss]] liegt und [[Datenfluss|Datenflüsse]] keine Rolle spielen – in solchen Fällen sind reine [[Kontrollfluss]]-Darstellungen oder textuelle Beschreibungen effizienter. Zudem eignen sie sich weniger für hochabstrakte [[Modell|Modelle]], in denen [[Datenfluss|Datenflüsse]] bewusst ausgeklammert werden. Im Vergleich zu [[Pin|Pins]] bieten [[Objektknoten]] eine weniger detaillierte Modellierung des [[Datenfluss|Datenflusses]], da sie keine [[Schnittstelle|Schnittstellen]] oder [[Parameter]] explizit darstellen.
- **Beispiel / Code:** ```plantuml
@startuml
:Aktion 1: Mitgliedsdaten erfassen;
(mitglied : Mitglied) --> Aktion 2 : {weight = 1}
:Aktion 2: Mitglied in Datenbank speichern;
@enduml
```

**Konzeptionelles Code-Beispiel (Java-ähnliche Pseudocode-Darstellung):**
```java
// Aktion 1: Mitgliedsdaten erfassen
Mitglied mitglied = new Mitglied(name, adresse);

// Objektknoten: 'mitglied' wird zwischen den Aktionen weitergegeben
// Aktion 2: Mitglied in Datenbank speichern
datenbank.speichern(mitglied);
```

In [[UML]]-Aktivitätsdiagrammen wird der [[Objektknoten]] *mitglied* als Rechteck mit dem Objektnamen und optional dem [[Typ|Typ]] dargestellt. Er verbindet die [[Aktion|Aktionen]] *Mitgliedsdaten erfassen* und *Mitglied speichern* und visualisiert den [[Datenfluss]] des [[Objekt|Objekts]] *mitglied* zwischen diesen Schritten.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a5
- **Vorgänger / Parent:** [[Aktivitätsdiagramm_Bausteine]]
- **Folgezettel / Unterzettel:**
  - [[Parameter]]
  - [[Pin]]
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
