---
id: 8acb03b0-f6c7-4b8f-90cf-55777695ec4e
title: "Meta-Modell-Beispiel"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Meta-Modell-Beispiel]]

- **Kernkonzept:** Ein Meta-Modell-Beispiel veranschaulicht die abstrakte Syntax einer Modellierungssprache wie UML, indem es die Struktur und Regeln der Sprache selbst in Form eines Modells beschreibt. Es definiert, welche Elemente (z. B. Klassen, Attribute, Assoziationen) in einem Modell erlaubt sind und wie diese miteinander in Beziehung stehen.
- **Nutzen & Zweck:** Das Konzept dient dazu, die Konsistenz und Klarheit von Modellierungssprachen wie UML zu gewährleisten. Es löst das Problem, dass ohne ein definiertes Meta-Modell unklar bleibt, welche Elemente und Beziehungen in einem Modell zulässig sind. Dadurch wird eine methodische Durchgängigkeit sichergestellt, die es ermöglicht, Modelle präzise zu erstellen, zu erweitern und zu interpretieren. Zudem bildet es die Grundlage für die Anpassung oder Erweiterung der Modellierungssprache an spezifische Domänen.
- **Abgrenzung & Grenzen:** Ein Meta-Modell sollte nicht genutzt werden, wenn einfache oder informelle Modellierungsansätze ausreichen, da es zusätzlichen Aufwand für die Definition und Pflege erfordert. Es unterscheidet sich von konkreten Modellen (z. B. einem Klassendiagramm für ein Softwaresystem) dadurch, dass es nicht die Realität abbildet, sondern die Regeln für die Abbildung selbst festlegt. Alternativen wie textuelle Beschreibungen oder informelle Skizzen sind weniger präzise, aber schneller umsetzbar, wenn keine formale Konsistenzprüfung erforderlich ist.
- **Beispiel / Code:** ```java
// Beispiel eines einfachen Meta-Modells für Klassen und Attribute in UML-ähnlicher Notation
class MetaKlasse {
    String name;
    List<MetaAttribut> attribute;
    List<MetaOperation> operationen;
}

class MetaAttribut {
    String name;
    String typ;
    String sichtbarkeit; // z. B. '+', '-', '#'
    String initialWert;
}

// Instanz des Meta-Modells: Eine konkrete Klasse 'Mitglied'
MetaKlasse mitglied = new MetaKlasse();
mitglied.name = "Mitglied";
mitglied.attribute.add(new MetaAttribut("name", "String", "+", null));
mitglied.attribute.add(new MetaAttribut("alter", "Date", "-", null));
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5b
- **Vorgänger / Parent:** [[Meta-Modell]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
