---
id: d14c9d5e-4c99-4314-8baf-a8535d6db0d6
title: "Mobile Computing"
date: 2026-06-01
tags:
  - verteilte_systeme
  - mobilität
  - virtualisierung
  - client-server
  - code_migration
  - netzwerk
  - cloud_computing
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Mobile Computing]]

- **Kernkonzept:** Mobile Computing bezeichnet die Nutzung von [[Rechenleistung|Rechenleistungen]] und [[Datenverarbeitung|Datenverarbeitungen]] auf tragbaren [[Gerät|Geräten]], um ortsunabhängig auf [[Dienst|Dienste]] und [[Ressource|Ressourcen]] in [[Verteilte Systeme|verteilten Systemen]] zuzugreifen. Es kombiniert [[Virtualisierung]], [[Client-Server-Architektur|Client-Server-Architekturen]] und [[Code-Migration]] zur Optimierung von [[Leistung|Leistungen]] und [[Energieeffizienz|Energieeffizienzen]].
- **Nutzen & Zweck:** Mobile Computing löst das Problem der ortsgebundenen [[Datenverarbeitung]] und ermöglicht flexible, dynamische [[Nutzung|Nutzungen]] von [[Ressource|Ressourcen]] in [[Netzwerk|Netzwerken]]. Es verbessert die [[Verfügbarkeit]] von [[Dienst|Diensten]], reduziert [[Latenz|Latenzen]] durch lokale [[Verarbeitung]] und unterstützt [[Lastverteilung]] in [[Cloud-Umgebung|Cloud-Umgebungen]].
- **Abgrenzung & Grenzen:** Mobile Computing ist nicht geeignet für [[Anwendung|Anwendungen]], die hohe [[Rechenleistung|Rechenleistungen]] oder dauerhafte [[Netzwerkverbindung|Netzwerkverbindungen]] erfordern. Im Vergleich zu stationären [[System|Systemen]] sind [[Energieverbrauch]], [[Sicherheit]] und [[Datenkonsistenz]] kritische Herausforderungen. Alternativen wie [[Edge Computing]] oder [[Fog Computing]] können in bestimmten Szenarien effizienter sein.
- **Beispiel / Code:** Ein Beispiel für Mobile Computing ist die Nutzung von [[Progressive Web App|Progressive Web Apps (PWAs)]], die clientseitigen Code dynamisch laden und lokal ausführen:

```javascript
// Dynamisches Laden von clientseitigem Code für eine PWA
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/sw.js').then(function(registration) {
    console.log('ServiceWorker registration successful');
  }).catch(function(err) {
    console.log('ServiceWorker registration failed: ', err);
  });
}
```

Dies ermöglicht [[Offline-Funktionalität|Offline-Funktionalitäten]] und reduziert die Abhängigkeit von [[Server|Servern]].
