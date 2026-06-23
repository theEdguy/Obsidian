---
id: 01e51811-049b-487c-843b-05593f6f7999
title: "Datenzugriffsschicht"
date: 2026-06-23
tags:
  - software_engineering
  - schicht
  - daten
  - draft
source: "software_engineering_kapitel_10"
---

# [[Datenzugriffsschicht]]

- **Kernkonzept:** Die Datenzugriffsschicht (auch Persistenzschicht genannt) ist eine dedizierte Schicht in der Softwarearchitektur, die den Zugriff auf externe Datenquellen wie Datenbanken, Dateisysteme oder Netzwerkdienste kapselt und die darüberliegende Logikschicht von technischen Details der Datenspeicherung entkoppelt.
- **Nutzen & Zweck:** Die Datenzugriffsschicht existiert, um die Komplexität der Datenspeicherung und -abfrage von der Geschäftslogik zu trennen. Sie löst das Problem der Vermischung von domänenspezifischer Logik mit technischen Details wie SQL-Abfragen, Dateizugriffen oder API-Aufrufen. Dadurch wird die Wartbarkeit, Testbarkeit und Austauschbarkeit von Datenquellen verbessert, ohne die Logikschicht anpassen zu müssen.
- **Abgrenzung & Grenzen:** Die Datenzugriffsschicht sollte nicht genutzt werden, wenn die Anwendung keine persistenten Daten benötigt oder wenn die Datenhaltung trivial ist (z. B. bei kleinen Skripten oder Prototypen). Alternativen wie direkte Datenbankzugriffe in der Logikschicht führen zwar zu schnellerer Entwicklung, verstoßen jedoch gegen das Prinzip der Trennung von Verantwortlichkeiten und erschweren spätere Änderungen. Im Gegensatz zur Logikschicht, die Geschäftsregeln implementiert, oder zur Präsentationsschicht, die Benutzeroberflächen verwaltet, konzentriert sich die Datenzugriffsschicht ausschließlich auf die technische Interaktion mit Datenquellen.
- **Beispiel / Code:** ```java
// Beispiel: Datenzugriffsschicht mit JDBC (vereinfacht)
public class MemberRepository {
    private final Connection databaseConnection;

    public MemberRepository(Connection databaseConnection) {
        this.databaseConnection = databaseConnection;
    }

    public Member findById(int id) throws SQLException {
        String sql = "SELECT * FROM members WHERE id = ?";
        try (PreparedStatement stmt = databaseConnection.prepareStatement(sql)) {
            stmt.setInt(1, id);
            ResultSet rs = stmt.executeQuery();
            if (rs.next()) {
                return new Member(rs.getInt("id"), rs.getString("name"));
            }
        }
        return null;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2a3
- **Vorgänger / Parent:** [[Drei-Schichtenmodell]]
- **Folgezettel / Unterzettel:**
  - [[Persistenz]]
  - [[Datenbankanbindung]]
- **Querverweise:** keine
