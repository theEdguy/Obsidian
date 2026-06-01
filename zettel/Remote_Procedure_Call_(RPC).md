---
id: ebe5f368-87d1-409a-a6a3-bb1c9fb3acc2
title: "Remote Procedure Call (RPC)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - kommunikation
  - netzwerk
  - protokolle
  - middleware
  - synchronisation
  - client-server
  - abstraktion
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Remote Procedure Call (RPC)]]

- **Kernkonzept:** Remote Procedure Call (RPC) ermöglicht den Aufruf von [[Prozedur|Prozeduren]] oder [[Funktion|Funktionen]] auf entfernten [[System|Systemen]], als wären sie lokal verfügbar. Es abstrahiert die [[Netzwerkkommunikation]] in [[Verteilte Systeme|verteilten Systemen]] und verbirgt die Komplexität der [[Interaktion|Interaktionen]] zwischen verteilten [[Komponente|Komponenten]], indem es eine synchrone, prozedurale [[Schnittstelle]] bereitstellt.
- **Nutzen & Zweck:** RPC löst das [[Problem]] der manuellen Implementierung von [[Netzwerkprogrammierung|Netzwerkkommunikation]] zwischen [[Prozess|Prozessen]] auf verschiedenen [[Rechner|Rechnern]] und reduziert die [[Komplexität]] bei der Entwicklung verteilter Anwendungen. Es ermöglicht [[Verteilungstransparenz]] (z. B. [[Ortstransparenz]], [[Zugriffstransparenz]] und [[Fehlertransparenz]]) und erleichtert die [[Entwicklung]] von [[Client-Server-Architektur|Client-Server-Architekturen]], indem es lokale und entfernte [[Aufruf|Aufrufe]] vereinheitlicht. Durch die Kapselung von [[Latenz]] und [[Fehlerbehandlung]] im Netzwerk wird die [[Nebenläufigkeit]] und [[Synchronisation]] in verteilten [[System|Systemen]] handhabbarer.
- **Abgrenzung & Grenzen:** RPC sollte nicht genutzt werden, wenn [[Latenz]] kritisch ist (z. B. in [[Echtzeitsystem|Echtzeitsystemen]]) oder wenn asynchrone [[Kommunikation]] oder [[Lose_Kopplung|lose Kopplung]] erforderlich ist, wie in [[Event-driven Architecture|ereignisgesteuerten Architekturen]]. Alternativen wie [[Message-Passing]], [[REST]] oder [[GraphQL]] sind besser geeignet für [[Skalierbarkeit|skalierbare]], zustandslose oder [[Webservice|Web-basierte]] [[Systeme]]. RPC kann bei hoher [[Netzwerklatenz]] oder instabilen Verbindungen zu [[Performance|Performance-Problemen]] führen und ist weniger flexibel als [[REST]] oder [[GraphQL]] bei der [[Datenübertragung]] in modernen [[Webservice|Webservices]]. Zudem erfordert RPC oft spezifische [[Middleware]] wie [[Stub (RPC)|Stubs]] oder [[Proxy (Entwurfsmuster)|Proxies]], was die [[Integration]] in heterogene [[Systeme]] erschweren kann.
- **Beispiel / Code:** RPC kann in verschiedenen Sprachen und Frameworks implementiert werden. Hier zwei Beispiele:

**1. Einfacher RPC-Aufruf in Go (gRPC):**
```go
// Server-Seite (Definition der Prozedur)
package main

type CalculatorServer struct {
    pb.UnimplementedCalculatorServer
}

func (s *CalculatorServer) Add(ctx context.Context, req *pb.AddRequest) (*pb.AddResponse, error) {
    return &pb.AddResponse{Result: req.A + req.B}, nil
}

// Client-Seite (Aufruf der entfernten Prozedur)
func main() {
    conn, _ := grpc.Dial("localhost:50051", grpc.WithInsecure())
    client := pb.NewCalculatorClient(conn)
    response, _ := client.Add(context.Background(), &pb.AddRequest{A: 3, B: 4})
    fmt.Println(response.Result) // Ausgabe: 7
}
```

**2. Einfaches RPC-Beispiel in Python mit `xmlrpc`:**
```python
# Server-Code
from xmlrpc.server import SimpleXMLRPCServer

def add(a, b):
    return a + b

server = SimpleXMLRPCServer(('localhost', 8000))
server.register_function(add, 'add')
server.serve_forever()

# Client-Code
import xmlrpc.client

proxy = xmlrpc.client.ServerProxy('http://localhost:8000/')
result = proxy.add(5, 3)
print(result)  # Ausgabe: 8
```

Beide Beispiele zeigen, wie der [[Client]] eine entfernte [[Funktion]] aufruft, als wäre sie lokal definiert. gRPC nutzt dabei [[HTTP/2]] für effiziente [[Datenübertragung]], während `xmlrpc` auf [[HTTP]] und [[XML]] basiert.
