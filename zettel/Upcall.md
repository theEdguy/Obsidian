---
id: 9846ec31-864c-437a-8cfa-53a5c694789f
title: "Upcall"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - koordination
  - schichtenmodell
  - ereignisbehandlung
  - software-design
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Upcall]]

- **Kernkonzept:** Ein [[Upcall]] ist ein Mechanismus in [[geschichteten_Architektur|geschichteten Architekturen]], bei dem eine tiefere [[Schicht]] eine höhere [[Schicht]] aufruft, um Ereignisse oder Daten zu verarbeiten, die von der tieferen [[Schicht]] nicht selbst behandelt werden können.
- **Nutzen & Zweck:** Der [[Upcall]] ermöglicht die [[Entkopplung]] von [[Komponente|Komponenten]] in [[geschichteten_Architektur|geschichteten Systemen]], indem er eine [[Rückruf|Rückruf-]] oder [[Ereignisbehandlung|Ereignisbehandlungs-]]Logik bereitstellt. Er löst das [[Problem]] der [[Umkehrung]] des Kontrollflusses, um flexiblere und modularere [[Systeme]] zu schaffen, insbesondere in [[Netzwerkprotokoll|Netzwerkprotokollen]] oder [[Ereignisgesteuerte_Architektur|ereignisgesteuerten Architekturen]].
- **Abgrenzung & Grenzen:** [[Upcall|Upcalls]] sollten nicht genutzt werden, wenn eine strikte [[Top-Down]]-Kontrolle erforderlich ist, da sie den Kontrollfluss unvorhersehbar machen können. Alternativen wie [[Downcall|Downcalls]] oder [[Polling]] sind einfacher zu debuggen, aber weniger flexibel. [[Upcall|Upcalls]] erhöhen die [[Komplexität]] und können zu [[Zirkuläre_Abhängigkeit|zirkulären Abhängigkeiten]] führen, wenn sie unsachgemäß eingesetzt werden.
- **Beispiel / Code:** Ein Beispiel für einen [[Upcall]] in einem [[Netzwerkprotokoll]]:\n\n1. Eine [[Transportschicht]] (z. B. TCP) empfängt ein Paket und erkennt, dass es für eine [[Anwendungsschicht]] bestimmt ist.\n2. Statt das Paket selbst zu verarbeiten, ruft die [[Transportschicht]] eine [[Callback-Funktion]] in der [[Anwendungsschicht]] auf (z. B. `onPacketReceived(data)`).\n3. Die [[Anwendungsschicht]] verarbeitet das Paket und gibt ggf. eine Antwort zurück.\n\nIn Python könnte dies vereinfacht so aussehen:\n```python\ndef handle_packet(data):\n    print(f"Anwendung verarbeitet Paket: {data}")\n\n# Transportschicht simuliert Upcall\ndef transport_layer(packet, callback):\n    callback(packet)\n\ntransport_layer("Datenpaket", handle_packet)\n```
