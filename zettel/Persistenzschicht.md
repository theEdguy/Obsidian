---
id: 5eb1f99a-ca41-4f91-ad3a-2243070969bd
title: "Persistenzschicht"
date: 2026-06-24
tags:
  - software_engineering
  - datenhaltung
  - architektur
  - draft
source: "software_engineering_kapitel_15"
---

# [[Persistenzschicht]]

- **Kernkonzept:** Die Persistenzschicht ist ein architektonisches Konzept in der Softwareentwicklung, das die dauerhafte Speicherung und Verwaltung von Daten in einer Datenbank oder einem anderen Speichermedium ermöglicht. Sie trennt die Datenhaltung logisch und technisch von der Anwendungslogik und Benutzeroberfläche.
- **Nutzen & Zweck:** Die Persistenzschicht existiert, um die Komplexität der Datenverwaltung von der Geschäftslogik zu entkoppeln. Sie löst das Problem der effizienten, konsistenten und sicheren Speicherung von Anwendungsdaten, indem sie standardisierte Schnittstellen (z. B. OR-Mapper) bereitstellt. Dadurch wird die Wartbarkeit, Skalierbarkeit und Portabilität der Software verbessert, da Änderungen an der Datenbank oder Speicherstrategie keine Auswirkungen auf andere Systemkomponenten haben.
- **Abgrenzung & Grenzen:** Die Persistenzschicht sollte nicht genutzt werden, wenn die Anwendung keine dauerhafte Datenspeicherung benötigt oder wenn die Datenmenge so gering ist, dass eine einfache Dateispeicherung ausreicht. Alternativen wie In-Memory-Datenbanken oder direkte Dateizugriffe können performanter sein, wenn keine komplexen Abfragen oder Transaktionen erforderlich sind. Zudem ist die Persistenzschicht oft überdimensioniert für kleine Projekte oder Prototypen, bei denen der Implementierungsaufwand den Nutzen übersteigt. Sie unterscheidet sich von direkten Datenbankzugriffen durch ihre Abstraktionsebene und die Verwendung von Frameworks wie Hibernate, die zwar Flexibilität bieten, aber auch zusätzliche Komplexität einführen.
- **Beispiel / Code:** ```java
// Beispiel: Verwendung eines OR-Mappers (Hibernate) zur Persistenz von Objekten
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

// Speichern eines Objekts in der Datenbank
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
Member member = new Member();
member.setName("Max Mustermann");
session.save(member);
tx.commit();
session.close();
```
