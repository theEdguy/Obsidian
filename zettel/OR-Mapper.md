---
id: f80267dd-ceab-4a5d-ae8c-d3958e15216b
title: "OR-Mapper"
date: 2026-06-24
tags:
  - software_engineering
  - datenhaltung
  - framework
  - draft
source: "software_engineering_kapitel_15"
---

# [[OR-Mapper]]

- **Kernkonzept:** Ein OR-Mapper (Object-Relational Mapper) ist ein Framework, das die Abbildung von relationalen Datenbanktabellen auf objektorientierte Klassen und deren Instanzen automatisiert. Es ermöglicht die persistente Speicherung von Objekten in einer Datenbank ohne manuelle SQL-Anweisungen.
- **Nutzen & Zweck:** OR-Mapper lösen das Problem des sogenannten 'Impedance Mismatch' zwischen objektorientierten Programmiersprachen und relationalen Datenbanken. Sie vereinfachen die Datenhaltung, indem sie Entwicklern erlauben, mit Objekten statt mit SQL zu arbeiten, und reduzieren so den manuellen Aufwand für Datenbankoperationen wie CRUD (Create, Read, Update, Delete). Zudem fördern sie die Wiederverwendbarkeit und Wartbarkeit von Code durch Standardisierung und Abstraktion.
- **Abgrenzung & Grenzen:** OR-Mapper sollten nicht genutzt werden, wenn die Anwendung sehr einfache Datenbankoperationen erfordert oder wenn die Performance kritisch ist, da sie oft Overhead durch Abstraktionsschichten verursachen. Alternativen wie direkter SQL-Zugriff oder Micro-ORMs können in solchen Fällen effizienter sein. Zudem sind OR-Mapper weniger geeignet für hochkomplexe Abfragen oder Datenbank-spezifische Optimierungen, die manuell angepasst werden müssen. Bei Projekten mit sehr spezifischen Datenbankanforderungen kann die Nutzung eines OR-Mappers zu unnötiger Komplexität führen.
- **Beispiel / Code:** ```java
// Beispiel mit Java Persistence API (JPA) und Hibernate als OR-Mapper
@Entity
@Table(name = "members")
public class Member {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(name = "name")
    private String name;
    
    // Getter und Setter
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}

// Nutzung im Code
EntityManagerFactory emf = Persistence.createEntityManagerFactory("myPersistenceUnit");
EntityManager em = emf.createEntityManager();
Member member = new Member();
member.setName("Max Mustermann");
em.getTransaction().begin();
em.persist(member);
em.getTransaction().commit();
```
