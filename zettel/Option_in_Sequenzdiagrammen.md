---
id: d8cc8846-866a-46fb-a282-83ccf96b124c
title: "Option_Coregion_und_Negation_in_Sequenzdiagrammen"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - kontrollstruktur
  - bedingung
  - nebenläufigkeit
  - modellierung
  - fehlerbehandlung
  - draft
source: "SWE Slides (Folien 301-315)"
---

# [[Option_Coregion_und_Negation_in_Sequenzdiagrammen]]

- **Kernkonzept:** In [[Sequenzdiagramm|Sequenzdiagrammen]] ermöglichen [[Option_in_Sequenzdiagrammen|Optionen]] die Modellierung von [[Ablauf|Abläufen]], die nur unter bestimmten [[Bedingung|Bedingungen]] ausgeführt werden, während [[Coregion_in_Sequenzdiagrammen|Coregionen]] Bereiche kennzeichnen, in denen [[Nachricht|Nachrichten]] in beliebiger Reihenfolge oder [[Parallelität_in_Sequenzdiagrammen|parallel]] ablaufen können. Die [[Negation_in_Sequenzdiagrammen|Negation]] ergänzt dies durch die Darstellung ungültiger oder unerwünschter [[Interaktion|Interaktionen]], etwa zur Spezifikation von [[Fehlerfall|Fehlerfällen]] oder [[Verbot|Verboten]].
- **Nutzen & Zweck:** Die [[Option_in_Sequenzdiagrammen|Option]] erhöht die Präzision bei der Modellierung bedingter [[Ablauf|Abläufe]], z. B. für [[Validierung|Validierungen]] oder [[Sonderfall|Sonderfälle]], während die [[Coregion_in_Sequenzdiagrammen|Coregion]] die Flexibilität für [[Nebenläufigkeit|nebenläufige]] oder unabhängige [[Operation|Operationen]] bietet. Die [[Negation_in_Sequenzdiagrammen|Negation]] dient der klaren Abgrenzung unerlaubter [[Interaktion|Interaktionen]] und unterstützt die Definition robuster [[Spezifikation|Spezifikationen]], insbesondere in [[Fehlerbehandlung|Fehlerbehandlungsszenarien]]. Alle drei [[Kontrollstruktur|Kontrollstrukturen]] erweitern die Ausdrucksstärke von [[Sequenzdiagramm|Sequenzdiagrammen]] für komplexe [[Systemverhalten|Systemverhalten]] und [[Anforderung|Anforderungen]].
- **Abgrenzung & Grenzen:** Die [[Option_in_Sequenzdiagrammen|Option]] ist ungeeignet für [[Ablauf|Abläufe]], die immer ausgeführt werden müssen – hier sind direkte [[Nachricht|Nachrichten]] vorzuziehen. Für [[Bedingung|Bedingungen]] mit mehreren Zweigen sollte stattdessen eine [[Alternative_in_Sequenzdiagrammen|Alternative]] verwendet werden. Die [[Coregion_in_Sequenzdiagrammen|Coregion]] beeinträchtigt die Lesbarkeit, wenn die [[Unabhängigkeit|Unabhängigkeit]] der [[Nachricht|Nachrichten]] nicht offensichtlich ist, und sollte nicht für streng sequenzielle [[Ablauf|Abläufe]] genutzt werden. Die [[Negation_in_Sequenzdiagrammen|Negation]] ist kein Ersatz für gültige [[Ablauf|Abläufe]] und kann missverstanden werden, wenn der Kontext unklar ist. Alle drei Konstrukte erhöhen die Komplexität des Diagramms und erfordern eine Abwägung zwischen Präzision und Verständlichkeit, insbesondere in [[Modellierung|Modellierungsszenarien]] mit hohen [[Qualitätsanforderung|Qualitätsanforderungen]].
- **Beispiel / Code:** ```uml
"Option" für bedingte Ausführung:
opt [voll == true]
    :User -> Glas: leeren()
end

"Coregion" für unabhängige/parallele Nachrichten:
coregion
    :System -> MemberField: getMember()
    :System -> DepartmentField: getDepartment()
endcoregion

"Negation" für unerwünschte Interaktionen:
neg
    :User -> Glas: leeren()
end
```
