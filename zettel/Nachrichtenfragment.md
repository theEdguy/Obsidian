---
id: 3032129c-34c3-4a7d-95b3-dc6bd978a6e5
title: "Nachrichtenfragment"
date: 2026-06-23
tags:
  - software_engineering
  - uml-element
  - kontrollfluss
  - draft
source: "software_engineering_kapitel_13"
---

# [[Nachrichtenfragment]]

- **Kernkonzept:** Ein Nachrichtenfragment in UML-Interaktionsdiagrammen ist ein strukturiertes Element, das spezielle Kontrollflüsse wie Alternativen, Schleifen, Parallelität oder Ausnahmebehandlungen kapselt. Es ermöglicht die Darstellung komplexer Abläufe innerhalb von Sequenz- oder Kommunikationsdiagrammen durch vordefinierte Operatoren wie 'alt', 'loop', 'par' oder 'break'.
- **Nutzen & Zweck:** Nachrichtenfragmente existieren, um die Lesbarkeit und Präzision von Interaktionsdiagrammen zu erhöhen, indem sie wiederkehrende oder bedingte Ablaufmuster standardisiert abbilden. Sie lösen das Problem, dass einfache Nachrichtenfolgen bei komplexen Bedingungen, Wiederholungen oder parallelen Prozessen unübersichtlich werden. Durch die Fragmentierung wird der Kontrollfluss modularisiert und die Semantik des Systems klarer kommuniziert, was insbesondere bei der Dokumentation und Analyse von Use Cases hilft.
- **Abgrenzung & Grenzen:** Nachrichtenfragmente sollten nicht genutzt werden, wenn der Kontrollfluss linear und einfach ist, da sie dann unnötige Komplexität einführen. Alternativen wie einfache Nachrichtenfolgen oder Zustandsdiagramme sind in solchen Fällen vorzuziehen. Fragmente unterscheiden sich von reinen Nachrichten durch ihre explizite Kontrolllogik – sie sind keine physischen Objekte oder Methodenaufrufe, sondern logische Strukturen. Bei sehr tief verschachtelten Fragmenten kann die Verständlichkeit leiden, weshalb eine Aufteilung in mehrere Diagramme oder die Verwendung von Referenzfragmenten ('ref') ratsam ist.
- **Beispiel / Code:** ```java
// Beispiel für ein Sequenzdiagramm mit Nachrichtenfragmenten (als UML-Notation):
// Fragment 'alt' (Alternative):
alt [Konto gedeckt] {
    Konto -> Bank: Geld abheben(Betrag)
    Bank -> Konto: Bestätigung
} else [Konto nicht gedeckt] {
    Bank -> Konto: Ablehnung
}

// Fragment 'loop' (Schleife):
loop (1, 10) {
    Benutzer -> Drucker: Seite drucken
}

// Fragment 'par' (Parallelität):
par {
    Server1 -> Datenbank: Anfrage A
    ---
    Server2 -> Datenbank: Anfrage B
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c
- **Vorgänger / Parent:** [[Sequenzdiagramm]]
- **Folgezettel / Unterzettel:**
  - [[Alternative]]
  - [[Option]]
  - [[Schleife]]
  - [[Parallelität]]
  - [[Abbruch]]
- **Querverweise:** keine
