---
type: chapter_quiz
chapter: 5
range: "326-350"
generated_at: 2026-06-20 20:47:43
tags:
  - software_engineering
  - quiz
  - chapter_quiz_5
---

# 🧠 Chapter 5 Quiz: Entwurfsmuster

**Slide Range:** 326-350

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zum Thema **Software-Engineering – Erzeugungsmuster (Kapitel 5, Slides 326–340)** im geforderten Format:

---

> [!question] **Frage 1: Welche zentrale Design-Empfehlung wird in Slide 329 durch Gamma et al. für die objektorientierte Programmierung formuliert?**
> - [ ] A) Klienten sollten direkt auf konkrete Implementierungen zugreifen, um die Performance zu optimieren.
> - [ ] B) Man sollte immer auf die Implementierung einer Klasse programmieren, um die Flexibilität zu erhöhen.
> - [ ] C) Klienten sollten nur die Schnittstelle einer Klasse kennen, nicht deren konkrete Implementierung.
> - [ ] D) Vererbung sollte bevorzugt werden, da sie zur Laufzeit dynamisch angepasst werden kann.
>
> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > Slide 329 betont das Prinzip **"Programmiere auf eine Schnittstelle hin, nicht auf eine Implementierung"**. Dies bedeutet, dass Klienten nur die Schnittstelle (z. B. ein Interface) einer Klasse kennen sollten, nicht die konkrete Implementierung. Dies ermöglicht Flexibilität und Austauschbarkeit der Objekte (z. B. durch Erzeugungsmuster wie "Fabrikmethode" oder "Abstrakte Fabrik").
> > - **A** ist falsch, da direkter Zugriff auf Implementierungen die Kapselung verletzt und die Flexibilität einschränkt.
> > - **B** widerspricht dem Prinzip, da es die Implementierung statt der Schnittstelle in den Vordergrund stellt.
> > - **D** ist falsch, da Vererbung zur Compile-Zeit festgelegt wird und nicht dynamisch zur Laufzeit angepasst werden kann (im Gegensatz zur Objektkomposition).

---

> [!question] **Frage 2: Welches Problem wird in Slide 336 durch die Verwendung von Subklassen zur Erzeugung spezifischer Visitenkarten (z. B. `FrenchAddressBook`) illustriert?**
> - [ ] A) Die Subklassen führen zu einer starken Kopplung zwischen `AddressBook` und den konkreten Label-Klassen, was die Wartbarkeit erschwert.
> - [ ] B) Die Subklassen ermöglichen eine einfache Erweiterung der Funktionalität, ohne den Code zu duplizieren.
> - [ ] C) Die Subklassen sind die effizienteste Lösung, da sie zur Compile-Zeit optimiert werden.
> - [ ] D) Die Subklassen reduzieren die Anzahl der benötigten Klassen, da sie alle Label-Typen zentral verwalten.
>
> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: A**
> >
> > *Erklärung*:
> > Slide 336 zeigt, dass die Verwendung von Subklassen (z. B. `FrenchAddressBook`) zu einem **"copy-and-paste"-Ansatz** führt, bei dem der Code für jede spezifische Implementierung (z. B. französische Adressen) dupliziert wird. Dies führt zu:
> > - **Hoher Kopplung**: Änderungen in der Basisklasse (`AddressBook`) erfordern Anpassungen in allen Subklassen.
> > - **Schlechter Wartbarkeit**: Neue Länder oder Label-Typen erfordern das Erstellen weiterer Subklassen.
> > - **Verletzung des DRY-Prinzips** (Don’t Repeat Yourself).
> > - **B** ist falsch, da die Subklassen gerade **keine** einfache Erweiterung ermöglichen, sondern Code-Duplikation erzwingen.
> > - **C** ist falsch, da Subklassen zwar zur Compile-Zeit optimiert sind, aber die Flexibilität einschränken.
> > - **D** ist falsch, da Subklassen die Anzahl der Klassen **erhöhen**, nicht reduzieren.

