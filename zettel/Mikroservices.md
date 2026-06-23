---
id: 972cda3a-44be-45cf-baa6-4ba098db87ba
title: "Mikroservices"
date: 2026-06-23
tags:
  - software_engineering
  - mikroservices
  - architektur
  - draft
source: "software_engineering_kapitel_07"
---

# [[Mikroservices]]

- **Kernkonzept:** Mikroservices sind ein Architekturstil, bei dem eine Anwendung als Sammlung kleiner, unabhängiger Dienste entwickelt wird, die jeweils eine spezifische Geschäftslogik kapseln und über klar definierte Schnittstellen kommunizieren. Diese Dienste sind eigenständig deploybar und skalierbar.
- **Nutzen & Zweck:** Mikroservices lösen das Problem monolithischer Anwendungen, die schwer zu warten, zu skalieren und weiterzuentwickeln sind. Sie ermöglichen eine flexible, modulare Entwicklung, bei der Teams unabhängig voneinander arbeiten und Technologien je nach Bedarf wählen können. Zudem erleichtern sie die Skalierung einzelner Komponenten und erhöhen die Ausfallsicherheit, da der Ausfall eines Dienstes nicht zwangsläufig das gesamte System betrifft.
- **Abgrenzung & Grenzen:** Mikroservices sollten nicht genutzt werden, wenn die Anwendung einfach und überschaubar ist, da der Overhead durch verteilte Systeme (z. B. Netzwerkkommunikation, Monitoring, Deployment) den Nutzen übersteigt. Im Vergleich zu monolithischen Architekturen erfordern Mikroservices mehr Aufwand für Infrastruktur, DevOps und Fehlerbehandlung. Alternativen wie modulare Monolithe oder Service-oriented Architectures (SOA) können in solchen Fällen besser geeignet sein. Zudem sind Mikroservices weniger sinnvoll, wenn starke transaktionale Konsistenz über mehrere Dienste hinweg erforderlich ist.
- **Beispiel / Code:** ```java
// Beispiel: Einfacher Mikroservice für Benutzerverwaltung mit Spring Boot
@RestController
@RequestMapping("/users")
public class UserController {
    @Autowired
    private UserRepository userRepository;

    @GetMapping("/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        return userRepository.findById(id)
                .map(ResponseEntity::ok)
                .orElse(ResponseEntity.notFound().build());
    }

    @PostMapping
    public User createUser(@RequestBody User user) {
        return userRepository.save(user);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b2
- **Vorgänger / Parent:** [[Architekturstil]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Architekturstil]]
