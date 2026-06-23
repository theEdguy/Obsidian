---
id: 1124acfa-d65e-417d-b6a1-a28b53b46a1f
title: "Nebenläufigkeit"
date: 2026-06-23
tags:
  - software_engineering
  - parallelität
  - synchronisation
  - architektur
  - draft
source: "software_engineering_kapitel_12"
---

# [[Nebenläufigkeit]]

- **Kernkonzept:** Nebenläufigkeit bezeichnet die Fähigkeit eines Systems, mehrere Aufgaben gleichzeitig oder quasi-gleichzeitig auszuführen, indem Prozesse oder Threads parallel abgearbeitet werden. Dies ermöglicht eine effizientere Nutzung von Ressourcen, insbesondere in Mehrkernprozessoren, und verbessert die Reaktionsfähigkeit von Anwendungen.
- **Nutzen & Zweck:** Nebenläufigkeit löst das Problem der Blockierung von Anwendungen durch langlaufende Operationen, indem sie diese in separate Ausführungseinheiten (Threads) unterteilt. Dadurch können Systeme reaktionsschneller gestaltet werden, z. B. in Benutzeroberflächen, die während Hintergrundberechnungen bedienbar bleiben. Zudem ermöglicht sie die Skalierung von Anwendungen, indem mehrere Anfragen oder Aufgaben parallel verarbeitet werden, was die Gesamtleistung steigert.
- **Abgrenzung & Grenzen:** Nebenläufigkeit sollte nicht eingesetzt werden, wenn die Aufgaben stark voneinander abhängig sind oder komplexe Synchronisationsmechanismen erfordern, da dies zu Race Conditions, Deadlocks oder unvorhersehbarem Verhalten führen kann. Alternativen wie sequentielle Verarbeitung oder asynchrone Programmierung (z. B. mit Callbacks oder Promises) sind oft einfacher zu implementieren und zu warten, wenn keine echte Parallelität benötigt wird. Zudem erhöht Nebenläufigkeit die Komplexität des Codes und erfordert sorgfältige Planung der Ressourcenverwaltung.
- **Beispiel / Code:** ```java
public class Counter {
    private int count = 0;
    
    // Synchronisierte Methode zur Vermeidung von Race Conditions
    public synchronized void increment() {
        count++;
    }
    
    public int getCount() {
        return count;
    }
}

// Verwendung in mehreren Threads
public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();
        
        Runnable task = () -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        };
        
        Thread thread1 = new Thread(task);
        Thread thread2 = new Thread(task);
        
        thread1.start();
        thread2.start();
        
        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        
        System.out.println("Final count: " + counter.getCount()); // Erwartet: 2000
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2c2
- **Vorgänger / Parent:** [[Schnittstellenverwaltung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Fassaden-Pattern]]
  - [[Synchronisation]]
