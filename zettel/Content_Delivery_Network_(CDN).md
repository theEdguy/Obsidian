---
id: 758dd567-986f-43fc-99a6-0627dbeb4a33
title: "Content Delivery Network (CDN)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - verteilte-systeme
  - performance
  - caching
  - edge-computing
  - hybride-architektur
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Content Delivery Network (CDN)]]

- **Kernkonzept:** Ein [[Content Delivery Network|Content Delivery Network (CDN)]] ist eine verteilte [[Infrastruktur|Infrastruktur]] aus [[Edge-Server|Edge-Servern]], die [[Inhalt|Inhalte]] wie [[Webseite|Webseiten]], [[Bild|Bilder]] oder [[Video|Videos]] geografisch nah an [[Endnutzer|Endnutzer]] ausliefert, um [[Latenz|Latenzen]] zu reduzieren und die [[Verfügbarkeit]] zu erhöhen.
- **Nutzen & Zweck:** Ein [[CDN]] löst das [[Problem]] der langsamen [[Datenübertragung]] und hohen [[Serverlast]] bei global verteilten [[Nutzer|Nutzern]], indem es [[Inhalt|Inhalte]] über [[Cache|Caches]] an [[Edge-Server|Edge-Servern]] zwischenspeichert. Dadurch wird die [[Performance]] verbessert, die [[Skalierbarkeit]] erhöht und die [[Ausfallsicherheit]] gestärkt.
- **Abgrenzung & Grenzen:** Ein [[CDN]] ist nicht geeignet für [[Echtzeitanwendung|Echtzeitanwendungen]] mit dynamischen [[Inhalt|Inhalten]], die keine [[Caching|Caching-Strategien]] zulassen (z. B. [[Banktransaktion|Banktransaktionen]]). Im Vergleich zu [[Peer-to-Peer-System|Peer-to-Peer-Systemen]] (z. B. [[BitTorrent]]) fehlt die dezentrale [[Nutzerbeteiligung]], und im Gegensatz zu [[Super-Peer-Netzwerk|Super-Peer-Netzwerken]] ist es zentraler organisiert. Für kleine, lokale [[Anwendung|Anwendungen]] mit geringer [[Nutzerzahl]] ist ein [[CDN]] oft überdimensioniert.
- **Beispiel / Code:** Ein typisches [[CDN-Konfigurationsbeispiel]] für eine [[Webseite]] mit [[Nginx]] als [[Reverse-Proxy]]:

```nginx
proxy_cache_path /var/cache/nginx levels=1:2 keys_zone=my_cache:10m inactive=60m;

server {
    listen 80;
    server_name example.com;
    
    location / {
        proxy_cache my_cache;
        proxy_pass http://backend_server;
        proxy_cache_valid 200 302 10m;
        proxy_cache_valid 404 1m;
    }
}
```

Hier werden [[Statische Inhalte]] wie [[Bild|Bilder]] oder [[CSS-Datei|CSS-Dateien]] für 10 Minuten gecacht, um die [[Ladezeit]] zu optimieren.
