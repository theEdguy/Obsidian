---
id: ccf9b5c4-4d04-42f2-9a76-c59d96041b6b
title: "Multithreaded Clients"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - threads
  - netzwerk
  - parallelisierung
  - client-server
  - performance
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Multithreaded Clients]]

- **Kernkonzept:** Ein [[Multithreaded Client|Multithreaded Client]] nutzt mehrere [[Thread|Threads]] innerhalb eines [[Prozess|Prozesses]], um Netzwerklatenz zu verbergen und parallele [[Request|Requests]] an [[Server|Server]] zu senden. Dadurch können blockierende [[Operation|Operationen]] (z. B. [[E/A-Operation|E/A-Operationen]]) überlappt werden.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der ineffizienten Auslastung von [[Client|Clients]] bei blockierenden [[Netzwerkoperation|Netzwerkoperationen]]. Es ermöglicht parallele [[Kommunikation]] mit mehreren [[Server|Servern]], versteckt [[Latenz]] und verbessert die [[Antwortzeit]] durch gleichzeitige Abarbeitung mehrerer [[Aufgabe|Aufgaben]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Thread-Synchronisation]] zu komplex wird oder [[Race Condition|Race Conditions]] schwer vermeidbar sind. Alternativen wie [[Singlethreaded Client|Singlethreaded Clients]] mit nicht-blockierenden [[Aufruf|Aufrufen]] oder [[Event Loop|Event Loops]] können einfacher sein. [[Multithreaded Clients]] erfordern mehr [[Ressource|Ressourcen]] und sind anfälliger für [[Fehler]] durch geteilten [[Adressraum]].
- **Beispiel / Code:** ```java
// Beispiel: Multithreaded HTTP-Requests in Java
ExecutorService executor = Executors.newFixedThreadPool(5);
List<Future<String>> futures = new ArrayList<>();

for (String url : urls) {
    futures.add(executor.submit(() -> {
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
        return client.send(request, HttpResponse.BodyHandlers.ofString()).body();
    }));
}

for (Future<String> future : futures) {
    System.out.println(future.get()); // Ergebnisse sammeln
}
executor.shutdown();
```
