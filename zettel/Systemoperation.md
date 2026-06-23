---
id: 02cdf72e-32f8-4dd9-9fa0-123d7dbddebb
title: "Systemoperation"
date: 2026-06-23
tags:
  - software_engineering
  - design_principle
  - architektur
  - system_design
  - use_case
  - design
  - implementation
  - operation
  - software
  - draft
source: "software_engineering_kapitel_12"
---

# [[Systemoperation]]

- **Kernkonzept:** Eine [[Systemoperation]] definiert eine präzise spezifizierte [[Schnittstelle|Schnittstellenfunktion]] innerhalb eines [[Systems]], die durch äußere [[Ereignis|Ereignisse]] (z. B. [[Nutzerinteraktion]]) ausgelöst wird und den [[Systemzustand]] gemäß festgelegter [[Vorbedingung|Vorbedingungen]] und [[Nachbedingung|Nachbedingungen]] verändert. Sie formalisiert die [[Verantwortung|Verantwortlichkeiten]] einer [[Komponente]] oder eines [[Subsystems]] im Rahmen eines [[Use_Case|Use Cases]] und strukturiert die Interaktion zwischen [[Benutzeroberfläche|Benutzeroberflächen]] und der [[Anwendungslogik]].
- **Nutzen & Zweck:** Eine [[Systemoperation]] ermöglicht die klare Abgrenzung von [[Verantwortung|Verantwortlichkeiten]] innerhalb eines [[Systems]] und dient als Grundlage für die Definition von [[Schnittstelle|Schnittstellen]]. Sie formalisiert die Interaktion zwischen [[Akteur|Akteuren]] und dem [[System]], unterstützt die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] und verbessert die [[Modularität]] sowie [[Wartbarkeit]]. Durch die präzise Definition von [[Eingabe|Eingaben]], [[Ausnahme|Ausnahmen]], [[Vorbedingung|Vorbedingungen]] und [[Nachbedingung|Nachbedingungen]] wird die Implementierung testbarer, weniger fehleranfällig und einfacher zu warten. Zudem löst sie das Problem unklarer [[Schnittstelle|Schnittstellen]] und unvorhersehbarer [[Systemzustand|Systemzustände]], indem sie sicherstellt, dass [[Operation|Operationen]] nur in zulässigen [[Zustand|Zuständen]] ausgeführt werden und nach ihrer Ausführung einen definierten Folgezustand hinterlassen. Dies erhöht die Nachvollziehbarkeit und reduziert die Komplexität des [[Systems]].
- **Abgrenzung & Grenzen:** Eine [[Systemoperation]] ist nicht direkt auf [[Benutzeroberfläche|Benutzeroberflächen]]-Operationen oder interne [[Hilfsmethode|Hilfsmethoden]] abzubilden, sondern bezieht sich auf die [[Logik]]-Ebene des [[Systems]]. Sie unterscheidet sich von [[Methode|Methoden]] auf Code-Ebene durch ihren abstrakteren Charakter und ihren Bezug zu [[Use_Case|Use Cases]]. [[Systemoperation|Systemoperationen]] sollten nicht für zu granulare oder rein technische Aufgaben genutzt werden, sondern bleiben auf die [[Funktionalität]] des [[Systems]] fokussiert. Sie sind ungeeignet für triviale Anwendungen ohne klare Trennung zwischen [[Benutzeroberfläche]] und [[Anwendungslogik]] oder für Systeme ohne definierte [[Zustand|Zustände]] und [[Zustandsübergang|Zustandsübergänge]], wie z. B. rein funktionale oder [[Stateless]]-Anwendungen. Alternativen wie direkte [[Methode|Methodenaufrufe]], [[Event-gesteuertes_System|ereignisgesteuerte Architekturen]] (z. B. [[Event_Sourcing]]) oder einfache Prozeduren ohne Zustandsmanagement können in solchen Fällen effizienter sein. Im Vergleich zu allgemeinen [[API]]-Endpunkten sind [[Systemoperation|Systemoperationen]] spezifisch auf [[Use_Case|Use Cases]] zugeschnitten und enthalten keine technischen Details wie Netzwerkprotokolle oder Serialisierung. Bei Systemen mit hoher [[Nebenläufigkeit]] können [[Systemoperation|Systemoperationen]] zudem schwer synchronisierbar sein, da sie zusätzliche Modellierungsaufwände für [[Zustand|Zustände]] und [[Bedingung|Bedingungen]] erfordern.
- **Beispiel / Code:** ```java
// Beispiel für Systemoperationen mit Zustandsmanagement und Vor-/Nachbedingungen
public interface MemberManagement {
    /**
     * Fügt ein neues Mitglied zum System hinzu.
     * @param member Das hinzuzufügende Mitglied
     * @throws DuplicateMemberException falls das Mitglied bereits existiert
     * @throws InvalidMemberDataException falls die Mitgliedsdaten ungültig sind
     * @throws IllegalStateException falls das System nicht im zulässigen Zustand ist
     */
    void addMember(Member member);
    
    /**
     * Entfernt ein Mitglied aus dem System.
     * @param id Die ID des zu entfernenden Mitglieds
     * @throws MemberNotFoundException falls das Mitglied nicht existiert
     * @throws IllegalStateException falls das System nicht im zulässigen Zustand ist
     */
    void removeMember(MemberId id);
    
    /**
     * Listet alle Mitglieder im System auf.
     * @return Liste aller Mitglieder
     * @throws DatabaseUnavailableException falls die Datenbank nicht erreichbar ist
     * @throws IllegalStateException falls das System nicht im zulässigen Zustand ist
     */
    List<Member> listMembers();
    
    /**
     * Systemoperation zum Laden und Aufbereiten von Mitgliederdaten mit Zustandsprüfung.
     * @param token [[Authentisierungstoken]] zur Validierung
     * @throws InvalidTokenException falls das Token ungültig ist
     * @throws DatabaseUnavailableException falls die Datenbank nicht erreichbar ist
     * @throws IllegalStateException falls das System nicht im zulässigen Zustand ist
     */
    void manageMembers(Token token);
}

// Implementierung mit Zustandsmaschine und Vor-/Nachbedingungen
public class MemberManagementImpl implements MemberManagement {
    private final StateMachine stateMachine;
    private final MemberRepository memberRepository;
    private final TokenValidator tokenValidator;
    
    @Override
    public void addMember(Member member) {
        // Vorbedingung: System muss im Zustand 'Initialized' oder 'EditMember' sein
        if (!stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            throw new IllegalStateException("Operation nicht erlaubt im aktuellen Zustand");
        }
        
        if (member == null || !member.isValid()) {
            throw new InvalidMemberDataException();
        }
        if (memberRepository.memberExists(member.getId())) {
            throw new DuplicateMemberException();
        }
        
        memberRepository.save(member);
        
        // Nachbedingung: Zustand wechselt zu 'EditMember'
        stateMachine.setState(State.S.EditMember);
    }
    
    @Override
    public void removeMember(MemberId id) {
        if (!stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            throw new IllegalStateException("Operation nicht erlaubt im aktuellen Zustand");
        }
        
        if (!memberRepository.memberExists(id)) {
            throw new MemberNotFoundException();
        }
        
        memberRepository.delete(id);
        
        // Nachbedingung: Zustand bleibt 'Initialized'
        stateMachine.setState(State.S.Initialized);
    }
    
    @Override
    public List<Member> listMembers() {
        if (!stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            throw new IllegalStateException("Operation nicht erlaubt im aktuellen Zustand");
        }
        
        if (!memberRepository.isAvailable()) {
            throw new DatabaseUnavailableException();
        }
        
        return memberRepository.loadAll();
    }
    
    @Override
    public void manageMembers(Token token) {
        if (!stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            throw new IllegalStateException("Operation nicht erlaubt im aktuellen Zustand");
        }
        
        if (!tokenValidator.validate(token)) {
            throw new InvalidTokenException("Token konnte nicht validiert werden");
        }
        
        List<Member> members = memberRepository.loadAll();
        memberCache.prepareForAccess(members);
        
        // Nachbedingung: Zustand wechselt zu 'ManagingMembers'
        stateMachine.setState(State.S.ManagingMembers);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Vorbedingungen]]
  - [[Nachbedingungen]]
  - [[Trigger]]
- **Querverweise:**
  - [[Protokoll-Automaten]]
  - [[State-Pattern]]
