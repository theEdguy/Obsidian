---
id: 7e2355d9-3a0f-43a6-a804-1319c0bf189d
title: "Client-Server"
date: 2026-06-23
tags:
  - software_engineering
  - client-server
  - architektur
  - draft
source: "software_engineering_kapitel_07"
---

# [[Client-Server]]

- **Kernkonzept:** Das Client-Server-Konzept ist ein Architekturmodell in der Softwareentwicklung, bei dem Aufgaben und Dienstleistungen zwischen Anbietern (Servern) und Nachfragern (Clients) aufgeteilt werden. Der Server stellt Ressourcen oder Funktionen bereit, während der Client diese über ein Netzwerk anfragt und nutzt.
- **Nutzen & Zweck:** Dieses Konzept existiert, um verteilte Systeme effizient zu gestalten und zentrale Ressourcenverwaltung zu ermöglichen. Es löst das Problem der Skalierbarkeit, Wartbarkeit und Lastverteilung, indem es die Verantwortlichkeiten zwischen Client und Server klar trennt. Dadurch können mehrere Clients gleichzeitig auf gemeinsame Ressourcen zugreifen, ohne dass jeder Client diese lokal vorhalten muss, was die Konsistenz und Aktualität der Daten sicherstellt.
- **Abgrenzung & Grenzen:** Das Client-Server-Modell sollte nicht genutzt werden, wenn eine direkte Peer-to-Peer-Kommunikation ohne zentrale Instanz erforderlich ist, z. B. in Echtzeit-Anwendungen mit hohen Latenzanforderungen oder in dezentralen Netzwerken wie Blockchain-Systemen. Alternativen wie Peer-to-Peer-Architekturen bieten hier mehr Flexibilität und Ausfallsicherheit. Zudem ist das Modell ungeeignet für Systeme mit extrem hohen Anforderungen an die Offline-Verfügbarkeit, da Clients ohne Netzwerkverbindung nicht auf Server-Ressourcen zugreifen können.
- **Beispiel / Code:** ```java
// Einfaches Beispiel: Client-Anfrage an einen Server in Java (HTTP)
import java.io.*;
import java.net.*;

public class SimpleClient {
    public static void main(String[] args) {
        try {
            Socket socket = new Socket("localhost", 8080);
            PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
            BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            
            out.println("GET /data HTTP/1.1");
            String response = in.readLine();
            System.out.println("Server-Antwort: " + response);
            
            socket.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b3
- **Vorgänger / Parent:** [[Architekturstil]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Architekturstil]]
