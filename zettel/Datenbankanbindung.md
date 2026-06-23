---
id: ab0f825d-2245-48b1-93f3-718c3d752b44
title: "Datenbankanbindung"
date: 2026-06-24
tags:
  - software_engineering
  - datenhaltung
  - architektur
  - draft
source: "software_engineering_kapitel_15"
---

# [[Datenbankanbindung]]

- **Kernkonzept:** Die Datenbankanbindung im Software-Engineering bezeichnet die Integration einer Persistenzschicht, die Objekte und Datenstrukturen einer Anwendung in einer Datenbank speichert, verwaltet und bei Bedarf wiederherstellt. Sie ermöglicht die dauerhafte Speicherung von Anwendungsdaten über Sitzungen hinweg.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der flüchtigen Datenspeicherung in Anwendungen, indem es eine strukturierte und effiziente Möglichkeit bietet, Daten dauerhaft zu speichern und abzurufen. Es ermöglicht die Trennung von Geschäftslogik und Datenhaltung, verbessert die Skalierbarkeit und vereinfacht die Wartung durch standardisierte Schnittstellen wie OR-Mapper. Zudem sichert es die Datenintegrität und unterstützt Transaktionen, um konsistente Zustände zu gewährleisten.
- **Abgrenzung & Grenzen:** Die Datenbankanbindung sollte nicht genutzt werden, wenn die Anwendung nur temporäre Daten verarbeitet oder keine dauerhafte Speicherung benötigt, da der Overhead der Datenbankintegration unnötig ist. Alternativen wie In-Memory-Datenbanken oder einfache Dateispeicherung können in solchen Fällen effizienter sein. Bei hochspezialisierten Anwendungen mit extrem niedrigen Latenzanforderungen kann eine direkte Dateispeicherung oder ein Caching-Mechanismus besser geeignet sein. Zudem ist die Nutzung von OR-Mappern nicht sinnvoll, wenn die Datenbankstruktur stark von der Objektstruktur abweicht oder komplexe, nicht-standardisierte Abfragen erforderlich sind.
- **Beispiel / Code:** ```java
// Beispiel für die Nutzung von JPA (Java Persistence API) mit Hibernate
@Entity
@Table(name = "members")
public class Member {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(name = "name")
    private String name;
    
    @Column(name = "email")
    private String email;
    
    // Getter und Setter
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }
}

// Nutzung im Service-Layer
public class MemberService {
    @PersistenceContext
    private EntityManager entityManager;
    
    public void saveMember(Member member) {
        entityManager.persist(member);
    }
    
    public Member findMemberById(Long id) {
        return entityManager.find(Member.class, id);
    }
}
```
