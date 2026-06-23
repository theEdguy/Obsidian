---
id: fd6fd41f-daf1-4121-b580-e1087902ba8f
title: "Analysemuster"
date: 2026-06-24
tags:
  - software_engineering
  - domain-driven-design
  - analyse
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Analysemuster]]

- **Kernkonzept:** Analysemuster sind wiederverwendbare [[Objektmodell|Objektmodelle]] und [[Lösungsmuster|Lösungsmuster]], die häufig auftretende [[Problemstellung|Problemstellungen]] in der [[Analysephase]] der [[Softwareentwicklung]] strukturiert abbilden. Sie bieten bewährte [[Struktur|Strukturen]] und [[Beziehung|Beziehungen]] zwischen [[Entität|Entitäten]], um komplexe [[Domäne|Domänenprobleme]] systematisch zu erfassen, zu modellieren und eine konsistente [[Modellierung]] durch erprobte Ansätze zu fördern. Als Grundlage für [[Domain-Driven_Design]] standardisieren sie die [[Analyse]] und [[Design|Gestaltung]] von [[Domain-spezifische_Probleme|domänenspezifischen Problemen]].
- **Nutzen & Zweck:** Analysemuster steigern die Effizienz und Qualität der [[Softwareanalyse]], indem sie Entwicklern und [[Analyst|Analysten]] vorgefertigte, validierte [[Lösungsansatz|Lösungsansätze]] für wiederkehrende fachliche [[Anforderung|Anforderungen]] bereitstellen. Sie reduzieren Redundanzen, beschleunigen die [[Modellierung]], minimieren Fehler durch bewährte [[Muster]] und etablieren eine gemeinsame sprachliche Basis für die [[Domänenmodellierung]]. Durch ihre Anwendung wird die [[Wiederverwendung]] von Wissen gefördert, die Kommunikation im Team verbessert und die [[Standardisierung]] von Analyse- und Designprozessen ermöglicht. Zudem lösen sie das Problem, dass ähnliche fachliche [[Anforderung|Anforderungen]] in verschiedenen Projekten immer wieder neu modelliert werden müssen, was Zeit kostet und zu inkonsistenten [[Lösung|Lösungen]] führt.
- **Abgrenzung & Grenzen:** Analysemuster sollten nicht genutzt werden, wenn die [[Problemstellung]] hochgradig domänenspezifisch, einzigartig oder trivial ist, da der Overhead der Musteranwendung dann den Nutzen übersteigt. Sie unterscheiden sich von [[Entwurfsmuster|Entwurfsmustern]], die sich auf technische [[Implementierung|Implementierungsdetails]] konzentrieren, indem sie sich auf die konzeptionelle [[Analysephase]] und fachliche [[Struktur|Strukturen]] fokussieren. Zudem sind sie keine fertigen [[Code]]-Lösungen, sondern abstrakte [[Modell|Modelle]], die an den konkreten Kontext angepasst und erst implementiert werden müssen. Bei sehr einfachen [[Domäne|Domänen]] können Analysemuster unnötig komplex wirken und die [[Modellierung]] überdimensionieren. Sie dienen als [[Analyse-Werkzeug]] und ersetzen keine [[Implementierung]], sondern unterstützen die [[Domain-Modellierung]].
- **Beispiel / Code:** ```java
// Beispiel: Analysemuster "Party" zur Modellierung von Akteuren (Personen und Organisationen)
public abstract class Party {
    private String name;
    private List<Address> addresses;
    
    public Party(String name) {
        this.name = name;
        this.addresses = new ArrayList<>();
    }
    
    public void addAddress(Address address) {
        addresses.add(address);
    }
}

public class Person extends Party {
    private String birthDate;
    
    public Person(String name, String birthDate) {
        super(name);
        this.birthDate = birthDate;
    }
}

public class Organization extends Party {
    private String taxId;
    
    public Organization(String name, String taxId) {
        super(name);
        this.taxId = taxId;
    }
}

// Beispiel: Analysemuster "Accountability" zur Modellierung von Verantwortlichkeiten
public class Accountability {
    private Party responsibleParty;
    private Party accountableParty;
    private String role;
    private Date startDate;
    private Date endDate;
    
    public Accountability(Party responsibleParty, Party accountableParty, String role) {
        this.responsibleParty = responsibleParty;
        this.accountableParty = accountableParty;
        this.role = role;
        this.startDate = new Date();
    }
    
    public void endAccountability() {
        this.endDate = new Date();
    }
}

// Beispiel: Analysemuster "Role" zur Erweiterung des Party-Musters
public interface Role {
    String getRoleName();
}

public class CustomerRole implements Role {
    @Override
    public String getRoleName() {
        return "Customer";
    }
}

public class PartyRole {
    private Party party;
    private Role role;
    
    public PartyRole(Party party, Role role) {
        this.party = party;
        this.role = role;
    }
    
    public String getRoleName() {
        return role.getRoleName();
    }
}
```
