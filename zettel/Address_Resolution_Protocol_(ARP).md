---
id: 004e12d6-5222-4531-b553-900f396de6c3
title: "Address Resolution Protocol (ARP)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - benennung
  - protokoll
  - datenverbindungsschicht
  - kommunikation
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Address Resolution Protocol (ARP)]]

- **Kernkonzept:** Das [[Address Resolution Protocol|ARP]] löst die [[Adresse|Adressen]]-Auflösung in lokalen [[Netzwerk|Netzwerken]] und bildet [[IP-Adresse|IP-Adressen]] auf [[MAC-Adresse|MAC-Adressen]] ab, um die Kommunikation zwischen [[Gerät|Geräten]] zu ermöglichen.
- **Nutzen & Zweck:** ARP löst das [[Problem]] der [[Namensauflösung]] in [[LAN|Lokalen Netzwerken]], indem es [[Bezeichner|technische Adressen]] (IP) in physische [[Adresse|Adressen]] (MAC) übersetzt. Ohne ARP könnten [[Gerät|Geräte]] keine direkte [[Kommunikation]] auf der [[Datenverbindungsschicht]] aufbauen.
- **Abgrenzung & Grenzen:** ARP ist auf [[LAN|lokale Netzwerke]] beschränkt und skaliert nicht für größere [[Netzwerk|Netzwerke]] wie das Internet. Alternativen wie [[DNS]] oder [[verteilte Hash-Tabelle|verteilte Hash-Tabellen]] (z. B. [[Chord]]) sind für hierarchische oder globale [[Namensauflösung]] besser geeignet. ARP ist zudem anfällig für [[Sicherheitslücke|Sicherheitslücken]] wie [[ARP-Spoofing]].
- **Beispiel / Code:** Ein typischer ARP-Request in einem lokalen Netzwerk:

1. Gerät A sendet einen Broadcast: "Wer hat die IP-Adresse 192.168.1.10?"
2. Gerät B (mit IP 192.168.1.10) antwortet direkt an Gerät A: "Meine MAC-Adresse ist 00:1A:2B:3C:4D:5E".

Der ARP-Cache von Gerät A speichert diese Zuordnung für zukünftige [[Kommunikation]].
