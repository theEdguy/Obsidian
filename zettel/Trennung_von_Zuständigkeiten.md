---
id: 3a90a413-f080-4631-ba52-3aba9b62719b
title: "Trennung_von_Zuständigkeiten"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - softwarearchitektur
  - clean_code
  - prinzipien
  - design
  - draft
source: "SWE Slides (Folien 226-240)"
---

# [[Trennung_von_Zuständigkeiten]]

- **Kernkonzept:** Die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] (Separation of Concerns) ist ein [[Designprinzip]] der [[Softwareentwicklung]], das besagt, dass jede [[Komponente]] oder jedes [[Modul]] einer [[Anwendung]] genau eine klar definierte Aufgabe erfüllen sollte. Dies fördert die [[Modularität]] und reduziert die [[Komplexität]] durch klare [[Schnittstelle|Schnittstellen]].
- **Nutzen & Zweck:** Die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] löst das Problem der [[Komplexität]] und [[Unwartbarkeit]] von [[Code]] durch die Schaffung klar abgegrenzter [[Komponente|Komponenten]] mit hoher [[Kohäsion]]. Sie verbessert die [[Wartbarkeit]], erleichtert die [[Wiederverwendbarkeit]] und ermöglicht eine einfachere [[Fehlerisolierung]]. Zudem unterstützt sie die [[Lose_Kopplung|lose Kopplung]] zwischen [[Modul|Modulen]], was die [[Skalierbarkeit]] und [[Testbarkeit]] von [[System|Systemen]] erhöht.
- **Abgrenzung & Grenzen:** Die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] ist nicht immer sinnvoll für sehr kleine [[Anwendung|Anwendungen]], bei denen der Aufwand für die [[Modularität]] unnötigen Overhead verursacht. Eine zu feingranulare [[Zerlegung]] kann zudem zu übermäßiger Fragmentierung führen und die [[Lesbarkeit]] des [[Code|Codes]] beeinträchtigen. In [[Monolithische_Architektur|monolithischen Architekturen]] mit geringer [[Komplexität]] kann der Nutzen der Trennung begrenzt sein. Sie unterscheidet sich von [[Monolithische_Architektur|monolithischen Ansätzen]] durch die Betonung der [[Modularität]] und [[Schnittstelle|Schnittstellen]].
- **Beispiel / Code:** ```java
// Schlecht: Vermischung von Zuständigkeiten (Datenhaltung, Logik, Präsentation)
public class UserManager {
    public void saveUserToDatabase(User user) { /* ... */ }
    public void sendWelcomeEmail(User user) { /* ... */ }
    public void displayUserName(User user) {
        System.out.println(user.getName());
    }
}

// Gut: Trennung von Zuständigkeiten (Datenhaltung, Logik, Präsentation)
public class User {
    private String name; // Datenhaltung
    
    public String getName() { // Logik
        return name;
    }
}

public class UserRepository {
    public void saveUser(User user) { /* ... */ }
}

public class EmailService {
    public void sendWelcomeEmail(User user) { /* ... */ }
}

public class UserDisplay { // Präsentation
    public void showName(String name) {
        System.out.println(name);
    }
}
```
