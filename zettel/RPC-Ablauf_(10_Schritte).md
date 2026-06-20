---
id: 092d13be-69b9-5fcc-8e00-baf9b1f1e720
title: "RPC-Ablauf (10 Schritte)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Kommunikation"
---

# [[RPC-Ablauf (10 Schritte)]]

- **Kernkonzept:** Sequenz eines synchronen RPC-Aufrufs: 1. Client-Prozedur ruft Client-Stub auf. 2. Stub verpackt Parameter (Marshaling) und ruft Client-BS auf. 3. Client-BS sendet Nachricht an Server-BS. 4. Server-BS übergibt Nachricht an Server-Stub. 5. Server-Stub entpackt Parameter (Unmarshaling) und ruft Server-Prozedur auf. 6. Server-Prozedur arbeitet und gibt Ergebnis an Server-Stub zurück. 7. Server-Stub verpackt Ergebnis und ruft Server-BS auf. 8. Server-BS sendet Nachricht an Client-BS. 9. Client-BS übergibt Nachricht an Client-Stub. 10. Client-Stub entpackt Ergebnis und gibt es an Client-Prozedur zurück.
- **Nutzen & Zweck:** Sequenz eines synchronen RPC-Aufrufs: 1. Client-Prozedur ruft Client-Stub auf. 2. Stub verpackt Parameter (Marshaling) und ruft Client-BS auf. 3. Client-BS sendet Nachricht an Server-BS. 4. Server-BS übergibt Nachricht an Server-Stub. 5. Server-Stub entpackt Parameter (Unmarshaling) und ruft Server-Prozedur auf. 6. Server-Prozedur arbeitet und gibt Ergebnis an Server-Stub zurück. 7. Server-Stub verpackt Ergebnis und ruft Server-BS auf. 8. Server-BS sendet Nachricht an Client-BS. 9. Client-BS übergibt Nachricht an Client-Stub. 10. Client-Stub entpackt Ergebnis und gibt es an Client-Prozedur zurück.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
