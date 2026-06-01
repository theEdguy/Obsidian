---
id: 9cca5a1b-a917-4758-a3e0-4bb9f85bce10
title: "Service-orientierte Architekturen (SOA)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - service-orientierung
  - integration
  - software-engineering
  - enterprise-architecture
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Service-orientierte Architekturen (SOA)]]

- **Kernkonzept:** Service-orientierte [[Architektur|Architekturen]] (SOA) sind ein [[Architekturstil|Architekturstil]], bei dem [[Anwendung|Anwendungen]] aus lose gekoppelten, wiederverwendbaren [[Service|Services]] bestehen, die über standardisierte [[Schnittstelle|Schnittstellen]] kommunizieren.
- **Nutzen & Zweck:** SOA löst das [[Problem]] der starren, monolithischen [[System|Systeme]], indem es [[Flexibilität]], [[Skalierbarkeit]] und [[Wiederverwendbarkeit]] von [[Komponente|Komponenten]] ermöglicht. Es fördert die [[Integration]] heterogener [[Systeme]] und unterstützt [[Geschäftsprozess|Geschäftsprozesse]] durch modulare [[Service|Services]].
- **Abgrenzung & Grenzen:** SOA ist nicht geeignet für [[Anwendung|Anwendungen]] mit hohen [[Performance|Performanceanforderungen]] oder starker [[Kopplung]] der [[Komponente|Komponenten]]. Im Vergleich zu [[Microservice|Microservices]] ist SOA oft schwerfälliger und weniger granular. Alternativen wie [[REST]]-basierte [[Architektur|Architekturen]] oder [[Event-driven Architecture|ereignisgesteuerte Architekturen]] können in bestimmten [[Szenario|Szenarien]] besser geeignet sein.
- **Beispiel / Code:** Ein Beispiel für eine SOA-Implementierung ist ein [[E-Commerce-System]], das aus separaten [[Service|Services]] besteht:

1. **Benutzerverwaltung** (Authentifizierung, Profilmanagement)
2. **Produktkatalog** (Suche, Filterung)
3. **Bestellabwicklung** (Warenkorb, Checkout)
4. **Zahlungsabwicklung** (Schnittstelle zu Payment-Providern)

Die [[Service|Services]] kommunizieren über [[SOAP]] oder [[REST]]-[[Schnittstelle|Schnittstellen]], z. B.:
```
// Aufruf des Produktkatalog-Service via REST
GET /api/products?category=books HTTP/1.1
Host: catalog-service.example.com
```
