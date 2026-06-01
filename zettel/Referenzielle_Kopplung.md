---
id: 0ee7f3cc-17c5-4fc7-9ce5-ab723afa3d99
title: "Referenzielle Kopplung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - kopplung
  - koordination
  - entwurfsmuster
  - publish-subscribe
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Referenzielle Kopplung]]

- **Kernkonzept:** Referenzielle Kopplung beschreibt die Abhängigkeit zwischen [[Komponente|Komponenten]] in [[Verteiltes System|verteilten Systemen]], bei der eine [[Komponente]] direkte Kenntnis (Referenz) einer anderen [[Komponente]] benötigt, um zu funktionieren. Dies führt zu einer engen Bindung zwischen [[Sender]] und [[Empfänger]].
- **Nutzen & Zweck:** Das Konzept dient der Analyse von [[Architekturstil|Architekturstilen]] und [[Koordinationsmechanismus|Koordinationsmechanismen]], um die Auswirkungen direkter Abhängigkeiten auf [[Skalierbarkeit]], [[Wartbarkeit]] und [[Fehlertoleranz]] in [[Verteiltes System|verteilten Systemen]] zu verstehen. Es hilft, [[Kopplung]] zu minimieren und [[Entkopplung]] zu fördern.
- **Abgrenzung & Grenzen:** Referenzielle Kopplung sollte vermieden werden, wenn [[Skalierbarkeit]] oder [[Flexibilität]] im Vordergrund stehen, da sie [[Änderung|Änderungen]] erschwert und [[Ausfall|Ausfälle]] propagieren kann. Alternativen wie [[Publish-Subscribe-Architektur|Publish-Subscribe]] oder [[Geteilter Datenraum|geteilte Datenräume]] bieten [[Entkopplung]] durch indirekte Kommunikation. Nicht geeignet für Systeme mit dynamischen [[Topologie|Topologien]] oder häufig wechselnden [[Komponente|Komponenten]].
- **Beispiel / Code:** Ein Beispiel für referenzielle Kopplung ist ein direkter [[Remote Procedure Call|RPC]] zwischen zwei [[Dienst|Diensten]]:

```java
// Client kennt die genaue Adresse des Servers
ServerService server = new ServerService("http://server:8080/api");
String result = server.callMethod("data");
```

Im Gegensatz dazu wäre ein [[Ereignis-Bus]] referenziell entkoppelt:

```java
// Client sendet Nachricht ohne Kenntnis des Empfängers
eventBus.publish("topic", "data");
```
