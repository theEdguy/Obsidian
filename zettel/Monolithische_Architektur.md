---
id: c3a36407-72d6-434f-b590-75e314f08f7b
title: "Monolithische Architektur"
date: 2026-06-23
tags:
  - software_engineering
  - monolith
  - architektur
  - draft
source: "software_engineering_kapitel_07"
---

# [[Monolithische Architektur]]

- **Kernkonzept:** Eine monolithische Architektur bezeichnet ein Softwaresystem, bei dem alle Komponenten und Funktionen in einem einzigen, untrennbaren Codeblock oder Deployment-Einheit zusammengefasst sind. Das gesamte System läuft als eine einzige Anwendung auf einem Server oder einer Instanz.
- **Nutzen & Zweck:** Die monolithische Architektur existiert, um die Entwicklung, das Deployment und die Wartung von Software in frühen Projektphasen oder bei überschaubaren Systemen zu vereinfachen. Sie löst das Problem der Komplexität durch zentrale Steuerung, da alle Module direkt miteinander interagieren und keine verteilte Kommunikation erforderlich ist. Dies reduziert Overhead in der Entwicklung und erleichtert die Fehlersuche, da alle Komponenten an einem Ort vorliegen.
- **Abgrenzung & Grenzen:** Monolithische Architekturen sollten nicht genutzt werden, wenn das System stark skalierbar, flexibel erweiterbar oder hochverfügbar sein muss. Im Vergleich zu Microservices oder modularen Architekturen fehlt die Möglichkeit, einzelne Komponenten unabhängig zu deployen oder zu skalieren. Zudem erschwert ein Monolith die Wartung bei wachsender Codebasis, da Änderungen an einer Stelle unerwartete Auswirkungen auf andere Teile des Systems haben können. Für komplexe, verteilte Systeme oder Anwendungen mit unterschiedlichen Skalierungsanforderungen sind alternative Architekturen besser geeignet.
- **Beispiel / Code:** ```java
// Beispiel für eine monolithische Java-Anwendung mit Spring Boot
@SpringBootApplication
public class MonolithicApp {
    public static void main(String[] args) {
        SpringApplication.run(MonolithicApp.class, args);
    }
}

@RestController
class UserController {
    @Autowired
    private UserService userService;

    @GetMapping("/users")
    public List<User> getAllUsers() {
        return userService.findAll();
    }
}

@Service
class UserService {
    @Autowired
    private UserRepository userRepository;

    public List<User> findAll() {
        return userRepository.findAll();
    }
}
```

*In diesem Beispiel sind alle Schichten (Controller, Service, Repository) in einer einzigen Anwendung gebündelt, was typisch für eine monolithische Architektur ist.*

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b1
- **Vorgänger / Parent:** [[Architekturstil]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Architekturstil]]