---
> [!question] **Frage 3: Welche Aussage zu parametrisierten Fabrikmethoden (Slide 340) trifft zu?**
> - [ ] A) Parametrisierte Fabrikmethoden können nur eine feste Anzahl von Objekttypen erzeugen.
> - [ ] B) Sie ermöglichen die dynamische Auswahl von Objekttypen zur Laufzeit, basierend auf Parametern.
> - [ ] C) Parametrisierte Fabrikmethoden sind weniger flexibel als abstrakte Fabrikmethoden, da sie keine Subklassen erfordern.
> - [ ] D) Sie ersetzen die Notwendigkeit von Interfaces, da die Parameter die Typen direkt festlegen.
>
> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Slide 340 zeigt, dass parametrisierte Fabrikmethoden (z. B. `mkAL(String type)`) die **dynamische Auswahl von Objekttypen zur Laufzeit** ermöglichen. Dies bietet folgende Vorteile:
> > - **Flexibilität**: Die Methode kann basierend auf Parametern unterschiedliche Objekte erzeugen (z. B. `FrenchAL`, `GermanAL`).
> > - **Erweiterbarkeit**: Neue Objekttypen können hinzugefügt werden, ohne die Basisklasse zu ändern (z. B. durch Überschreiben der Methode in Subklassen wie `WWAddressBook`).
> > - **Vermeidung von Code-Duplikation**: Im Gegensatz zu Subklassen (Slide 336) wird der Erzeugungsprozess zentralisiert.
> >
> > - **A** ist falsch, da parametrisierte Methoden theoretisch unbegrenzt viele Objekttypen erzeugen können.
> > - **C** ist falsch, da parametrisierte Methoden **ergänzend** zu abstrakten Fabrikmethoden eingesetzt werden können und nicht weniger flexibel sind.
> > - **D** ist falsch, da Interfaces weiterhin benötigt werden, um die Schnittstelle der erzeugten Objekte zu definieren. Die Parameter legen nur den konkreten Typ fest.

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zum Thema **Software Engineering – Fabrikmethoden und Abstrakte Fabriken** (Slides 341–350):

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt **korrekt** den Zweck der Fabrikmethode (Factory Method) nach Gamma et al.?**
> - [ ] A) Die Fabrikmethode dient ausschließlich dazu, die Erzeugung von Objekten in einer Klasse zu zentralisieren, um Code-Duplikate zu vermeiden.
> - [ ] B) Die Fabrikmethode ermöglicht es einer Klasse, die Erzeugung von Objekten an Unterklassen zu delegieren, wobei die Schnittstelle zur Objekterzeugung dediziert und überschreibbar ist.
> - [ ] C) Die Fabrikmethode ersetzt Konstruktoren vollständig und stellt sicher, dass nur eine einzige Instanz eines Produkts erzeugt wird (Singleton-Muster).
> - [ ] D) Die Fabrikmethode wird verwendet, um komplexe Objekte durch Komposition aus einfachen Objekten zusammenzusetzen (Builder-Pattern).

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Die Fabrikmethode (Factory Method) nach Gamma et al. hat laut Slide 342 den **Zweck**, eine dedizierte Schnittstelle zum Erzeugen von Objekten bereitzustellen, die von Unterklassen überschrieben werden kann. Die Erzeugung wird dabei an die Unterklassen delegiert.
> - **Option A** ist falsch, da die Fabrikmethode nicht primär der Code-Zentralisierung dient, sondern der Delegation der Objekterzeugung.
> - **Option C** ist falsch, weil die Fabrikmethode kein Singleton erzwingt (das wäre ein anderes Muster).
> - **Option D** beschreibt das **Builder-Pattern**, nicht die Fabrikmethode.

---

