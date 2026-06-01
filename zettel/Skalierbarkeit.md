---
id: 8d81ebea-cff6-4c42-aecd-ae5e8fc0aec6
title: "Skalierbarkeit"
date: 2026-06-01
tags:
  - verteilte_systeme
  - grundlagen
  - performance
  - systemdesign
  - architektur
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Skalierbarkeit]]

- **Kernkonzept:** Die Fähigkeit eines [[verteilten_Systems|verteilten Systems]], mit wachsender [[Last]] (z. B. mehr [[Nutzer]], größere [[Datenmenge|Datenmengen]] oder geografische Verteilung) effizient umzugehen, indem die [[Leistung]] durch Hinzufügen von [[Ressource|Ressourcen]] proportional zur [[Last]] gesteigert wird, ohne die [[Funktionalität]] zu beeinträchtigen.
- **Nutzen & Zweck:** Skalierbarkeit ermöglicht es [[verteilten_Systemen|verteilten Systemen]], steigende Anforderungen wie wachsende [[Nutzer|Nutzerzahlen]], [[Datenmenge|Datenmengen]] oder [[Transaktion|Transaktionen]] ohne signifikante [[Performance]]-Einbußen zu bewältigen. Dies ist essenziell für die [[Verfügbarkeit]] und [[Zuverlässigkeit]] von Systemen, die global oder unter hoher [[Last]] betrieben werden, wie z. B. soziale Netzwerke, [[E-Commerce]]-Plattformen oder [[Cloud-Computing]]-Dienste.
- **Abgrenzung & Grenzen:** Nicht alle Systeme sind in allen Dimensionen linear skalierbar. Geografische Skalierbarkeit erfordert spezielle [[Protokoll|Protokolle]] für asynchrone [[Kommunikation]], während administrative Skalierbarkeit oft politische oder organisatorische Hürden aufweist. Zudem können globale [[Synchronisation]] oder Abhängigkeiten zwischen [[Komponente|Komponenten]] die Skalierbarkeit einschränken. Alternativen wie [[Replikation]], [[Partitionierung]] oder [[Caching]] müssen sorgfältig abgewogen werden, um [[Engpass|Engpässe]] zu vermeiden.
- **Beispiel / Code:** Ein soziales Netzwerk wie Facebook nutzt verschiedene Strategien zur Skalierung:

- **[[Load_Balancing]]:** Verteilung von [[Anfrage|Anfragen]] auf mehrere [[Server]] mittels Load Balancern.
- **[[Replikation]]:** Daten werden auf mehrere [[Rechenzentrum|Rechenzentren]] repliziert, um [[Latenz]] zu reduzieren und [[Ausfallsicherheit]] zu erhöhen.
- **[[Partitionierung]]:** Daten werden nach Regionen oder Nutzergruppen partitioniert, um die [[Last]] zu verteilen.
- **[[Caching]]:** Häufig abgerufene Daten werden in [[Cache|Caches]] wie Redis oder Memcached zwischengespeichert.

```java
// Beispiel: Load Balancer-Konfiguration (vereinfacht)
public class LoadBalancer {
    private List<Server> servers;
    private int currentIndex = 0;

    public Server getNextServer() {
        Server server = servers.get(currentIndex);
        currentIndex = (currentIndex + 1) % servers.size();
        return server;
    }
}
```

Ein [[E-Commerce]]-Shop könnte ähnlich vorgehen, indem er [[Anfrage|Anfragen]] auf mehrere [[Backend]]-Server verteilt und [[Datenbank|Datenbanken]] partitioniert, um die [[Last]] zu skalieren.
