---
id: 998fd07c-df5f-4724-9f20-4e37425433a9
title: "Verteiltes System"
date: 2026-06-01
tags:
  - verteilte_systeme
  - grundlagen
  - architektur
  - systemdesign
  - netzwerk
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Verteiltes System]]

- **Kernkonzept:** Ein [[verteiltes System]] besteht aus einer Sammlung [[autonomes Rechenelement|autonomer Rechenelemente]] (auch [[Knoten]] genannt), die ihren Nutzern als ein einzelnes, kohärentes [[System]] erscheinen, obwohl sie unabhängig voneinander operieren und über ein [[Netzwerk]] kommunizieren. Die [[Knoten]] arbeiten zusammen, um eine einheitliche Funktionalität zu bieten, wobei [[Autonomie]] und [[Heterogenität]] zentrale Eigenschaften darstellen.
- **Nutzen & Zweck:** Ein [[verteiltes System]] ermöglicht die [[Skalierbarkeit]], [[Fehlertoleranz]] und effiziente [[Ressourcenteilung]] in [[System|Systemen]], indem [[autonomes Rechenelement|autonome Rechenelemente]] kooperieren und zentrale Engpässe vermeiden. Es unterstützt die Integration heterogener [[Hardware]] und [[Software]] und bildet die Grundlage für moderne Anwendungen wie [[Cloud Computing]], [[Peer-to-Peer-Systeme]], [[Content-Delivery-Netzwerk|Content-Delivery-Netzwerke]] oder [[Cloud-Speicherdienst|Cloud-Speicherdienste]]. Durch die dezentrale Struktur können [[Lastverteilung]] und [[Redundanz]] realisiert werden, was die [[Ausfallsicherheit]] erhöht und die gemeinsame Nutzung von [[Ressource|Ressourcen]] optimiert.
- **Abgrenzung & Grenzen:** Ein [[verteiltes System]] ist nicht geeignet für Anwendungen, die strikte [[Echtzeitanforderung|Echtzeitanforderungen]], deterministische [[Synchronisation]] oder starke [[Konsistenz]] erfordern, da [[autonomes Rechenelement|autonome Rechenelemente]] keine globale [[Uhr]] besitzen und [[Netzwerk]]-Latenzen die [[Koordination]] erschweren. Im Vergleich zu [[monolithisches System|monolithischen Systemen]] oder [[zentralisiertes System|zentralisierten Systemen]] ist die Komplexität der [[Konsistenzsicherung]], [[Fehlererkennung]] und [[Sicherheit]] deutlich höher. Zudem erfordern [[verteilte Algorithmen]] wie das [[Paxos-Protokoll]] oder [[Raft-Protokoll]] zusätzlichen Aufwand zur Gewährleistung der [[Korrektheit]]. Partielle [[Ausfall|Ausfälle]] und [[Netzwerk]]-Latenzen können die Leistung beeinträchtigen, insbesondere in Szenarien mit hohen Anforderungen an [[Konsistenz]] oder [[Echtzeitfähigkeit]].
- **Beispiel / Code:** Ein klassisches Beispiel für ein [[verteiltes System]] ist das [[World Wide Web]], bei dem [[Server|autonome Server]] und [[Client]]-Geräte über das [[Internet]] kommunizieren, um Nutzern eine einheitliche Sicht auf Informationen zu bieten. Ein weiteres Beispiel ist ein [[Content-Delivery-Netzwerk]] (CDN), das geografisch verteilte [[Server]] nutzt, um Inhalte mit minimaler Latenz bereitzustellen. Zudem illustriert ein [[Cloud-Speicherdienst]] wie Dropbox die Replikation von Dateien auf mehreren [[Server|Servern]], um [[Verfügbarkeit]] und Zugriffsgeschwindigkeit zu gewährleisten:

```java
// Vereinfachtes Beispiel: Client-Anfrage an ein CDN mit Replikation
public class CDNClient {
    private List<CDNServer> servers;

    public String fetchContent(String contentId) {
        CDNServer optimalServer = findOptimalServer();
        return optimalServer.retrieveContent(contentId);
    }

    private CDNServer findOptimalServer() {
        // Algorithmus zur Auswahl des nächstgelegenen Servers
        return servers.stream()
                .min(Comparator.comparing(s -> s.getLatency()))
                .orElseThrow(() -> new RuntimeException("Kein Server verfügbar"));
    }

    public void replicateContent(String contentId, String content) {
        // Replikation auf mehrere Server für Redundanz
        servers.forEach(server -> server.storeContent(contentId, content));
    }
}
```

Das Beispiel zeigt, wie ein [[Client]] den optimalen [[Server]] auswählt, um die [[Latenz]] zu minimieren, und wie Inhalte auf mehreren [[Server|Servern]] repliziert werden, um [[Redundanz]] und [[Verfügbarkeit]] zu erhöhen. Die [[Lastverteilung]] und [[Ausfallsicherheit]] sind hier durch die Verteilung der [[Server]] und die Replikation der Daten implizit gegeben.
