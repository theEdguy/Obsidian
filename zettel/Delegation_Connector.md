---
id: 63f9d7d8-d4d3-4a62-82e9-cbe208cf71b5
title: "Delegation Connector"
date: 2026-06-23
tags:
  - software_engineering
  - verbindung
  - schnittstelle
  - draft
source: "software_engineering_kapitel_10"
---

# [[Delegation Connector]]

- **Kernkonzept:** Ein Delegation Connector ist ein Verbindungselement in der komponentenbasierten Softwarearchitektur, das externe Schnittstellen einer Komponente mit den internen Subkomponenten verknüpft, die diese Schnittstellen entweder bereitstellen oder benötigen. Er ermöglicht die Weiterleitung von Anfragen zwischen der äußeren und inneren Struktur einer Komponente.
- **Nutzen & Zweck:** Der Delegation Connector existiert, um eine klare Trennung zwischen der öffentlichen Schnittstelle einer Komponente und ihrer internen Implementierung zu gewährleisten. Er löst das Problem, dass externe Nutzer einer Komponente nicht direkt auf deren interne Subkomponenten zugreifen müssen, sondern über definierte Schnittstellen kommunizieren. Dadurch wird die Modularität und Wartbarkeit des Systems verbessert, da Änderungen an der internen Struktur keine Auswirkungen auf die externe Nutzung haben.
- **Abgrenzung & Grenzen:** Ein Delegation Connector sollte nicht genutzt werden, wenn eine direkte Verbindung zwischen Komponenten ohne Zwischenschicht erforderlich ist, beispielsweise bei extrem performancekritischen Systemen, wo der Overhead der Delegation vermieden werden muss. Er unterscheidet sich von einem Assembly Connector, der Komponenten auf derselben Abstraktionsebene verbindet, indem er speziell die Schnittstelle einer Komponente mit deren internen Subkomponenten verknüpft. Bei einfachen Systemen mit flacher Hierarchie kann der Einsatz eines Delegation Connectors unnötig komplex wirken.
- **Beispiel / Code:** ```java
// Beispiel: Delegation Connector in einer Komponente mit Subkomponenten
public class UserManagementComponent {
    private UserService userService;  // Subkomponente
    private AuthService authService;  // Subkomponente

    // Öffentliche Schnittstelle der Komponente
    public User getUser(String userId) {
        // Delegation an interne Subkomponente
        return userService.fetchUser(userId);
    }

    public boolean authenticate(String username, String password) {
        // Delegation an interne Subkomponente
        return authService.validateCredentials(username, password);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1a2b
- **Vorgänger / Parent:** [[Konnektoren]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
