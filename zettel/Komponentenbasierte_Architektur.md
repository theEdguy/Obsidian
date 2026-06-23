---
id: 618af726-e35c-47b0-96a3-120ef322818b
title: "Komponentenbasierte_Architektur"
date: 2026-06-23
tags:
  - software_engineering
  - architekturstil
  - softwarearchitektur
  - modularisierung
  - design_principle
  - architektur
  - komponenten
  - draft
source: "software_engineering_kapitel_10"
---

# [[Komponentenbasierte_Architektur]]

- **Kernkonzept:** [[Komponentenbasierte_Architektur]] ist ein [[Architekturstil]] und [[Entwurfsmuster]] in der [[Softwareentwicklung]], bei dem ein [[System]] in modulare, wiederverwendbare und unabhängige [[Komponente|Komponenten]] zerlegt wird. Jede [[Komponente]] besitzt eine definierte [[Schnittstelle]] und kapselt ihre [[Implementierung]], um klare [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Lose_Kopplung]] zu gewährleisten. Die [[Komponente|Komponenten]] kommunizieren über festgelegte [[Schnittstelle|Schnittstellen]] und repräsentieren spezifische [[Use_Case|Use-Cases]] oder [[Akteur|Akteure]] des [[System|Systems]].
- **Nutzen & Zweck:** [[Komponentenbasierte_Architektur]] existiert, um die [[Komplexität]] großer [[System|Systeme]] beherrschbar zu machen und die [[Wiederverwendbarkeit]], [[Modularität]] sowie [[Erweiterbarkeit]] zu fördern. Durch die Zerlegung in [[Komponente|Komponenten]] können [[Entwicklungsteam|Teams]] parallel arbeiten, einzelne [[Komponente|Komponenten]] isoliert entwickeln, testen und warten sowie leichter austauschen oder wiederverwenden. Dies erhöht die [[Kohäsion]] innerhalb der [[Komponente|Komponenten]] und reduziert die [[Abhängigkeit|Abhängigkeiten]] zwischen ihnen, was die [[Wartbarkeit]] und [[Skalierbarkeit]] des [[System|Systems]] verbessert. Konkret löst dieser [[Architekturstil]] Probleme wie enge [[Kopplung]], mangelnde [[Testbarkeit]] und schlechte [[Wartbarkeit]] in [[Monolithische_Architektur|monolithischen Architekturen]]. Zudem ermöglicht die klare Abgrenzung der [[Funktionalität]] eine bessere [[Arbeitsteilung]] in [[Projekt|Projekten]] und vereinfacht das [[Refactoring]] sowie die [[Integration]] neuer [[Anforderung|Anforderungen]].
- **Abgrenzung & Grenzen:** [[Komponentenbasierte_Architektur]] ist nicht für sehr kleine oder einfach strukturierte [[Systeme]] geeignet, da der [[Overhead]] durch [[Schnittstelle|Schnittstellen]]-Definitionen, [[Kommunikationsprotokoll|Kommunikationsprotokolle]] und [[Modularisierung]] unnötig sein kann. In solchen Fällen können [[Monolithische_Architektur|monolithische Architekturen]] oder [[Funktionale_Programmierung|funktionale Programmierung]] effizienter sein. Zudem unterscheidet sich dieser [[Architekturstil]] von [[Microservices]] durch seine Fokussierung auf lokale [[Modularität]] innerhalb eines [[System|Systems]], während [[Microservices]] eigenständige, verteilte [[Dienst|Dienste]] darstellen. Bei [[System|Systemen]] mit extrem hohen [[Performance]]-Anforderungen kann die zusätzliche [[Abstraktionsebene]] der [[Komponente|Komponenten]] zu unnötigen [[Latenz|Latenzen]] führen. Weitere Herausforderungen umfassen den erhöhten [[Designaufwand]] für die initiale Aufteilung in [[Komponente|Komponenten]] sowie potenzielle Probleme bei der [[Integration]] und [[Synchronisation]] vieler [[Komponente|Komponenten]] in großen [[System|Systemen]].
- **Beispiel / Code:** ```java
// Beispiel einer Komponente mit definierter Schnittstelle und Systemoperationen
public interface MemberManagement {
    // Systemoperation: Mitglied hinzufügen
    void addMember([[Member|Member]] member);
    
    // Systemoperation: Mitglied abrufen
    [[Member|Member]] getMember(int id);
    
    // Erweiterte Systemoperationen aus der neuen Quelle
    void updateMember([[Member|Member]] member);
    void deleteMember(int id);
}

// Implementierung der Komponente (versteckt hinter der Schnittstelle)
public class MemberManagementImpl implements MemberManagement {
    private [[Datenbank|Datenbank]]Connector dbConnector;
    
    public MemberManagementImpl([[Datenbank|Datenbank]]Connector dbConnector) {
        this.dbConnector = dbConnector;
    }
    
    @Override
    public void addMember([[Member|Member]] member) {
        dbConnector.speichern(member);
    }
    
    @Override
    public [[Member|Member]] getMember(int id) {
        return dbConnector.laden(id);
    }
    
    @Override
    public void updateMember([[Member|Member]] member) {
        dbConnector.aktualisieren(member);
    }
    
    @Override
    public void deleteMember(int id) {
        dbConnector.loeschen(id);
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

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1
- **Vorgänger / Parent:** [[Systemarchitektur]]
- **Folgezettel / Unterzettel:**
  - [[Komponenten]]
  - [[Ports]]
  - [[Konnektoren]]
  - [[Komponentendiagramme]]
- **Querverweise:** keine
