---
id: 51c40ef3-dff3-4053-bcf5-335d4e0151a7
title: "Modell_in_der_Logikschicht"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design_principle
  - draft
source: "SWE Slides (Folien 241-255)"
---

# [[Modell_in_der_Logikschicht]]

- **Kernkonzept:** Das [[Modell]] in einer [[Mehrschichtenarchitektur]], das die [[Geschäftslogik]] und [[Daten]] eines [[Systems]] kapselt. Es ist unabhängig von der [[Benutzeroberfläche]] und stellt [[Systemoperation|Systemoperationen]] für die [[Logikschicht]] bereit.
- **Nutzen & Zweck:** Trennt die [[Geschäftslogik]] von der [[Präsentation]], um [[Wiederverwendbarkeit]], [[Testbarkeit]] und [[Wartbarkeit]] zu erhöhen. Ermöglicht die unabhängige Entwicklung von [[Logik]] und [[Benutzeroberfläche]].
- **Abgrenzung & Grenzen:** Keine direkte Interaktion mit der [[Benutzeroberfläche]], sondern über definierte [[Schnittstelle|Schnittstellen]]. Unterscheidet sich von [[Anämisches_Domänenmodell|anämischen Domänenmodellen]] durch die Kapselung von [[Logik]] und [[Daten]].
- **Beispiel / Code:** ```java
// Beispiel für ein Modell in der Logikschicht
public class MemberModel {
    private List<Member> members;
    
    public void addMember(Member member) {
        if (members.contains(member)) {
            throw new DuplicateMemberException();
        }
        members.add(member);
    }
}
```
