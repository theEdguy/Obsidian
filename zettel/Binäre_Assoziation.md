---
id: 4e448109-ae4d-431f-b886-85802c89bbaa
title: "Binäre_Assoziation"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - klassendiagramm
  - beziehung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Binäre_Assoziation]]

- **Kernkonzept:** Eine [[Binäre_Assoziation|binäre Assoziation]] beschreibt die grundlegendste Form der [[Beziehung|Beziehung]] zwischen genau zwei [[Klasse|Klassen]] in der [[Objektorientierte_Programmierung|objektorientierten Modellierung]], die eine strukturelle Verbindung zwischen deren [[Instanz|Instanzen]] definiert. Jedes [[Assoziationsende]] kann spezifische Eigenschaften wie [[Stelligkeit]], [[Rolle|Rollenbezeichner]] und [[Navigierbarkeit]] besitzen, um die Interaktion oder Referenzierung der [[Objekt|Objekte]] präzise abzubilden.
- **Nutzen & Zweck:** Die [[Binäre_Assoziation|binäre Assoziation]] ermöglicht die systematische Abbildung von Kommunikation und Zusammenarbeit zwischen [[Objekt|Objekten]] unterschiedlicher [[Klasse|Klassen]], indem sie strukturelle [[Abhängigkeit|Abhängigkeiten]] und [[Datenmodellierung|Datenmodelle]] klar darstellt. Sie löst das Problem, dass [[Objekt|Objekte]] ohne definierte [[Beziehung|Beziehungen]] nicht gezielt aufeinander zugreifen oder Daten austauschen können. Durch die explizite Modellierung werden [[Semantik|Semantik]], [[Navigierbarkeit]], [[Kardinalität|Kardinalitäten]] und [[Rolle|Rollen]] festgelegt, was die Verständlichkeit, [[Wartbarkeit]] und [[Erweiterbarkeit]] des Systems verbessert. Zudem unterstützt sie die präzise Abbildung realer Zusammenhänge in [[Klassendiagramm|Klassendiagrammen]], was für die [[Modellierung]] komplexer Systeme essenziell ist.
- **Abgrenzung & Grenzen:** Eine [[Binäre_Assoziation|binäre Assoziation]] ist nicht geeignet für [[Mehrstellige_Assoziation|mehrstellige Beziehungen]], bei denen mehr als zwei [[Klasse|Klassen]] beteiligt sind – hier sind [[Mehrstellige_Assoziation|n-stellige Assoziationen]] oder [[Assoziationsklasse|Assoziationsklassen]] vorzuziehen. Sie sollte auch vermieden werden, wenn die [[Beziehung]] existenzabhängige [[Teil-Ganzes-Beziehung|Teil-Ganzes-Strukturen]] beschreibt, da dafür [[Komposition]] oder [[Aggregation]] besser geeignet sind. Im Gegensatz zu [[Abhängigkeit|Abhängigkeiten]] (Dependencies) beschreibt eine [[Binäre_Assoziation|binäre Assoziation]] eine dauerhafte, strukturelle Verbindung, nicht nur eine temporäre oder dynamische [[Beziehung]]. Zudem ist sie ungeeignet, wenn die [[Beziehung]] keine klare [[Semantik]] oder [[Kardinalität]] besitzt, da dies zu unklaren oder fehleranfälligen [[Modellierung|Modellen]] führt. Für Fälle, in denen zusätzliche [[Attribut|Attribute]] oder [[Operation|Operationen]] direkt der [[Beziehung]] zugeordnet werden müssen, sind [[Assoziationsklasse|Assoziationsklassen]] die bessere Wahl.
- **Beispiel / Code:** ```java
// Beispiel einer [[Binäre_Assoziation|binären Assoziation]] zwischen 'Verein' und 'Mitglied' (einseitige Navigierbarkeit)
class Verein {
    private List<Mitglied> mitglieder;
    
    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
}

class Mitglied {
    // Keine Referenz zurück zum Verein (einseitige Navigierbarkeit)
}

// Beispiel einer [[Binäre_Assoziation|binären Assoziation]] zwischen 'Kunde' und 'Bestellung' (beidseitige Navigierbarkeit)
class Kunde {
    private List<Bestellung> bestellungen;
    
    public void bestellungHinzufuegen(Bestellung bestellung) {
        bestellungen.add(bestellung);
    }
}

class Bestellung {
    private Kunde kunde;
    
    public Bestellung(Kunde kunde) {
        this.kunde = kunde;
        kunde.bestellungHinzufuegen(this);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a1a
- **Vorgänger / Parent:** [[Assoziation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Assoziation]]
  - [[Klassendiagramm]]
