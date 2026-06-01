---
id: 0b1beb92-7541-4fc3-a0a4-47d60bafb24a
title: "Dynamische Port-Zuweisung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - server-architektur
  - verteilte-systeme
  - kommunikation
  - port-management
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Dynamische Port-Zuweisung]]

- **Kernkonzept:** Die dynamische Port-Zuweisung ermöglicht es [[Server|Servern]], [[Endpunkt|Endpunkte]] für [[Kommunikation|Kommunikationen]] zur Laufzeit zu registrieren und [[Client|Clients]] diese Informationen bereitzustellen, statt feste [[Port|Ports]] zu verwenden.
- **Nutzen & Zweck:** Sie löst das Problem der [[Skalierbarkeit|Skalierbarkeits]]- und [[Flexibilität|Flexibilitäts]]-Einschränkungen bei der Nutzung statischer [[Port|Ports]], indem sie [[Dienst|Dienste]] dynamisch verfügbar macht und [[Konflikt|Konflikte]] bei der [[Port|Port]]-Nutzung vermeidet. Besonders relevant in [[Verteilte Systeme|verteilten Systemen]] und [[Cloud Computing|Cloud-Computing]]-Umgebungen.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[System|Systeme]], die feste [[Port|Ports]] für [[Sicherheit|Sicherheits]]- oder [[Konfiguration|Konfigurations]]-Zwecke benötigen (z. B. Firewall-Regeln). Unterscheidet sich von statischen [[Port|Ports]], die einfacher zu verwalten, aber weniger flexibel sind. In [[Echtzeit-Systeme|Echtzeit-Systemen]] kann die dynamische Zuweisung zu [[Latenz|Latenzen]] führen.
- **Beispiel / Code:** Ein typischer Ablauf in einem Unix-basierten System:
1. Ein [[Daemon]] (z. B. `inetd` oder `systemd`) lauscht auf einem bekannten [[Port]] (z. B. Port 111 für RPC).
2. Ein [[Client]] fragt den [[Daemon]] nach dem [[Endpunkt]] eines [[Dienst|Dienstes]] (z. B. via RPC).
3. Der [[Daemon]] startet den [[Server]]-Prozess, weist ihm einen freien [[Port]] zu und gibt diesen an den [[Client]] zurück.
4. Der [[Client]] kommuniziert direkt mit dem [[Server]] über den zugewiesenen [[Port]].

Beispiel-Code (Pseudocode):
```
// Server-Seite
port = get_free_port();
register_service("mein_dienst", port);
start_server(port);

// Client-Seite
port = lookup_service("mein_dienst");
connect_to_server(port);
```
