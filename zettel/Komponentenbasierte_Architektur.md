---
id: 673993f9-95bd-4563-b821-52bb98922ba5
title: "Komponentenbasierte_Architektur"
date: 2026-05-30
tags:
  - software_engineering
  - architekturstil
  - softwarearchitektur
  - modularisierung
  - design_principle
  - architektur
  - draft
source: "SWE Slides (Folien 241-255)"
---

# [[Komponentenbasierte_Architektur]]

- **Kernkonzept:** [[Komponentenbasierte_Architektur]] ist ein [[Architekturstil]], bei dem eine [[Anwendung]] aus unabhängigen, wiederverwendbaren [[Komponente|Komponenten]] zusammengesetzt wird, die über definierte [[Schnittstelle|Schnittstellen]] kommunizieren. Jede [[Komponente]] repräsentiert dabei einen [[Use_Case]] oder [[Akteur]] und realisiert spezifische [[Systemoperation|Systemoperationen]], um die [[Logik]] des [[System|Systems]] modular abzubilden.
- **Nutzen & Zweck:** [[Komponentenbasierte_Architektur]] fördert die [[Wiederverwendbarkeit]], [[Modularität]] und [[Erweiterbarkeit]] von [[System|Systemen]], indem [[Komponente|Komponenten]] isoliert entwickelt, getestet und gewartet werden können. Durch die klare Abgrenzung der [[Funktionalität]] wird die [[Kohäsion]] innerhalb der [[Komponente|Komponenten]] erhöht, während die [[Lose_Kopplung]] zwischen ihnen die unabhängige Weiterentwicklung ermöglicht. Dies vereinfacht die [[Wartbarkeit]] und reduziert die [[Komplexität]] großer [[Anwendung|Anwendungen]].
- **Abgrenzung & Grenzen:** [[Komponentenbasierte_Architektur]] kann zu [[Overhead]] durch aufwendige [[Schnittstelle|Schnittstellen]]-Definitionen und [[Kommunikationsprotokoll|Kommunikationsprotokolle]] führen, was sie für sehr kleine [[Systeme]] oder [[Monolith|Monolithen]] mit geringer [[Komplexität]] weniger geeignet macht. Im Gegensatz zu [[Monolithische_Architektur|monolithischen Architekturen]] erfordert sie eine explizite Aufteilung in [[Komponente|Komponenten]], was zusätzlichen [[Designaufwand]] verursachen kann. Zudem kann die Verwaltung vieler [[Komponente|Komponenten]] in großen [[System|Systemen]] zu Herausforderungen bei der [[Integration]] und [[Performance]] führen.
- **Beispiel / Code:** ```java
// Komponente mit klarer Schnittstelle und Systemoperationen
public interface MemberManagement {
    // Systemoperation: Mitglied hinzufügen
    void addMember([[Member|Member]] member);
    
    // Systemoperation: Mitglied abrufen
    [[Member|Member]] getMember(int id);
}

// Implementierung der Komponente
public class MemberManagementImpl implements MemberManagement {
    @Override
    public void addMember([[Member|Member]] member) {
        // Logik zum Hinzufügen eines Mitglieds
    }
    
    @Override
    public [[Member|Member]] getMember(int id) {
        // Logik zum Abrufen eines Mitglieds
        return null;
    }
}

// Beispiel für eine weitere Komponente mit spezifischen Systemoperationen
public class AuthenticationComponent {
    // Systemoperation: Authentifizierung
    public void authenticate([[UserCredentials|UserCredentials]] credentials) {
        // Authentifizierungslogik
    }
    
    // Systemoperation: Session-Verwaltung
    public void invalidateSession([[Session|Session]] session) {
        // Logik zum Beenden einer Session
    }
}
```
