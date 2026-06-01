---
id: 044625af-9fff-4492-bd60-0f9e82665838
title: "Sicherheitsprotokolle"
date: 2026-06-01
tags:
  - verteilte_systeme
  - sicherheit
  - netzwerk
  - kommunikation
  - middleware
  - verschlüsselung
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Sicherheitsprotokolle]]

- **Kernkonzept:** Sicherheitsprotokolle sind standardisierte Verfahren in [[verteiltes System|verteilten Systemen]], die den sicheren Austausch von [[Nachricht|Nachrichten]] und [[Daten|Daten]] zwischen [[Kommunikationspartner|Kommunikationspartnern]] gewährleisten, indem sie [[Vertraulichkeit]], [[Integrität]] und [[Authentizität]] sicherstellen.
- **Nutzen & Zweck:** Sie existieren, um [[Angriff|Angriffe]] wie [[Abhören]], [[Manipulation]] oder [[Identitätsdiebstahl]] in [[Netzwerk|Netzwerken]] zu verhindern und [[Kommunikation]] in unsicheren Umgebungen zu ermöglichen. Ohne sie wären [[Datenübertragung|Datenübertragungen]] in [[verteiltes System|verteilten Systemen]] anfällig für [[Sicherheitslücke|Sicherheitslücken]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn keine sensiblen [[Daten]] übertragen werden oder wenn der [[Overhead]] durch Verschlüsselung und Authentifizierung die [[Performance]] unnötig beeinträchtigt. Alternativen wie ungesicherte [[Protokoll|Protokolle]] (z. B. UDP) sind schneller, aber unsicher. Sicherheitsprotokolle ersetzen keine [[Firewall|Firewalls]] oder [[Zugriffskontrolle|Zugriffskontrollen]], sondern ergänzen sie.
- **Beispiel / Code:** Ein klassisches Beispiel ist TLS (Transport Layer Security), das in HTTPS verwendet wird:
```
// Vereinfachtes TLS-Handshake-Beispiel (Pseudocode)
Client -> Server: ClientHello (unterstützte Verschlüsselungsverfahren)
Server -> Client: ServerHello (ausgewähltes Verfahren) + Zertifikat
Client: Verifiziert Zertifikat, generiert Sitzungsschlüssel
Client -> Server: Verschlüsselter Sitzungsschlüssel
// Ab hier: Verschlüsselte Kommunikation
```
