---
id: 3b8aed85-9561-44fc-9ea2-6b2ef82dadc2
title: "Empathy_und_Template_in_Objektorientierung"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - draft
source: "SWE Slides (Folien 46-60)"
---

# [[Empathy_und_Template_in_Objektorientierung]]

- **Kernkonzept:** [[Empathy_in_Objektorientierung|Empathy]] und [[Template_in_Objektorientierung|Templates]] sind zwei komplementäre [[Vererbungsmechanismus|Mechanismen]] der [[Objektorientierung]], die [[Wiederverwendbarkeit]] und [[Flexibilität]] in [[Softwarearchitektur|Softwarearchitekturen]] erhöhen. Während [[Empathy_in_Objektorientierung|Empathy]] das [[Verhalten]] eines [[Objekt|Objekts]] durch dynamische Weitergabe von [[Nachrichten]] nachahmt, definieren [[Template_in_Objektorientierung|Templates]] eine [[Schablone]] für gemeinsame [[Eigenschaft|Eigenschaften]] und [[Verhalten]] von [[Instanz|Instanzen]].
- **Nutzen & Zweck:** Beide Konzepte lösen zentrale [[Herausforderung|Herausforderungen]] der [[Objektorientierung]]: [[Empathy_in_Objektorientierung|Empathy]] ermöglicht dynamische [[Anpassung]] von [[Verhalten]] ohne [[Code]]-Duplikation, während [[Template_in_Objektorientierung|Templates]] [[Konsistenz]] und [[Struktur]] durch garantierte [[Eigenschaft|Eigenschaften]] und [[Schnittstelle|Schnittstellen]] sicherstellen. Zusammen fördern sie [[Modularität]] und [[Erweiterbarkeit]] in [[Softwareentwurf|Softwareentwürfen]], insbesondere in [[Domain-Driven_Design|domänenspezifischen Systemen]] oder [[Frameworks]].
- **Abgrenzung & Grenzen:** [[Empathy_in_Objektorientierung|Empathy]] ist ungeeignet für [[Problembereich|Problembereiche]], die statische [[Vererbung]] oder [[Komposition]] erfordern, da es zu unklaren [[Verantwortlichkeit|Verantwortlichkeiten]] führen kann. [[Template_in_Objektorientierung|Templates]] hingegen können [[Starre_Architektur|starre Architekturen]] begünstigen, wenn sie übermäßig eingesetzt werden, insbesondere in [[Problembereich|Bereichen]], die dynamische [[Anpassung]] benötigen. Beide Mechanismen sollten mit [[Entwurfsmuster|Mustern]] wie [[Strategy_Pattern]] oder [[Decorator_Pattern]] kombiniert werden, um [[Flexibilität]] zu wahren. Eine sorgfältige Abwägung zwischen [[Vererbung]] und [[Komposition]] ist entscheidend, um [[Kohäsion]] und [[Lose_Kopplung]] zu erhalten.
- **Beispiel / Code:** Beispiel für [[Empathy_in_Objektorientierung|Empathy]] in Smalltalk-ähnlicher Syntax:

```smalltalk
"Klasse B definiert Methode foo, die self bar aufruft"
B >> foo
    self bar.

"Klasse A erbt von B und überschreibt bar"
A >> bar
    Transcript show: 'A bar'.

"Aufruf von A new foo führt zu: Ausgabe 'A bar' (Empathy)"
```

Beispiel für [[Template_in_Objektorientierung|Templates]] in Eiffel:

```eiffel
class PERSON
    feature {NONE}
        name: STRING
    feature
        set_name (a_name: STRING)
            do
                name := a_name
            end
        get_name: STRING
            do
                Result := name
            end
end

"Alle Instanzen von PERSON teilen dieselbe Struktur (Template)"
```
