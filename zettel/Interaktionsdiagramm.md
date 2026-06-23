---
id: 7ccb8ed5-d638-4f92-9747-e76909a1c8cf
title: "Interaktionsdiagramm"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - dynamische_analyse
  - modellierungstechnik
  - dynamik
  - draft
source: "software_engineering_kapitel_13"
---

# [[Interaktionsdiagramm]]

- **Kernkonzept:** Ein [[Interaktionsdiagramm]] ist ein [[UML-Diagrammtyp|UML-Diagramm]], das die [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]], [[Komponente|Komponenten]] oder [[Akteur|Akteuren]] in einem [[System]] durch [[Nachrichtenfluss|Nachrichtenflüsse]] und zeitliche [[Ablauf|Abläufe]] visualisiert, um das dynamische [[Verhalten]] in spezifischen [[Use_Case|Szenarien]] oder [[Operation|Operationen]] zu modellieren und [[Verantwortlichkeit|Verantwortlichkeiten]] sowie die [[Zusammenarbeit|Zusammenarbeit]] von [[Systemkomponente|Systemkomponenten]] zur [[Laufzeit]] zu klären.
- **Nutzen & Zweck:** Ein [[Interaktionsdiagramm]] unterstützt die [[Analyse]] und das [[Design]] von [[System|Systemen]], indem es [[Nachrichtenfluss|Nachrichtenflüsse]] und [[Zusammenarbeit|Zusammenarbeiten]] zwischen [[Objekt|Objekten]], [[Komponente|Komponenten]] oder [[Akteur|Akteuren]] detailliert darstellt. Dadurch werden [[Design]]-Entscheidungen dokumentiert, [[Fehler]] in der [[Logik]] frühzeitig erkannt und die konkrete Umsetzung von [[Use_Case|Anwendungsfällen]] oder [[Operation|Operationen]] durch die Abbildung von [[Interaktion|Interaktionen]] veranschaulicht. Besonders nützlich ist es zur Klärung von [[Ablauf|Abläufen]] in [[Event-gesteuertes_System|Event-gesteuerten Systemen]], bei der Anwendung von [[Entwurfsmuster|Mustern]] wie dem [[Observer_Pattern]] oder zur präzisen Kommunikation zwischen [[Entwickler|Entwicklern]] und [[Stakeholder|Stakeholdern]]. Es löst das Problem abstrakter [[Anforderung|Anforderungsbeschreibungen]], indem es zeigt, wie [[Systemkomponente|Systemkomponenten]] zur [[Laufzeit]] zusammenwirken, um funktionale [[Anforderung|Anforderungen]] zu erfüllen. Zudem sichert es die [[Konsistenz]] zwischen [[Analyse]], [[Design]] und [[Implementierung]] und ermöglicht die frühzeitige Erkennung von [[Designfehler|Designfehlern]] durch die Visualisierung von [[Nachrichtenfluss|Nachrichtenflüssen]] und zeitlichen [[Ablauf|Abläufen]].
- **Abgrenzung & Grenzen:** Ein [[Interaktionsdiagramm]] ist nicht geeignet für die Darstellung statischer [[Struktur|Strukturen]] (hierfür [[Klassendiagramm|Klassendiagramme]] verwenden) oder übergreifender [[Prozess|Prozessabläufe]] (hier sind [[Aktivitätsdiagramm|Aktivitätsdiagramme]] besser geeignet). Im Gegensatz zu [[Aktivitätsdiagramm|Aktivitätsdiagrammen]], die [[Kontrollfluss|Kontrollflüsse]] und parallele [[Ablauf|Abläufe]] modellieren, fokussieren [[Interaktionsdiagramm|Interaktionsdiagramme]] auf die [[Kommunikation]] zwischen [[Objekt|Objekten]] und deren zeitliche Abfolge. Bei komplexen [[System|Systemen]] mit vielen [[Verzweigung|Verzweigungen]] oder [[Schleife|Schleifen]] können sie unübersichtlich werden; hier sind textuelle [[Dokumentation|Beschreibungen]] oder [[Zustandsdiagramm|Zustandsdiagramme]] oft klarer. Zudem eignen sie sich weniger für die Darstellung nicht-funktionaler [[Anforderung|Anforderungen]] wie [[Performance]] oder [[Sicherheit]] sowie für die Modellierung von [[Zustandsänderung|Zustandsänderungen]] über längere Zeiträume. Sie sind ungeeignet, wenn das [[Systemverhalten]] stark von externen, nicht-objektorientierten Faktoren abhängt oder wenn die [[Interaktion|Interaktionen]] zu trivial sind, um eine grafische Darstellung zu rechtfertigen. [[Interaktionsdiagramm|Interaktionsdiagramme]] umfassen spezifischere [[Diagrammtyp|Diagrammtypen]] wie [[Sequenzdiagramm|Sequenzdiagramme]] (zeitliche Abfolge) und [[Kommunikationsdiagramm|Kommunikationsdiagramme]] (strukturelle [[Beziehung|Beziehungen]]).
- **Beispiel / Code:** ```java
// Beispiel: [[Sequenzdiagramm]] (Teil eines [[Interaktionsdiagramm|Interaktionsdiagramms]]) für den [[Use_Case|Use Case]] "Mitglied anmelden"
actor [[Akteur|Mitglied]]
participant [[System]]
participant [[Datenbank]]

[[Akteur|Mitglied]] -> [[System]]: anmelden(benutzername, passwort)
[[System]] -> [[Datenbank]]: prüfeAnmeldedaten(benutzername, passwort)
[[Datenbank]] --> [[System]]: gültig
[[System]] --> [[Akteur|Mitglied]]: anmeldungErfolgreich()
[[System]] -> [[Datenbank]]: speichereSitzung(mitgliedId)

// Alternativ: [[Kommunikationsdiagramm]]-Beispiel (fokussiert auf strukturelle [[Beziehung|Beziehungen]])
[[Objekt|Objekte]]: [A:Benutzer, B:Controller, C:Model, D:View]
[[Nachrichtenfluss|Nachrichten]]:
A → B: 1: login(benutzername, passwort)
B → C: 1.1: validiere(benutzername, passwort)
C → B: 1.2: true/false
B → D: 2: zeigeErgebnis()

// Beispiel für eine [[Fassade|Fassade]] als zentralen Interaktionspunkt in einem [[Sequenzdiagramm]]
public interface ManagementFactory {
    ManagementFactory FACTORY = new ManagementFacade();
    
    MemberManagement memberManagement();
}

// Implementierung einer [[Fassade|Fassade]], die [[Lose_Kopplung|lose Kopplung]] fördert
@ApplicationScope
@Component
class ManagementFacade implements MemberManagement {
    @Autowired
    private StateMachine stateMachine;
    
    public void addMember(String memberData) {
        // Delegation an weitere [[Objekt|Objekte]] (z. B. MemberValidator, MemberRepository)
        stateMachine.validate(memberData);
        stateMachine.save(memberData);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1f
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Sequenzdiagramm]]
  - [[Kommunikationsdiagramm]]
- **Querverweise:**
  - [[UML]]
  - [[Verantwortungszuweisung]]
