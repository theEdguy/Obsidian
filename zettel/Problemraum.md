---
id: accda9b6-d89b-4251-ae58-80ddb3c295f5
title: "Problemraum"
date: 2026-06-23
tags:
  - software_engineering
  - systemanalyse
  - anforderungsengineering
  - use_case
  - domänenmodellierung
  - softwareentwurf
  - prozess
  - draft
source: "software_engineering_kapitel_03"
---

# [[Problemraum]]

- **Kernkonzept:** Der [[Problemraum]] bezeichnet im Kontext des [[Software_Engineering]] und der [[Systemanalyse]] die abstrakte [[Domäne|Domäne]], in der ein zu lösendes [[Problem]] existiert. Er umfasst alle relevanten [[Anforderung|Anforderungen]], [[Randbedingung|Randbedingungen]], [[Akteur|Akteure]], Ziele und Konflikte, die für die Problembeschreibung und spätere [[Lösungsraum|Lösungserarbeitung]] essenziell sind. Der [[Problemraum]] wird durch eine strukturierte Analyse (z. B. mittels [[Use_Case_Diagramm]] oder [[Anforderungsdokumentation]]) erfasst und dient als Grundlage für die [[Modellierung]] im [[Lösungsraum]]. Er definiert den Bereich der realen Welt, der durch [[Nutzerbedürfnis|Nutzerbedürfnisse]], fachliche Zusammenhänge und [[Anforderung|Anforderungen]] geprägt ist, bevor technische [[Lösung|Lösungen]] entwickelt werden.
- **Nutzen & Zweck:** Der [[Problemraum]] erfüllt folgende zentrale Zwecke:
1. **Klärung der [[Domäne|Domäne]]**: Er zwingt [[Entwickler|Entwicklerinnen]] und [[Stakeholder|Stakeholdern]], das [[Problem]] vor der [[Implementierung]] präzise zu verstehen, um Fehlentwicklungen (z. B. durch falsche [[Annahme|Annahmen]]) zu vermeiden. Dies schafft eine gemeinsame [[Sprache]] zwischen allen Beteiligten und reduziert [[Missverständnis|Missverständnisse]].
2. **Trennung von Analyse und [[Design]]**: Durch die explizite Abgrenzung zum [[Lösungsraum]] wird verhindert, dass [[Lösungsdetail|Lösungsdetails]] zu früh in die Problembeschreibung einfließen (vgl. [[Separation_of_Concerns]]). Dies stellt sicher, dass die [[Software]] die tatsächlichen [[Nutzerbedürfnis|Bedürfnisse]] der [[Akteur|Akteure]] abbildet und nicht an den [[Anforderung|Anforderungen]] vorbeientwickelt wird.
3. **Risikominimierung**: Eine gründliche [[Problemraumanalyse]] identifiziert frühzeitig Konflikte (z. B. widersprüchliche [[Anforderung|Anforderungen]]) oder nicht-funktionale [[Randbedingung|Randbedingungen]] (z. B. [[Performance]]-Anforderungen). Dies verbessert die [[Kommunikation]] und erhöht die Qualität der späteren [[Implementierung]].
4. **Fachliche Fokussierung**: Der [[Problemraum]] konzentriert sich rein auf die fachlichen und konzeptionellen Aspekte, während technische [[Lösung|Lösungen]] bewusst ausgeklammert bleiben. Dies verhindert eine voreilige Festlegung auf [[Technologie|Technologien]] oder [[Architektur|Architekturen]] (z. B. [[Microservices]]).
- **Abgrenzung & Grenzen:** 1. **Keine [[Lösung|Lösungsvorschläge]]**: Der [[Problemraum]] beschreibt *was* das [[Problem]] ist, nicht *wie* es gelöst wird. [[Lösungsansatz|Lösungsansätze]] gehören in den [[Lösungsraum]].
2. **Dynamische Natur**: Der [[Problemraum]] ist nicht statisch – neue [[Anforderung|Anforderungen]] oder Erkenntnisse können ihn erweitern oder verändern (vgl. [[Agile_Entwicklung]]).
3. **Subjektivität**: Die Definition des [[Problemraum|Problemraums]] hängt stark von der Perspektive der [[Stakeholder]] ab. Beispiel: Eine [[Kundin]] sieht ein [[Usability]]-Problem, während [[Entwickler]] ein [[Performance]]-Problem priorisieren.
4. **Stolpersteine**:
   - **Überanalyse**: Zu detaillierte [[Problemraumanalyse|Problemraumbeschreibungen]] können zu [[Analysis_Paralysis]] führen.
   - **Vernachlässigung**: Wird der [[Problemraum]] zu oberflächlich behandelt, entstehen [[Lösung|Lösungen]], die das eigentliche [[Problem]] nicht adressieren (vgl. [[XY_Problem]]).
   - **Vermischung mit [[Lösungsraum]]**: Ein typischer Fehler ist die frühzeitige Festlegung auf [[Technologie|Technologien]] (z. B. "Wir brauchen [[Microservices]]") statt der Fokussierung auf das [[Problem]].
