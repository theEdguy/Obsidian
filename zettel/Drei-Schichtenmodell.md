---
id: c5755790-ffbb-481e-a182-ff8382a99b01
title: "Drei-Schichtenmodell"
date: 2026-05-30
tags:
  - software_engineering
  - architekturmuster
  - softwarearchitektur
  - schichtenmodell
  - draft
source: "SWE Slides (Folien 211-225)"
---

# [[Drei-Schichtenmodell]]

- **Kernkonzept:** Das [[Drei-Schichtenmodell]] ist ein [[Architekturmuster]], das eine [[Anwendung]] in drei logische [[Schicht|Schichten]] unterteilt: [[Präsentationsschicht]], [[Logikschicht]] (Business-Logik) und [[Datenzugriffsschicht]] (Persistenz).
- **Nutzen & Zweck:** Es fördert die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]], verbessert die [[Wartbarkeit]] und ermöglicht die unabhängige [[Skalierung]] einzelner [[Schicht|Schichten]].
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Anwendung|Anwendungen]] mit geringer Komplexität, da der Overhead der [[Schicht|Schichten]]-Trennung unnötig ist. Bei [[Echtzeitsystem|Echtzeitsystemen]] kann die zusätzliche [[Latenz]] durch die [[Schicht|Schichten]]-Kommunikation problematisch sein.
- **Beispiel / Code:** ```java
// Präsentationsschicht (GUI)
public class MemberManagementGUI {
    private MemberManagementLogic logic;
    
    public void updateMember() {
        logic.updateMemberData();
    }
}

// Logikschicht (Business-Logik)
public class MemberManagementLogic {
    private DatabaseConnector dbConnector;
    
    public void updateMemberData() {
        dbConnector.saveToDatabase();
    }
}

// Datenzugriffsschicht (Persistenz)
public class DatabaseConnector {
    public void saveToDatabase() {
        // JDBC-Code zur Speicherung
    }
}
```
