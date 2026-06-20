---
type: quiz
chapter: 5
subtopic: "Entwurfsmuster"
format: callout
generated_at: 2026-06-20 20:47:21
tags:
  - software_engineering
  - quiz
  - chapter_5
---

# 🧠 Quiz: Entwurfsmuster

**Kapitel:** 5
**Details:** 

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zum Thema **Entwurfsmuster** im geforderten Format:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt am besten die **Fabrikmethode** als Entwurfsmuster?**
> - [ ] A) Sie ermöglicht die direkte Erzeugung von Objekten durch eine zentrale Klasse, um die Kopplung zwischen Client und konkreten Klassen zu erhöhen.
> - [ ] B) Sie delegiert die Objekterzeugung an eine dedizierte Schnittstelle, die von Unterklassen überschrieben werden kann, um Flexibilität in der Objektkreation zu ermöglichen.
> - [ ] C) Sie kapselt eine Familie verwandter Algorithmen und macht diese austauschbar, ohne die Client-Klassen zu ändern.
> - [ ] D) Sie definiert eine Familie von Algorithmen, die in einer Hierarchie von Klassen implementiert werden, wobei jede Klasse eine spezifische Variante des Algorithmus bereitstellt.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Die **Fabrikmethode** (Factory Method) ist ein **Erzeugungsmuster**, das eine **dedizierte Schnittstelle** zur Objekterzeugung bereitstellt. Diese Schnittstelle kann von Unterklassen überschrieben werden, um die konkrete Objekterzeugung zu steuern. Dadurch wird die **Abhängigkeit des Clients von konkreten Klassen reduziert** und die **Flexibilität erhöht** (z. B. bei der Erweiterung um neue Objekttypen).
> - **Option A** ist falsch, weil die Fabrikmethode gerade die Kopplung **vermindert**, nicht erhöht.
> - **Option C** beschreibt das **Strategie-Muster** (Algorithmenaustausch), nicht die Fabrikmethode.
> - **Option D** bezieht sich auf das **Template-Methoden-Muster** (Algorithmen-Hierarchie), nicht auf die Objekterzeugung.

---

> [!question] **Frage 2: Welche der folgenden Aussagen trifft auf die **Verantwortungszuweisung** im Entwurfsmuster-Kontext zu?**
> - [ ] A) Verantwortlichkeiten sollten immer direkt in der Klasse implementiert werden, die sie benötigt, um die Kohäsion zu maximieren.
> - [ ] B) Verantwortlichkeiten für "Wissen" (z. B. Daten speichern) und "Tun" (z. B. Berechnungen durchführen) sollten immer in derselben Klasse gebündelt werden, um die Wartbarkeit zu verbessern.
> - [ ] C) Verantwortlichkeiten können delegiert werden, wobei eine Klasse entweder selbst handelt oder die Aufgabe an eine andere Klasse weitergibt, um die Komplexität zu verteilen.
> - [ ] D) Verantwortlichkeiten sollten ausschließlich über Schnittstellen definiert werden, um die Implementierungsdetails zu verbergen, unabhängig von der tatsächlichen Funktionalität.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Die **Verantwortungszuweisung** ist ein zentrales Prinzip beim Entwurf von Klassen und Schnittstellen. Eine Klasse kann:
> - **Verantwortlichkeiten für "Tun"** (z. B. eine Methode ausführen) entweder selbst übernehmen oder an eine andere Klasse delegieren.
> - **Verantwortlichkeiten für "Wissen"** (z. B. Daten speichern oder berechnen) haben, wobei diese klar zugeordnet sein müssen.
> - **Option A** ist falsch, weil Verantwortlichkeiten **nicht immer in einer Klasse gebündelt** werden sollten (das würde zu hoher Kopplung führen).
> - **Option B** ist falsch, weil "Wissen" und "Tun" oft in **unterschiedlichen Klassen** liegen sollten (z. B. ein `Repository` speichert Daten, eine `Service`-Klasse führt Berechnungen durch).
> - **Option D** ist falsch, weil Verantwortlichkeiten **nicht ausschließlich über Schnittstellen** definiert werden, sondern auch durch konkrete Implementierungen.

---
> [!question] **Frage 3: Ein Softwareteam entwirft ein System zur Verwaltung von Mitgliedern eines Vereins. Welches Entwurfsmuster eignet sich am besten, um die verschiedenen **Zustände** eines Mitglieds (z. B. "Neu", "Aktiv", "Gesperrt") zu modellieren, und warum?**
> - [ ] A) **Singleton**: Weil nur eine Instanz eines Mitglieds pro Zustand existieren darf.
> - [ ] B) **State**: Weil es die Zustandsabhängigkeiten kapselt und das Verhalten dynamisch an den aktuellen Zustand anpasst.
> - [ ] C) **Observer**: Weil Änderungen im Zustand eines Mitglieds an andere Komponenten propagiert werden müssen.
> - [ ] D) **Composite**: Weil Mitglieder hierarchisch in Gruppen (z. B. "Vorstand", "Abteilungsleiter") organisiert werden können.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Das **State-Muster** ist ideal für die Modellierung von **Zustandsabhängigkeiten**, da es:
> - Jeden Zustand als **eigenständige Klasse** kapselt (z. B. `ActiveMemberState`, `BannedMemberState`).
> - Das Verhalten des Objekts **dynamisch an den aktuellen Zustand anpasst** (z. B. unterschiedliche Methodenaufrufe je nach Zustand).
> - Die **Zustandsübergänge** explizit macht (z. B. von "Neu" zu "Aktiv" durch eine Methode wie `activate()`).
>
> - **Option A** ist falsch, weil das **Singleton-Muster** die **Einzelinstanz** eines Objekts sicherstellt, nicht die Zustandsverwaltung.
> - **Option C** ist falsch, weil der **Observer** für die **Benachrichtigung** von Änderungen zuständig ist, nicht für die Zustandslogik selbst.
> - **Option D** ist falsch, weil das **Composite-Muster** für **hierarchische Strukturen** (z. B. Baumstrukturen) verwendet wird, nicht für Zustände.

---
Das Quiz prüft **Verständnis** (Frage 1: Definition der Fabrikmethode), **Anwendung** (Frage 2: Verantwortungszuweisung in der Praxis) und **Abgrenzung von Mustern** (Frage 3: State vs. andere Muster). Die Distraktoren sind fachlich plausibel, aber eindeutig falsch.