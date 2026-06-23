---
id: c17a27a2-e0e1-42cf-94f3-a6b44dc252f9
title: "Architekturprinzipien"
date: 2026-06-23
tags:
  - software_engineering
  - prinzipien
  - architektur
  - draft
source: "software_engineering_kapitel_07"
---

# [[Architekturprinzipien]]

- **Kernkonzept:** Architekturprinzipien sind grundlegende Leitlinien und Regeln, die den strukturellen Aufbau und die Organisation von Softwaresystemen definieren, um deren Qualität, Wartbarkeit und Skalierbarkeit sicherzustellen. Sie bilden das Fundament für Entscheidungen im Software-Engineering-Prozess und leiten die Entwicklung einer stabilen Systemarchitektur.
- **Nutzen & Zweck:** Architekturprinzipien existieren, um komplexe Softwaresysteme beherrschbar zu machen, indem sie klare Richtlinien für Designentscheidungen vorgeben. Sie lösen das Problem der Inkonsistenz, unkontrollierter Abhängigkeiten und technischer Schulden, die durch ad-hoc-Entscheidungen entstehen. Durch ihre Anwendung wird die Nachvollziehbarkeit, Erweiterbarkeit und Robustheit der Software gefördert, was langfristig Entwicklungs- und Wartungskosten reduziert und die Anpassungsfähigkeit an neue Anforderungen verbessert.
- **Abgrenzung & Grenzen:** Architekturprinzipien sollten nicht starr angewendet werden, wenn Flexibilität und schnelle Prototypenentwicklung im Vordergrund stehen, wie z. B. in frühen Startup-Phasen oder bei Proof-of-Concept-Projekten. Sie unterscheiden sich von konkreten Designmustern oder Implementierungsdetails, da sie abstrakter und kontextunabhängiger sind. Alternativen wie anekdotische Erfahrungswerte oder rein funktionale Anforderungen können in einfachen Systemen ausreichen, bergen jedoch das Risiko von Inkonsistenzen und technischen Schulden in größeren oder langlebigen Projekten.
- **Beispiel / Code:** ```java
// Beispiel für das Prinzip 'Separation of Concerns' in einer Schichtenarchitektur
public class UserService {
    private final UserRepository userRepository;
    private final EmailService emailService;

    public UserService(UserRepository userRepository, EmailService emailService) {
        this.userRepository = userRepository;
        this.emailService = emailService;
    }

    public void registerUser(User user) {
        userRepository.save(user);
        emailService.sendWelcomeEmail(user);
    }
}

// UserRepository und EmailService sind separate Komponenten mit klaren Verantwortlichkeiten
interface UserRepository {
    void save(User user);
}

interface EmailService {
    void sendWelcomeEmail(User user);
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a
- **Vorgänger / Parent:** [[Systemarchitektur]]
- **Folgezettel / Unterzettel:**
  - [[Modularität]]
  - [[Kohäsion]]
  - [[Kopplung]]
  - [[Separation_of_Concerns]]
- **Querverweise:**
  - [[Systemarchitektur]]
  - [[Design-Prinzipien]]
