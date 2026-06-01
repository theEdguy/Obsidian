---
id: aadca582-559f-4b5c-a7f6-b4dce3f470aa
title: "Geteilter Datenraum (Shared Data Space)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - koordination
  - datenhaltung
  - asynchron
  - entkopplung
  - tuple-space
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Geteilter Datenraum (Shared Data Space)]]

- **Kernkonzept:** Ein [[geteilter Datenraum|geteilter Datenraum]] ist ein [[Architekturstil|Architekturstil]] in [[verteilten Systemen|verteilten Systemen]], der einen [[persistenten|persistenten]] [[Speicherbereich|Speicherbereich]] bereitstellt, in dem [[Komponente|Komponenten]] [[Daten]] ablegen und abrufen können, ohne direkte [[Kommunikation]] oder [[zeitliche Synchronisation]] mit anderen [[Komponente|Komponenten]].
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[temporalen]] und [[referenziellen Entkopplung]] in [[verteilten Systemen]]: [[Komponente|Komponenten]] müssen sich nicht gegenseitig kennen oder gleichzeitig aktiv sein, um [[Daten]] auszutauschen. Es ermöglicht [[flexible Koordination]] und [[skalierbare]] [[Interaktion]] in [[asynchronen]] Umgebungen.
- **Abgrenzung & Grenzen:** Ein [[geteilter Datenraum|geteilter Datenraum]] ist ungeeignet für [[Echtzeitanwendungen]], die [[strikte Konsistenz]] oder [[niedrige Latenz]] erfordern. Im Vergleich zu [[Publish-Subscribe-Systemen]] oder [[direkter Kommunikation]] (z. B. [[RPC]]) bietet er weniger [[Kontrolle]] über [[Datenfluss]] und [[Benachrichtigungen]]. Alternativen wie [[Message Queues]] oder [[Datenbanken]] können je nach [[Anforderung]] besser geeignet sein.
- **Beispiel / Code:** Ein einfaches Beispiel für einen [[geteilten Datenraum|geteilten Datenraum]] ist das [[Tuple Space]]-Modell (z. B. in JavaSpaces oder Linda):

```java
// Komponente A schreibt ein Datum in den geteilten Raum
TupleSpace space = new TupleSpace();
space.write(new Tuple("Temperatur", 23.5));

// Komponente B liest das Datum asynchron
Tuple template = new Tuple("Temperatur", Double.class);
Tuple result = space.read(template);
```

Hier agiert der [[Tuple Space]] als [[persistenter]] [[Datenraum]], der [[Lese-]] und [[Schreiboperationen]] entkoppelt.
