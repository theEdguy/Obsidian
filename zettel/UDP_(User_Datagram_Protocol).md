---
id: e1844c15-a590-42ab-8bfc-d16a085e94ac
title: "UDP (User Datagram Protocol)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - transportschicht
  - protokoll
  - verteilte-systeme
  - echtzeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[UDP (User Datagram Protocol)]]

- **Kernkonzept:** UDP ist ein [[Protokoll|Protokolle]] der [[Transportschicht]] im [[Netzwerk|Netzwerkmodell]], das eine unzuverlässige, verbindungslose [[Datagram|Datagram-Kommunikation]] ermöglicht. Es bietet eine einfache, effiziente Methode zum Versenden von [[Nachricht|Nachrichten]] ohne Garantie auf Auslieferung, Reihenfolge oder Fehlerfreiheit.
- **Nutzen & Zweck:** UDP löst das [[Problem]] der [[Latenz|hohen Latenz]] und des [[Overhead|Protokoll-Overheads]] in [[verteilte Systeme|verteilten Systemen]], indem es auf komplexe Mechanismen wie [[Flusskontrolle]], [[Fehlererkennung]] oder [[Wiederholungsübertragung]] verzichtet. Es eignet sich für Anwendungen, bei denen [[Echtzeitfähigkeit]] oder [[Skalierbarkeit]] wichtiger sind als [[Zuverlässigkeit]], z. B. bei [[Video-Streaming]], [[VoIP]] oder [[Online-Spiele|Online-Spielen]].
- **Abgrenzung & Grenzen:** UDP sollte nicht genutzt werden, wenn [[Datenintegrität]], [[Reihenfolge]] oder [[Auslieferungsgarantie]] kritisch sind – hier ist [[TCP]] die bessere Wahl. Im Gegensatz zu TCP fehlen UDP [[Verbindungsaufbau|Verbindungsmechanismen]], [[Bestätigung|Bestätigungsnachrichten]] und [[Pufferung]]. Es ist ungeeignet für [[Dateiübertragung|Dateiübertragungen]] oder [[Transaktion|Transaktionen]], bei denen [[Datenverlust]] nicht tolerierbar ist. Zudem bietet es keine [[Sicherheitsfunktion|eingebauten Sicherheitsfunktionen]] wie [[Verschlüsselung]].
- **Beispiel / Code:** Ein einfaches UDP-Beispiel in Python zum Versenden einer Nachricht:

```python
import socket

# UDP-Socket erstellen
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# Zieladresse und Port
server_address = ('localhost', 10000)
message = 'Hallo, UDP-Server!'

# Nachricht senden
sock.sendto(message.encode(), server_address)

# Auf Antwort warten
response, _ = sock.recvfrom(4096)
print('Empfangen:', response.decode())
```

Auf der Serverseite würde ein ähnlicher Socket auf eingehende [[Datagram|Datagramme]] warten, ohne eine [[Verbindung]] aufzubauen.
