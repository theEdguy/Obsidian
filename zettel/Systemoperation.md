---
id: 33d77209-2a9b-4883-9495-cbaea38fea27
title: "Systemoperation"
date: 2026-05-30
tags:
  - software_engineering
  - design_principle
  - architektur
  - system_design
  - use_case
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[Systemoperation]]

- **Kernkonzept:** Eine [[Systemoperation]] definiert eine spezifische [[Operation]], die von einer [[Komponente]] oder einem [[Subsystem]] bereitgestellt wird, um eine [[Funktionalität]] im Rahmen eines [[Use_Case|Use Cases]] zu realisieren. Sie beschreibt die [[Verantwortung|Verantwortlichkeiten]], [[Vorbedingung|Vorbedingungen]], [[Nachbedingung|Nachbedingungen]] und mögliche [[Ausnahme|Ausnahmen]] auf [[System|System]]-Ebene.
- **Nutzen & Zweck:** Eine [[Systemoperation]] ermöglicht die klare Abgrenzung von [[Verantwortung|Verantwortlichkeiten]] innerhalb eines [[Systems]] und dient als Grundlage für die Definition von [[Schnittstelle|Schnittstellen]]. Sie formalisiert die Interaktion zwischen [[Akteur|Akteuren]] und dem [[System]], unterstützt die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] und verbessert die [[Modularität]] sowie [[Wartbarkeit]] des [[Systems]].
- **Abgrenzung & Grenzen:** Eine [[Systemoperation]] ist nicht direkt auf [[Benutzeroberfläche|Benutzeroberflächen]]-Operationen oder interne [[Hilfsmethode|Hilfsmethoden]] abzubilden, sondern bezieht sich auf die [[Logik]]-Ebene des [[Systems]]. Sie unterscheidet sich von [[Methode|Methoden]] auf Code-Ebene durch ihren abstrakteren Charakter und ihren Bezug zu [[Use_Case|Use Cases]]. [[Systemoperation|Systemoperationen]] sollten nicht für zu granulare oder rein technische Aufgaben genutzt werden, sondern bleiben auf die [[Funktionalität]] des [[Systems]] fokussiert.
- **Beispiel / Code:** ```java
// Beispiel für eine Systemoperation in einer Komponente mit Vor- und Nachbedingungen
public interface MemberManagement {
    /**
     * Fügt ein neues Mitglied zum System hinzu.
     * @param member Das hinzuzufügende Mitglied
     * @throws DuplicateMemberException falls das Mitglied bereits existiert
     * @throws InvalidMemberDataException falls die Mitgliedsdaten ungültig sind
     */
    void addMember(Member member);
    
    /**
     * Entfernt ein Mitglied aus dem System.
     * @param id Die ID des zu entfernenden Mitglieds
     * @throws MemberNotFoundException falls das Mitglied nicht existiert
     */
    void removeMember(MemberId id);
    
    /**
     * Listet alle Mitglieder im System auf.
     * @return Liste aller Mitglieder
     * @throws DatabaseUnavailableException falls die Datenbank nicht erreichbar ist
     */
    List<Member> listMembers();
}

// Beispielimplementierung mit Vor- und Nachbedingungen
public class MemberManagementImpl implements MemberManagement {
    @Override
    public void addMember(Member member) {
        if (member == null || !member.isValid()) {
            throw new InvalidMemberDataException();
        }
        if (database.memberExists(member.getId())) {
            throw new DuplicateMemberException();
        }
        database.storeMember(member);
    }
    
    @Override
    public void removeMember(MemberId id) {
        if (!database.memberExists(id)) {
            throw new MemberNotFoundException();
        }
        database.deleteMember(id);
    }
    
    @Override
    public List<Member> listMembers() {
        if (!database.isAvailable()) {
            throw new DatabaseUnavailableException();
        }
        return database.loadAllMembers();
    }
}
```
