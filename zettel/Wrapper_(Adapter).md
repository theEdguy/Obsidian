---
id: 2569aa30-5afd-4ecf-8cd6-62f6a0706bf8
title: "Wrapper (Adapter)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architekturmuster
  - middleware
  - schnittstellen
  - verteilte-systeme
  - software-design
  - adapter-pattern
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Wrapper (Adapter)]]

- **Kernkonzept:** Ein [[Wrapper|Wrapper]] (auch [[Adapter|Adapter]]) kapselt eine bestehende [[Komponente|Komponente]] und bietet ein angepasstes [[Interface|Interface]], um Inkompatibilitäten zwischen [[Schnittstelle|Schnittstellen]] zu überbrücken. Er transformiert [[Aufruf|Aufrufe]] der [[Client-Anwendung|Client-Anwendung]] in die erwartete Form der [[Altlast|Altlast]].
- **Nutzen & Zweck:** Der [[Wrapper|Wrapper]] löst das Problem der [[Schnittstellen-Inkompatibilität|Schnittstellen-Inkompatibilitäten]] zwischen [[Legacy-System|Legacy-Systemen]] und modernen [[Anwendung|Anwendungen]]. Er ermöglicht die [[Wiederverwendung|Wiederverwendung]] bestehender [[Funktionalität|Funktionalitäten]] ohne deren direkte [[Anpassung|Anpassung]] und reduziert so den [[Migrationsaufwand|Migrationsaufwand]] in [[Verteilte Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Ein [[Wrapper|Wrapper]] sollte nicht genutzt werden, wenn die [[Performance|Performance]] kritisch ist, da er zusätzliche [[Latenz|Latenz]] durch die [[Transformation|Transformation]] einführt. Alternativen wie [[Refactoring|Refactoring]] oder [[Neuentwicklung|Neuentwicklung]] sind vorzuziehen, wenn die [[Komplexität|Komplexität]] der [[Altlast|Altlast]] zu hoch ist oder die [[Schnittstelle|Schnittstelle]] grundlegend geändert werden muss. Im Gegensatz zu [[Interzeptor|Interzeptoren]] verändert ein [[Wrapper|Wrapper]] nicht das [[Verhalten|Verhalten]] der [[Middleware|Middleware]], sondern nur die [[Schnittstellen-Darstellung|Schnittstellen-Darstellung]].
- **Beispiel / Code:** ```python
# Beispiel: Wrapper für einen Linda-Tupelraum, der eine vereinfachte Schnittstelle bietet
class LindaWrapper:
    def __init__(self, tuple_space):
        self.tuple_space = tuple_space

    def write(self, author, topic, message):
        # Transformiert den Aufruf in das Linda-Interface
        self.tuple_space._out((author, topic, message))

    def read(self, author, topic):
        # Blockierender Aufruf, transformiert in das Linda-Interface
        return self.tuple_space._rd((author, topic, str))

# Nutzung:
blog = LindaWrapper(linda.universe._rd(("MicroBlog", linda.TupleSpace))[1])
blog.write("bob", "distsys", "Wrapper vereinfachen Schnittstellen")
message = blog.read("bob", "distsys")
```
