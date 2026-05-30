---
id: d8fd0f9e-c92c-4fee-b273-f073bccf41e7
title: "Kunde_im_Software_Engineering"
date: 2026-05-30
tags:
  - software_engineering
  - agile_entwicklung
  - use_case
  - stakeholder_management
  - anforderungsanalyse
  - uml
  - kundenzentrierung
  - draft
source: "Klausur_Referenz"
---

# [[Kunde_im_Software_Engineering]]

- **Kernkonzept:** Ein [[Kunde]] im Kontext des [[Software_Engineering]] ist eine natürliche oder juristische Person, die ein [[Softwareprodukt]] oder eine Dienstleistung in Auftrag gibt, nutzt oder davon profitiert. Der Kunde ist zentraler Stakeholder in der [[agilen_Entwicklung]] und definiert durch seine Anforderungen (z. B. [[Use_Case]]s) die Funktionalität und Qualität des Systems. Im Gegensatz zum [[Endbenutzer]] kann der Kunde auch eine Organisation oder ein interner Auftraggeber sein, der die Entwicklung steuert oder finanziert.
- **Nutzen & Zweck:** 1. **Anforderungsdefinition**: Der Kunde liefert die Grundlage für [[Anforderungsanalyse]] und [[Produktvision]], indem er Use Cases, User Stories oder [[Akzeptanzkriterien]] formuliert. 
2. **Kundenzentrierte Entwicklung**: Durch kontinuierliches Feedback (z. B. in [[Sprint_Review]]s) wird sichergestellt, dass das Produkt den tatsächlichen Bedürfnissen entspricht. 
3. **Wertschöpfung**: Eine klare Kundenorientierung reduziert Fehlentwicklungen und erhöht die [[Benutzerakzeptanz]]. 
4. **Prozessoptimierung**: Wie im Beispiel der Bestell-App können kundenspezifische Pain Points (z. B. unpräzise Lieferadressen) durch digitale Lösungen adressiert werden, was die [[Kundenbindung]] und Effizienz steigert.
- **Abgrenzung & Grenzen:** 1. **Kunde vs. Endbenutzer**: Nicht jeder Kunde ist direkter Nutzer des Systems (z. B. ein Einkaufsleiter, der eine App für Mitarbeiter bestellt). 
2. **Anforderungsambiguität**: Kunden formulieren Anforderungen oft vage (z. B. "benutzerfreundlich"), was zu Missverständnissen führt. Hier helfen Techniken wie [[User_Story_Mapping]] oder [[Prototyping]]. 
3. **Konfliktpotenzial**: Unterschiedliche Kundengruppen (z. B. Vertrieb vs. Logistik) haben divergierende Prioritäten, die durch [[Stakeholder_Analyse]] und [[Priorisierungstechniken]] (z. B. [[MoSCoW]]) aufgelöst werden müssen. 
4. **Technische Grenzen**: Kundenwünsche kollidieren manchmal mit Machbarkeit (z. B. Echtzeit-Tracking in Gebieten ohne Netzabdeckung). Hier ist transparente Kommunikation über [[Nicht-funktionale_Anforderungen]] essenziell.
- **Beispiel / Code:** {'beschreibung': 'UML-Use-Case-Diagramm (Mermaid-Syntax) für die Bestell-App aus dem Kontext:', 'diagramm': '```mermaid\nuseCaseDiagram\n    actor Kunde as "Kunde (Mitarbeiter)"\n    actor Vertrieb as "Vertrieb (Intern)"\n    actor Logistik as "Logistik (Intern)"\n    \n    Kunde --> (Bestellung aufgeben)\n    Kunde --> (Bestellstatus einsehen)\n    Kunde --> (Aufstellort mit Foto dokumentieren)\n    Kunde --> (Ansprechpartner hinterlegen)\n    \n    Vertrieb --> (Kundenfeedback analysieren)\n    Vertrieb --> (Bestellprozess optimieren)\n    \n    Logistik --> (Lieferadresse prüfen)\n    Logistik --> (Aufstellbedingungen validieren)\n    \n    (Bestellung aufgeben) ..> (Bestellstatus einsehen) : <<include>>\n    (Bestellung aufgeben) ..> (Aufstellort mit Foto dokumentieren) : <<extend>>\n```'}
