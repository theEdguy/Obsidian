---
id: f2538d50-5e9d-4f88-88ff-5941546cd76c
title: "Schleife"
date: 2026-06-23
tags:
  - software_engineering
  - uml-fragment
  - kontrollfluss
  - draft
source: "software_engineering_kapitel_13"
---

# [[Schleife]]

- **Kernkonzept:** Eine Schleife in UML-Interaktionsdiagrammen ist ein Fragment, das iterative Abläufe modelliert, bei denen eine oder mehrere Nachrichten wiederholt ausgeführt werden, bis eine bestimmte Bedingung erfüllt ist.
- **Nutzen & Zweck:** Schleifen existieren, um wiederkehrende Prozesse oder Abläufe in der Softwaremodellierung darzustellen. Sie lösen das Problem, repetitive Interaktionen zwischen Objekten ohne redundante Darstellung im Diagramm abzubilden und ermöglichen so eine klare, kompakte Visualisierung von Kontrollflüssen mit Wiederholungen.
- **Abgrenzung & Grenzen:** Schleifen sollten nicht genutzt werden, wenn der Ablauf keine Wiederholung erfordert oder wenn die Iterationslogik zu komplex ist, um sie im Diagramm verständlich abzubilden. Alternativen wie separate Sequenzdiagramme für jeden Iterationsschritt sind dann vorzuziehen. Im Gegensatz zu einfachen Nachrichtenfolgen oder bedingten Fragmenten (z. B. 'alt') eignen sich Schleifen ausschließlich für zyklische Prozesse.
- **Beispiel / Code:** ```java
// Beispiel für eine Schleife in einem UML-Sequenzdiagramm (Pseudocode-Darstellung)
loop(1, 10) {
    benutzer -> system: Anfrage senden();
    system -> datenbank: Daten abrufen();
    datenbank --> system: Ergebnis zurückgeben();
    system --> benutzer: Antwort anzeigen();
}
```

// UML-Fragment-Notation (textuell):
loop(min, max) [Bedingung]
    [Nachrichtenfolge]
end

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c3
- **Vorgänger / Parent:** [[Nachrichtenfragment]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