5. **Grenzen der Anwendung**: Der [[Problemraum]] sollte nicht genutzt werden, wenn bereits eine fertige technische [[Lösung]] vorliegt oder wenn die [[Anforderung|Anforderungen]] trivial und vollständig bekannt sind. Alternativen wie direktes [[Prototyping]] oder [[codezentrierter_Ansatz|codezentrierte Ansätze]] können effizienter sein, wenn keine komplexen fachlichen Abhängigkeiten bestehen oder wenn die [[Anforderung|Anforderungen]] dynamisch und schwer greifbar sind.
- **Beispiel / Code:** ```mermaid
classDiagram
    class Problemraum {
        +String beschreibung
        +List~Akteur~ akteure
        +List~Anforderung~ funktionaleAnforderungen
        +List~Anforderung~ nichtFunktionaleAnforderungen
        +List~Randbedingung~ randbedingungen
        +analysiere() Problemmodell
    }
    
    class Akteur {
        +String name
        +String rolle
    }
    
    class Anforderung {
        +String id
        +String text
        +Priorität priorität
    }
    
    class Randbedingung {
        +String beschreibung
        +Typ typ
    }
    
    Problemraum "1" *-- "0..*" Akteur : umfasst
    Problemraum "1" *-- "1..*" Anforderung : enthält
    Problemraum "1" *-- "0..*" Randbedingung : berücksichtigt
```

**Textuelles Beispiel (Use-Case-Extrakt für ein Bibliothekssystem):**
- **[[Akteur|Akteure]]**: [[Bibliothekarin]], [[Nutzerin]], [[Systemadministrator]]
- **Funktionale [[Anforderung|Anforderungen]]**:
  - FR-1: [[Nutzerin|Nutzerinnen]] müssen [[Buch|Bücher]] ausleihen können.
  - FR-2: [[Bibliothekarin|Bibliothekarinnen]] müssen [[Ausleihfrist|Ausleihfristen]] verwalten.
- **Nicht-funktionale [[Anforderung|Anforderungen]]**:
  - NFR-1: Das System muss 99,9% [[Verfügbarkeit]] bieten.
  - NFR-2: Die Suche nach [[Buch|Büchern]] darf max. 2 Sekunden dauern.
- **[[Randbedingung|Randbedingungen]]**:
  - RB-1: Das System muss mit der bestehenden [[Datenbank]] kompatibel sein.
  - RB-2: Die [[Implementierung]] muss innerhalb von 6 Monaten abgeschlossen sein.

```java
// Beispiel: Modellierung eines Mitglieds im Problemraum (fachliche Eigenschaften und Regeln)
class Mitglied {
    // Attribute (fachliche Eigenschaften aus dem Problemraum)
    private String name;
    private String adresse;
    private int alter;
    private int leistungspunkte;

    // Operation (fachliche Funktion aus dem Problemraum)
    public int leistungsprognose(Date datum) {
        // Berechnung basierend auf fachlichen Regeln (Problemraum)
        return this.leistungspunkte * berechneAltersfaktor(this.alter);
    }
    
    private double berechneAltersfaktor(int alter) {
        // Fachliche Logik: Altersabhängiger Faktor für Leistungsprognose
        if (alter < 18) return 1.2;
        else if (alter >= 18 && alter < 30) return 1.0;
        else if (alter >= 30 && alter < 50) return 0.9;
        else return 0.8;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Anforderungserfassung]]
- **Querverweise:**
  - [[Lösungsraum]]