> [!question] **Frage 2: Warum ist die Verwendung einer **abstrakten Fabrik (Abstract Factory)** in dem gegebenen Beispiel (Slides 346–349) vorteilhaft gegenüber der reinen Fabrikmethode (Slide 341)?**
> - [ ] A) Die abstrakte Fabrik ermöglicht die Erzeugung **kohärenter Produktfamilien**, während die Fabrikmethode nur einzelne Objekte erzeugen kann.
> - [ ] B) Die abstrakte Fabrik ist einfacher zu implementieren, da sie keine Schnittstellen oder Vererbung erfordert.
> - [ ] C) Die abstrakte Fabrik garantiert, dass alle erzeugten Objekte denselben Typ haben (z. B. nur `AddressLabel`).
> - [ ] D) Die abstrakte Fabrik ersetzt die Notwendigkeit von Konstruktoren vollständig und macht Klassen zu reinen Fabriken.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: A**
>
> *Erklärung*:
> Die abstrakte Fabrik (Slide 346) definiert eine Schnittstelle zur Erzeugung **mehrerer verwandter Objekte** (z. B. `AddressLabel`, `TelephoneLabel`, `BusinessLabel`), die zusammen eine Produktfamilie bilden. Dies stellt sicher, dass die Objekte **kohärent** sind (z. B. alle deutschen Labels oder alle französischen Labels).
> - **Option B** ist falsch, da die abstrakte Fabrik zusätzliche Abstraktionsebenen (Schnittstellen, Implementierungsklassen) erfordert.
> - **Option C** ist falsch, weil die abstrakte Fabrik **verschiedene Produkttypen** erzeugen kann (nicht nur einen Typ).
> - **Option D** ist falsch, da Konstruktoren weiterhin benötigt werden (z. B. in `GermanLabelFactory`).

---
> [!question] **Frage 3: Welche der folgenden Aussagen beschreibt **korrekt** die Variante II der abstrakten Fabrik (Slide 350), bei der die Fabrikmethoden in den Produkten implementiert werden?**
> - [ ] A) In Variante II wird die Erzeugung der Produkte vollständig in die abstrakte Fabrikklasse verlagert, während die konkreten Fabriken nur noch Delegationsmethoden bereitstellen.
> - [ ] B) Variante II ermöglicht es, **unterschiedliche Varianten von Produkten** (z. B. RFC3966-Telefonnummern) bereits in der abstrakten Fabrik zu definieren, ohne die konkreten Fabriken anzupassen.
> - [ ] C) Variante II ersetzt die abstrakte Fabrik durch eine konkrete Fabrikklasse, die alle Produktvarianten direkt instanziiert.
> - [ ] D) Variante II ist nur anwendbar, wenn alle Produkte denselben Typ haben (z. B. nur `AddressLabel`).

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> In Variante II (Slide 350) werden die **Fabrikmethoden in den Produkten selbst** implementiert (z. B. `GermanAL.mkAddressLabel()`). Die abstrakte Fabrik (`LabelFactory`) delegiert die Erzeugung an diese Produktmethoden. Dadurch können **unterschiedliche Varianten** (z. B. RFC3966-Telefonnummern) bereits in der abstrakten Fabrik definiert werden, ohne die konkreten Fabriken (`GermanLabelFactory`, `AmericanLabelFactory`) anzupassen.
> - **Option A** ist falsch, weil die Erzeugung in Variante II **nicht** in der abstrakten Fabrik, sondern in den Produkten stattfindet.
> - **Option C** ist falsch, da Variante II weiterhin eine abstrakte Fabrik verwendet.
> - **Option D** ist falsch, weil Variante II für **mehrere Produkttypen** (z. B. `AddressLabel`, `TelephoneLabel`) funktioniert.

---
Das Quiz deckt damit die zentralen Konzepte der **Fabrikmethode**, **abstrakten Fabrik** und deren Varianten ab und prüft sowohl theoretisches Verständnis als auch praktische Anwendung. Die Fragen sind auf akademischem Niveau und erfordern vertieftes Wissen aus den Slides.