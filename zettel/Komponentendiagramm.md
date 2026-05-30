---
id: fa334a19-acc3-4f2e-97b5-4ffdc9d6b254
title: "Komponentendiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - softwarearchitektur
  - modularisierung
  - schnittstellen
  - schichtenarchitektur
  - draft
source: "Klausur_Referenz"
---

# [[Komponentendiagramm]]

- **Kernkonzept:** Ein [[Komponentendiagramm]] ist eine strukturelle [[UML]]-Diagrammart, die die Organisation und Abhängigkeiten von [[Komponenten]] in einem Softwaresystem modelliert. Es zeigt, wie Komponenten über [[Schnittstellen]] (Interfaces) und Ports miteinander interagieren, ohne deren interne Implementierung offenzulegen. Komponenten können dabei physikalische (z. B. ausführbare Dateien) oder logische Einheiten (z. B. Module) repräsentieren. Das Diagramm visualisiert Konnektoren wie Delegation-Konnektoren oder Assembly-Konnektoren, die die Kommunikation zwischen Komponenten regeln.
- **Nutzen & Zweck:** Komponentendiagramme dienen der Dokumentation und Planung von [[Softwarearchitektur]] auf hoher Abstraktionsebene. Sie helfen, die Modularität eines Systems zu verdeutlichen, indem sie die Verantwortlichkeiten einzelner Komponenten und deren Schnittstellen klar trennen. Dies fördert die Wiederverwendbarkeit, Wartbarkeit und Skalierbarkeit des Systems. Zudem unterstützen sie die Kommunikation zwischen Entwicklern, Architekten und Stakeholdern, indem sie die Systemstruktur visuell verständlich darstellen. In der [[Schichtenarchitektur]] (z. B. [[Three_Tier_Architecture]]) sind sie besonders nützlich, um die Trennung von Schichten (z. B. Präsentation, Logik, Daten) und deren Interaktionen zu modellieren.
- **Abgrenzung & Grenzen:** Ein Komponentendiagramm unterscheidet sich von anderen UML-Diagrammen wie dem [[Klassendiagramm]] oder [[Paketdiagramm]] durch seinen Fokus auf die *physische oder logische Verteilung* von Komponenten und deren Schnittstellen, nicht auf Klassen oder Paketstrukturen. Typische Stolpersteine sind:
- **Überladung mit Details**: Komponentendiagramme sollten keine internen Implementierungsdetails (z. B. Klassen oder Methoden) zeigen, sondern sich auf die externe Sicht beschränken.
- **Unklare Schnittstellen**: Schnittstellen müssen präzise definiert sein, um Missverständnisse in der Kommunikation zwischen Komponenten zu vermeiden.
- **Schichtenübergreifende Abhängigkeiten**: Bei der Verbindung von Komponenten unterschiedlicher Schichten (z. B. UI und Datenbank) muss auf lose Kopplung geachtet werden, um die [[Separation_of_Concerns]] zu wahren.
- **Delegation vs. direkte Verbindung**: Delegation-Konnektoren (z. B. zwischen Ports) müssen korrekt modelliert werden, um die Weiterleitung von Anfragen zwischen Komponenten abzubilden.
- **Beispiel / Code:** {'beschreibung': 'Textuelle UML-Beschreibung des Beispiels aus dem Kontext (Aufgabe a, 3 Punkte):', 'mermaid_syntax': '```mermaid\ncomponentDiagram\n    component A {\n        port P\n    }\n    component B {\n        port Q\n        port R\n    }\n    component C {\n        port R\n    }\n\n    A --> P : erwartet Interface I\n    B --> Q : stellt Interface I bereit\n    B --> R : bezieht Interface I\n    C --> R : stellt Interface I bereit\n\n    B -[hidden]-> C : Delegation-Konnektor\n```', 'erlaeuterung': 'Die Komponente A erwartet am Port P das Interface I, das von Komponente B am Port Q bereitgestellt wird. B bezieht dieses Interface jedoch über einen Delegation-Konnektor vom Port R der Komponente C. Das Diagramm zeigt:\n- Die Abhängigkeit von A zu B über Interface I.\n- Die interne Weiterleitung von C zu B über Port R und Q.\n- Die lose Kopplung durch Schnittstellen, die eine flexible Austauschbarkeit der Komponenten ermöglicht.'}
