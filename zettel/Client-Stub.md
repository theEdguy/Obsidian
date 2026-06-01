---
id: db5efd57-284b-4eb0-b658-93f2c6948dc1
title: "Client-Stub"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - rpc
  - middleware
  - client-server
  - transparenz
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Client-Stub]]

- **Kernkonzept:** Ein [[Client-Stub|Client-Stub]] ist eine clientseitige Softwarekomponente, die als lokaler Stellvertreter für einen entfernten [[Server|Server]] fungiert und [[Verteilungstransparenz|Verteilungstransparenzen]] wie [[Zugriffstransparenz]] oder [[Ortstransparenz]] ermöglicht.
- **Nutzen & Zweck:** Der [[Client-Stub|Client-Stub]] löst das Problem der Komplexität in [[verteilten Systemen|verteilten Systemen]], indem er die Kommunikation mit entfernten [[Dienst|Diensten]] vereinfacht. Er kapselt Netzwerkdetails, serialisiert [[Aufruf|Aufrufe]] und ermöglicht [[Replikationstransparenz]] durch Steuerung replizierter Requests.
- **Abgrenzung & Grenzen:** Ein [[Client-Stub|Client-Stub]] sollte nicht genutzt werden, wenn die [[Latenz]] der Netzwerkkommunikation kritisch ist oder wenn [[Zustandslosigkeit]] des Servers erforderlich ist. Alternativen wie direkte [[Socket-Programmierung]] oder [[Middleware]]-basierte Lösungen (z. B. [[Message-Oriented Middleware]]) können in solchen Fällen effizienter sein.
- **Beispiel / Code:** Ein Beispiel für einen [[Client-Stub|Client-Stub]] in Java (RPC-basiert):

```java
// Generierter Stub für einen entfernten Dienst
public class CalculatorStub implements Calculator {
    private RemoteConnection connection;
    
    public int add(int a, int b) {
        Request request = new Request("add", a, b);
        Response response = connection.send(request);
        return response.getResult();
    }
}
```

Der Stub serialisiert den [[Aufruf|Aufruf]] `add(a, b)`, sendet ihn an den Server und deserialisiert die Antwort.
