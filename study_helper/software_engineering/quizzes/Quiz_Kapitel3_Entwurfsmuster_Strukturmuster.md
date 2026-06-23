---
type: quiz
chapter: 3
subtopic: "Entwurfsmuster: Strukturmuster"
format: callout
generated_at: 2026-06-06 16:29:21
tags:
  - software_engineering
  - quiz
  - chapter_3
---

# 🧠 Quiz: Entwurfsmuster: Strukturmuster

**Kapitel:** Kapitel 3: Design – Softwarearchitektur & Entwurfsmuster
**Details:** (Bridge, Adapter)

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zu den Strukturmustern **Bridge** und **Adapter** im Format der Vorlesungsinhalte:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt korrekt den **Zweck des Bridge-Musters**?**
> - [ ] A) Es ermöglicht die Zusammenarbeit zwischen Klassen mit inkompatiblen Schnittstellen, indem es eine Vermittlungsschicht (Wrapper) einfügt.
> - [ ] B) Es entkoppelt Abstraktion und Implementierung, sodass beide unabhängig voneinander variiert werden können.
> - [ ] C) Es dient dazu, die Mehrfachvererbung in objektorientierten Sprachen zu ersetzen, indem es eine gemeinsame Oberklasse definiert.
> - [ ] D) Es transformiert die Schnittstelle einer Klasse in eine andere, die der Client erwartet, ohne jedoch die Funktionalität zu ändern.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Das **Bridge-Muster** (nach GoF) trennt die Abstraktion (z. B. eine Klasse mit hoher Abstraktionsebene) von der Implementierung (z. B. konkrete Implementierungsklassen), sodass beide unabhängig voneinander erweitert oder ausgetauscht werden können. Dies entspricht genau der Definition in den Vorlesungsfolien (Folie 346–360).
> - **A** beschreibt den **Adapter**, nicht die Bridge.
> - **C** ist falsch, da die Bridge keine Mehrfachvererbung ersetzt, sondern eine Entkopplung schafft.
> - **D** ist die Definition des **Adapters**, nicht der Bridge.

---

> [!question] **Frage 2: Wann würde man das **Adapter-Muster** (insbesondere den Objekt-Adapter) bevorzugen?**
> - [ ] A) Wenn man die Implementierung einer Klasse komplett durch eine andere ersetzen möchte, ohne die Schnittstelle zu ändern.
> - [ ] B) Wenn man eine bestehende Klasse mit einer inkompatiblen Schnittstelle in ein neues System integrieren muss.
> - [ ] C) Wenn man die Abstraktion und Implementierung strikt voneinander trennen will, um beide unabhängig zu erweitern.
> - [ ] D) Wenn man eine Klasse mit mehreren Implementierungen versehen möchte, ohne die Vererbungshierarchie zu ändern.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Der **Adapter** wird eingesetzt, um die Zusammenarbeit zwischen Klassen mit inkompatiblen Schnittstellen zu ermöglichen. Dies ist besonders relevant für **Legacy-Systeme** oder externe Bibliotheken (siehe Folie 368–369: "Wrapper oder Adapter bieten ein Interface passend zur Client Anwendung").
> - **A** beschreibt eher das **Bridge-Muster** oder eine direkte Substitution.
> - **C** ist die Kernidee der **Bridge**, nicht des Adapters.
> - **D** ist falsch, da der Adapter keine neue Implementierungsebene schafft, sondern eine Schnittstellenanpassung vornimmt.

---
> [!question] **Frage 3: Welche der folgenden Aussagen trifft **nicht** auf das **Bridge-Muster** zu?**
> - [ ] A) Die Abstraktion delegiert Operationen an die Implementierung.
> - [ ] B) Es ermöglicht die Variation der Implementierung, ohne die Abstraktion zu ändern.
> - [ ] C) Es wird typischerweise verwendet, um Legacy-Code mit modernen Systemen zu verbinden.
> - [ ] D) Die Implementierung kann zur Laufzeit ausgetauscht werden.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> - **A** und **B** sind korrekte Beschreibungen der Bridge (Folie 346–360: "Die Abstraktion definiert und implementiert das Interface, während die eigentliche Implementierung ausgelagert wird").
> - **D** ist richtig, da die Bridge eine **dynamische Bindung** zwischen Abstraktion und Implementierung ermöglicht (z. B. durch Referenzen).
> - **C** ist falsch, da dies die **Aufgabe des Adapter-Musters** ist (Wrapper für Legacy-Code, Folie 368–369).

---
> [!question] **Frage 4: Welche der folgenden Aussagen beschreibt einen **Unterschied zwischen Bridge und Adapter**?**
> - [ ] A) Die Bridge trennt Abstraktion und Implementierung, während der Adapter zwei inkompatible Schnittstellen verbindet.
> - [ ] B) Der Adapter kann nur mit Klassen arbeiten, die eine gemeinsame Oberklasse haben, während die Bridge dies nicht erfordert.
> - [ ] C) Die Bridge wird ausschließlich zur Laufzeit eingesetzt, der Adapter nur zur Compile-Zeit.
> - [ ] D) Beide Muster verändern die Implementierung einer Klasse, aber nur der Adapter ändert auch die Schnittstelle.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: A**
>
> *Erklärung*:
> - **A** ist die zentrale Unterscheidung:
>   - **Bridge**: Entkopplung von Abstraktion und Implementierung (Folie 346–360).
>   - **Adapter**: Anpassung einer Schnittstelle an eine andere (Folie 368–369).
> - **B** ist falsch, da der **Objekt-Adapter** (im Gegensatz zum Klassen-Adapter) keine gemeinsame Oberklasse benötigt.
> - **C** ist falsch, da beide Muster sowohl zur Compile-Zeit als auch zur Laufzeit eingesetzt werden können.
> - **D** ist teilweise richtig, aber ungenau: Der Adapter **ändert die Schnittstelle**, während die Bridge **nur die Implementierung variiert**.

---
> [!question] **Frage 5: Ein Entwickler möchte eine neue Datenbank-API in ein bestehendes System integrieren, das bereits eine andere Datenbank nutzt. Die neue API hat jedoch eine vollständig andere Schnittstelle. Welches Muster sollte er verwenden, und warum?**
> - [ ] A) **Bridge**, weil es die Abstraktion (Datenbank-Operationen) von der Implementierung (API) trennt.
> - [ ] B) **Adapter**, weil er die Schnittstelle der neuen API an die bestehende Abstraktion anpasst.
> - [ ] C) **Bridge**, weil es die Implementierung zur Laufzeit austauschen kann.
> - [ ] D) **Adapter**, weil es die Abstraktion und Implementierung strikt voneinander trennt.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - Der **Adapter** ist das passende Muster, um eine **inkompatible Schnittstelle** (neue API) an die bestehende Abstraktion (Datenbank-Operationen) anzupassen (Folie 368–369: "Wrapper oder Adapter bieten ein Interface passend zur Client Anwendung").
> - **A** und **C** beschreiben das **Bridge-Muster**, das hier nicht direkt anwendbar ist, da keine Entkopplung von Abstraktion und Implementierung im Vordergrund steht.
> - **D** ist falsch, weil der Adapter **keine Abstraktion trennt**, sondern Schnittstellen anpasst.

---
Das Quiz deckt die zentralen Konzepte der **Bridge** (Entkopplung von Abstraktion/Implementierung) und des **Adapters** (Schnittstellenanpassung) ab und prüft sowohl das theoretische Verständnis als auch die Anwendung in Szenarien. Die Distraktoren sind so gewählt, dass sie typische Missverständnisse oder Verwechslungen zwischen den Mustern aufgreifen.