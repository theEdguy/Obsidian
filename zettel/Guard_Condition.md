---
id: 2228918c-1fd5-46dd-a908-c1a0a9b41a46
title: "Guard_Condition"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - zustandsmodellierung
  - entwurfsmuster
  - systemdesign
  - workflow
  - draft
source: "Klausur_Referenz"
---

# [[Guard_Condition]]

- **Kernkonzept:** Eine **Guard_Condition** (Wächterbedingung) ist eine boolesche Bedingung in [[Zustandsdiagrammen]] oder [[Aktivitätsdiagrammen]] der [[UML]], die den Übergang zwischen zwei Zuständen oder die Ausführung einer Aktion steuert. Sie wird vor dem Auslösen einer [[Transition]] evaluiert und muss `true` sein, damit die Transition stattfindet. Guard_Conditions beziehen sich typischerweise auf Attribute des Systems, Parameter von [[Trigger]]-Ereignissen oder den aktuellen [[Systemzustand]].
- **Nutzen & Zweck:** Guard_Conditions dienen der präzisen Steuerung von Abläufen in modellbasierten Systemen. Sie ermöglichen:
- **Konditionale Transitionen**: Nur wenn die Bedingung erfüllt ist, wird eine Aktion ausgeführt oder ein Zustand gewechselt.
- **Erhöhte Lesbarkeit**: Komplexe Entscheidungslogik wird explizit im Diagramm dargestellt, statt in Code versteckt.
- **Sicherheit**: Verhindert unerwünschte Zustandswechsel durch klare Vorbedingungen (z. B. Berechtigungsprüfungen).
- **Modularität**: Trennt die Auslösebedingung ([[Trigger]]) von der Bedingungsprüfung, was die Wartbarkeit verbessert.

Häufig eingesetzt in [[State_Machine]]-Implementierungen, [[Workflow-Systemen]] oder bei der Spezifikation von [[Use_Cases]].
- **Abgrenzung & Grenzen:** - **Keine Seiteneffekte**: Guard_Conditions dürfen den [[Systemzustand]] nicht verändern – sie sind reine Prüfinstanzen.
- **Keine Schleifenlogik**: Komplexe Algorithmen gehören nicht in Guard-Conditions, sondern in separate [[Methoden]] oder [[Aktionen]].
- **Kein Ersatz für Validierung**: Guard-Conditions prüfen Bedingungen, ersetzen aber keine Eingabevalidierung (z. B. in [[Schnittstellen]]).
- **Stolperfalle**: Mehrere Guard-Conditions auf einer Transition können zu unklaren Prioritäten führen (z. B. bei überlappenden Bedingungen).
- **UML-Spezifität**: Guard-Conditions sind ein UML-Konzept und nicht direkt in allen Programmiersprachen abgebildet (z. B. in Java müssen sie manuell als `if`-Bedingungen implementiert werden).
- **Beispiel / Code:** {'uml_transition': 'stateDiagram-v2\n    [*] --> Idle\n    Idle --> Processing: trigger[guardCondition] / action\n    \n    state "Processing" as Processing {\n        [*] --> Step1\n        Step1 --> Step2: [dataValid]\n        Step2 --> [*]\n    }\n    Processing --> Idle: [timeout > 10s] / notifyUser', 'java_implementation': 'public class MemberManager {\n    private boolean isAdmin;\n    private int memberCount;\n\n    public void addMember(String memberId) {\n        // Guard-Condition als if-Bedingung\n        if (isAdmin && memberCount < 100) {\n            // Action-Expression\n            memberCount++;\n            System.out.println("Mitglied hinzugefügt: " + memberId);\n        } else {\n            System.out.println("Fehler: Berechtigung oder Kapazität überschritten");\n        }\n    }\n}', 'erlaeuterung': 'Im UML-Beispiel löst der `trigger` die Transition von `Idle` zu `Processing` aus, **nur wenn** die `guardCondition` erfüllt ist. Innerhalb von `Processing` wird die Transition von `Step1` zu `Step2` durch die Guard-Condition `[dataValid]` gesteuert. In Java wird die Guard-Condition als `if`-Bedingung implementiert, die vor der Ausführung der Aktion (`memberCount++`) geprüft wird.'}
