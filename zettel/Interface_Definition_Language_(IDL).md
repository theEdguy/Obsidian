---
id: 59309b6c-7948-42dd-a52e-f4b0e10065c7
title: "Interface Definition Language (IDL)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - rpc
  - schnittstellen
  - codegenerierung
  - heterogenität
  - kommunikation
  - middleware
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Interface Definition Language (IDL)]]

- **Kernkonzept:** Eine [[Interface Definition Language|IDL]] ist eine [[Spezifikationssprache|Spezifikationssprache]], die zur Definition von [[Schnittstelle|Schnittstellen]] in [[Verteilte Systeme|verteilten Systemen]] dient, um [[Kommunikation|Kommunikationsprotokolle]] und [[Datenstruktur|Datenstrukturen]] plattformunabhängig zu beschreiben.
- **Nutzen & Zweck:** Die [[Interface Definition Language|IDL]] löst das [[Problem]] der [[Heterogenität]] in [[Verteilte Systeme|verteilten Systemen]], indem sie eine einheitliche Beschreibung von [[Schnittstelle|Schnittstellen]] ermöglicht. Dadurch wird die [[Interoperabilität]] zwischen verschiedenen [[Programmiersprache|Programmiersprachen]] und [[Systemarchitektur|Systemarchitekturen]] gewährleistet, insbesondere bei [[Remote Procedure Call|RPC]]-basierten [[Kommunikation|Kommunikationsmechanismen]].
- **Abgrenzung & Grenzen:** Eine [[Interface Definition Language|IDL]] sollte nicht genutzt werden, wenn die [[Kommunikation]] zwischen [[Komponente|Komponenten]] lokal und homogen ist, da der [[Overhead]] der [[Codegenerierung]] und [[Stubs]] unnötig ist. Alternativen wie direkte [[Socket]]-Programmierung oder [[Nachrichtenorientierte Middleware|nachrichtenorientierte Middleware]] (z. B. [[ZeroMQ]]) sind in solchen Fällen effizienter. Zudem eignet sich [[IDL]] nicht für [[Echtzeitkommunikation|Echtzeitkommunikationsszenarien]], die niedrige [[Latenz]] erfordern.
- **Beispiel / Code:** // Beispiel einer IDL-Definition in DCE/RPC
interface BeispielService {
    // Definiert eine entfernte Prozedur mit Copy-in/Copy-out-Semantik
    void incr([in, out] long *wert1, [in, out] long *wert2);
}

// Der IDL-Compiler generiert daraus Client- und Server-Stubs,
die die Kommunikation zwischen Client und Server abstrahieren.
