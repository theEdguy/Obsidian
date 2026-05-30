---
id: 3c9b3da0-df97-49f8-9acd-2ab1158752cb
title: "Kontrollstrukturen_in_Sequenzdiagrammen"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - kontrollstruktur
  - iteration
  - bedingung
  - fehlerbehandlung
  - modellierung
  - draft
source: "SWE Slides (Folien 301-315)"
---

# [[Kontrollstrukturen_in_Sequenzdiagrammen]]

- **Kernkonzept:** In [[Sequenzdiagramm|Sequenzdiagrammen]] modellieren [[Kontrollstruktur|Kontrollstrukturen]] wie [[Schleife_in_Sequenzdiagrammen|Schleifen]], [[Alternative_in_Sequenzdiagrammen|Alternativen]] und [[Abbruch_in_Sequenzdiagrammen|Abbruchfragmente]] iterative, bedingte oder vorzeitige [[Ablauf|Abläufe]], um komplexe [[Interaktion|Interaktionen]] zwischen [[Komponente|Komponenten]] darzustellen. Sie ermöglichen die Abbildung von [[Iteration|Iterationen]], [[Verzweigung|Verzweigungen]] und [[Ausnahmebehandlung|Ausnahmebehandlungen]] basierend auf [[Bedingung|Bedingungen]] oder definierten Wiederholungen.
- **Nutzen & Zweck:** [[Kontrollstruktur|Kontrollstrukturen]] in [[Sequenzdiagramm|Sequenzdiagrammen]] dienen dazu, dynamische [[Ablauf|Abläufe]] präzise zu modellieren. [[Schleife_in_Sequenzdiagrammen|Schleifen]] eignen sich für das Durchlaufen von [[Liste|Listen]], das wiederholte Ausführen von [[Operation|Operationen]] oder das Abarbeiten von [[Element|Elementen]] bis eine Abbruchbedingung erfüllt ist. [[Alternative_in_Sequenzdiagrammen|Alternativen]] ermöglichen die Darstellung von [[Verzweigung|Verzweigungen]], z. B. für [[Fehlerbehandlung|Fehlerbehandlungen]], [[Entscheidung|Entscheidungen]] basierend auf [[Attribut|Attributwerten]] oder unterschiedliche [[Ablauf|Abläufe]] je nach [[Zustand]]. [[Abbruch_in_Sequenzdiagrammen|Abbruchfragmente]] ergänzen diese Möglichkeiten, indem sie das vorzeitige Beenden eines [[Ablauf|Ablaufs]] bei [[Fehler|Fehlern]] oder [[Ausnahme|Ausnahmen]] modellieren, was insbesondere für die [[Ausnahmebehandlung|Ausnahmebehandlung]] in [[System|Systemen]] mit hohen [[Zuverlässigkeit|Zuverlässigkeitsanforderungen]] essenziell ist.
- **Abgrenzung & Grenzen:** [[Kontrollstruktur|Kontrollstrukturen]] in [[Sequenzdiagramm|Sequenzdiagrammen]] sind nicht für einfache, lineare [[Ablauf|Abläufe]] ohne Wiederholungen, [[Bedingung|Bedingungen]] oder vorzeitige Beendigungen geeignet. Für solche Fälle reichen einfache [[Nachricht|Nachrichten]] ohne [[Fragment_in_Sequenzdiagrammen|Fragmente]] aus. [[Schleife_in_Sequenzdiagrammen|Schleifen]] sollten vermieden werden, wenn keine [[Iteration]] erforderlich ist, während [[Alternative_in_Sequenzdiagrammen|Alternativen]] überflüssig sind, wenn keine [[Verzweigung]] vorliegt. [[Abbruch_in_Sequenzdiagrammen|Abbruchfragmente]] sind ungeeignet für [[Ablauf|Abläufe]], die immer vollständig durchlaufen werden müssen, und können die Lesbarkeit beeinträchtigen, wenn zu viele [[Abbruch_in_Sequenzdiagrammen|Abbruchbedingungen]] modelliert werden. Für einfache [[Bedingung|Bedingungen]] ohne Verzweigung kann stattdessen das [[Option_in_Sequenzdiagrammen|Option-Fragment]] genutzt werden. Die Wahl der richtigen [[Kontrollstruktur]] hängt vom spezifischen [[Anwendungsfall]] und der Komplexität des modellierten [[Ablauf|Ablaufs]] ab.
- **Beispiel / Code:** ```uml
"Beispiel für eine Schleife (Iteration):"
loop (1, n)
    :Shop -> Order: getItem([[Index|i]])
    :Order -> Item: getTitle()
    :Item -> Worker: getIt(title, qty)
end

"Beispiel für eine Alternative (Verzweigung):"
alt [y > x]
    :Facade -> ClassA: op([[Parameter|y]])
[else]
    :Facade -> ClassB: op([[Parameter|y]])
end

"Beispiel für einen Abbruch (Ausnahmebehandlung):"
break [Panik]
    :Student -> Blatt: neuSammeln()
    :Blatt -> System: logError()
end
```
