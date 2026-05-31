---
id: c23ad2df-4cab-4128-a190-7217da06ccc2
title: "Delegation_Konnektor"
date: 2026-05-31
tags:
  - software_engineering
  - softwarearchitektur
  - entwurfsmuster
  - uml
  - komponentenbasierte_entwicklung
  - modularisierung
  - draft
source: "Klausur_Referenz"
---

# [[Delegation_Konnektor]]

- **Kernkonzept:** Ein **Delegation_Konnektor** ist ein [[Konnektor]] in der [[Softwarearchitektur]], der eine externe [[Schnittstelle]] einer [[Komponente]] mit den internen (Sub-)Komponenten verbindet, die diese Schnittstelle entweder realisieren oder nutzen. Im Gegensatz zum [[Assembly_Connector]], der Komponenten direkt über Schnittstellen verbindet, dient der Delegation-Konnektor dazu, die Verantwortung für die Implementierung oder den Aufruf einer Schnittstelle an eine untergeordnete Komponente zu delegieren. Dies ermöglicht eine klare Trennung von externer Schnittstellenbeschreibung und interner Realisierung.
- **Nutzen & Zweck:** Der Delegation-Konnektor wird eingesetzt, um:
- **Kapselung** zu verbessern, indem interne Strukturen einer Komponente vor externen Nutzern verborgen werden.
- **Modularität** zu fördern, da Subkomponenten unabhängig von der externen Schnittstelle entwickelt und ausgetauscht werden können.
- **Wiederverwendbarkeit** zu erhöhen, indem dieselbe Schnittstelle von verschiedenen Subkomponenten implementiert oder genutzt werden kann.
- **Komplexität** zu reduzieren, indem die Verantwortung für eine Schnittstelle an spezialisierte Subkomponenten delegiert wird (z. B. in [[Fassadenmuster]]-Szenarien).

Typische Anwendungsfälle sind:
- Verbindung einer öffentlichen Schnittstelle einer Komponente mit einer internen Implementierungsklasse.
- Weiterleitung von Aufrufen an Subkomponenten, die spezifische Teilfunktionalitäten bereitstellen (z. B. in [[Kompositum_Muster]]-Strukturen).
- **Abgrenzung & Grenzen:** Abgrenzung zu verwandten Konzepten:
- **[[Assembly_Connector]]**: Verbindet zwei Komponenten direkt über ihre Schnittstellen, ohne Delegation an Subkomponenten.
- **[[Adapter_Muster]]**: Dient der Anpassung inkompatibler Schnittstellen, während der Delegation-Konnektor die Verbindung zwischen externer und interner Schnittstelle herstellt.
- **[[Fassadenmuster]]**: Nutzt oft Delegation-Konnektoren, um Aufrufe an Subsysteme weiterzuleiten, ist aber selbst kein Konnektor.

Stolpersteine:
- **Zyklische Abhängigkeiten**: Delegation kann zu ungewollten Abhängigkeitszyklen führen, wenn Subkomponenten auf die übergeordnete Komponente zurückverweisen.
- **Übermäßige Indirektion**: Zu viele Delegationsebenen können die Nachvollziehbarkeit des Kontrollflusses erschweren.
- **Schnittstellenkonsistenz**: Änderungen an der externen Schnittstelle müssen auch in den delegierenden Subkomponenten nachgezogen werden, um Inkonsistenzen zu vermeiden.
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Klassendiagramm (textuell beschrieben) veranschaulicht einen Delegation-Konnektor in einer Management-Komponente:\n\n```mermaid\nclassDiagram\n    class ManagementFacade {\n        -manager: ManageMembers\n        +manageMembers(Token token)\n    }\n    class ManageMembers {\n        +manageMembers(Token token)\n    }\n    class IMemberManagement {\n        <<interface>>\n        +manageMembers(Token token)\n    }\n\n    ManagementFacade ..|> IMemberManagement : implements\n    ManagementFacade --> ManageMembers : Delegation-Konnektor\n```\n\nJava-Codebeispiel (vereinfacht):\n```java\npublic interface IMemberManagement {\n    void manageMembers(Token token);\n}\n\npublic class ManagementFacade implements IMemberManagement {\n    private ManageMembers manager = new ManageMembers();\n\n    @Override\n    public void manageMembers(Token token) {\n        // Delegation an Subkomponente\n        manager.manageMembers(token);\n    }\n}\n\npublic class ManageMembers {\n    public void manageMembers(Token token) {\n        // Implementierungslogik\n    }\n}\n```', 'hinweis': 'Der Delegation-Konnektor ist hier die Verbindung zwischen `ManagementFacade` (externe Schnittstelle) und `ManageMembers` (interne Implementierung).'}
