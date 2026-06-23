---
id: 1871b805-1f70-4496-8a73-bd401274bf9e
title: "OCL"
date: 2026-06-24
tags:
  - software_engineering
  - modellierung
  - sprache
  - standard
  - modellierungssprache
  - draft
source: "software_engineering_kapitel_15"
---

# [[OCL]]

- **Kernkonzept:** OCL (Object Constraint Language) ist eine [[formale_Sprache|formale Sprache]] zur Spezifikation von [[Bedingung|Bedingungen]], [[Invariante|Invarianten]], Vor- und Nachbedingungen in [[UML|UML-Modellen]], die nicht durch grafische [[Notation|Notationen]] allein ausgedrückt werden können. Sie ermöglicht präzise Definitionen von [[Regel|Regeln]], die [[Objekt|Objekte]] und ihre [[Beziehung|Beziehungen]] in einem [[Modell]] erfüllen müssen, ohne dabei die [[Implementierung]] vorwegzunehmen.
- **Nutzen & Zweck:** OCL existiert, um [[Mehrdeutigkeit|Mehrdeutigkeiten]] in [[UML|UML-Modellen]] zu vermeiden und komplexe logische [[Bedingung|Bedingungen]] oder [[Geschäftsregel|Geschäftsregeln]] exakt zu formulieren. Sie löst das Problem, dass grafische [[UML|UML-Diagramme]] oft nicht ausreichen, um alle [[Anforderung|Anforderungen]] an ein [[System]] vollständig und unmissverständlich zu beschreiben. Durch OCL können [[Entwickler]] und [[Modellierer]] sicherstellen, dass [[Modell|Modelle]] konsistent, korrekt und maschinell überprüfbar sind, was insbesondere in der [[objektorientierte_Analyse|objektorientierten Analyse]] und [[Designphase|Designphase]] entscheidend ist. Zudem stellt OCL sicher, dass ein [[Modell]] später in [[Code]] umgesetzt werden kann, ohne dass wichtige [[Randbedingung|Randbedingungen]] verloren gehen.
- **Abgrenzung & Grenzen:** OCL sollte nicht genutzt werden, wenn die [[Modellierung]] ausschließlich einfache [[Struktur|Strukturen]] oder [[Ablauf|Abläufe]] ohne komplexe [[Bedingung|Bedingungen]] erfordert, da der Aufwand für die Spezifikation dann unnötig hoch ist. Im Gegensatz zu [[Programmiersprache|Programmiersprachen]] wie [[Java]] oder [[Python]] ist OCL keine ausführbare Sprache, sondern dient ausschließlich der [[Modellierung]] und [[Dokumentation]]. Alternativen wie informelle [[Kommentar|Kommentare]] oder [[Pseudocode]] sind weniger präzise, aber schneller umsetzbar, wenn keine formale Überprüfung erforderlich ist. Zudem eignet sich OCL nicht für die Beschreibung dynamischer [[Ablauf|Abläufe]] oder [[Algorithmus|Algorithmen]], hier sind [[Aktivitätsdiagramm|Aktivitäts-]] oder [[Sequenzdiagramm|Sequenzdiagramme]] besser geeignet. OCL ist auch nicht für die Kommunikation mit [[Nicht-Techniker|Nicht-Technikern]] geeignet, da die formale [[Syntax]] oft schwer verständlich ist. In solchen Fällen sind natürliche Sprache oder einfache [[UML|UML-Notizen]] vorzuziehen, auch wenn sie weniger präzise sind.
- **Beispiel / Code:** ```ocl
-- Invariante: Ein Mitglied muss ab 18 Jahren Vollmitglied sein
context Mitglied inv:
    self.alter >= 18 implies self.istVollmitglied = true

-- Vor- und Nachbedingungen für die Operation 'beitritt' in der Klasse 'Verein'
context Verein::beitritt(mitglied: Mitglied): Boolean
    pre: mitglied.alter >= 16
    post: mitglied.oclIsTypeOf(Vollmitglied) or mitglied.oclIsTypeOf(Jugendmitglied)

-- Vor- und Nachbedingungen für die Operation 'hinzufuegenMitglied'
context Verein::hinzufuegenMitglied(m: Mitglied): Boolean
    pre: m.istGueltig()
    post: self.mitglieder->includes(m) and result = true
```

*Erklärung:*
- Die erste [[Invariante]] definiert eine Regel für die [[Klasse]] `Mitglied`: Wenn das Alter mindestens 18 ist, muss das Attribut `istVollmitglied` wahr sein.
- Die zweite Regel beschreibt eine Vorbedingung (`pre`) und Nachbedingung (`post`) für die Operation `beitritt` im `Verein`.
- Die dritte Regel zeigt eine weitere Vor- und Nachbedingung für die Operation `hinzufuegenMitglied`, wobei die Nachbedingung sicherstellt, dass das neue Mitglied in der [[Liste]] `mitglieder` enthalten ist und der Rückgabewert `true` ist.
