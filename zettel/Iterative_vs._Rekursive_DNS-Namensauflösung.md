---
id: dbfe154a-c978-5c6d-b846-7d08c51aa6f8
title: "Iterative vs. Rekursive DNS-Namensauflösung"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_5
  - draft
source: "Kapitel 5: Benennung"
---

# [[Iterative vs. Rekursive DNS-Namensauflösung]]

- **Kernkonzept:** Iterativ: Der Client-Resolver sendet eine Anfrage an den Nameserver. Dieser antwortet mit der Adresse des nächsten zuständigen Nameservers (Referral/Delegation). Der Client stellt die Anfrage dann selbst an den nächsten Server. Rekursiv: Der angefragte Nameserver übernimmt die komplette Auflösung, fragt nachgelagerte Server selbstständig ab, wartet auf die Antwort und liefert dem Client das finale Ergebnis. Rekursives Routing profitiert stark von Caching.
- **Nutzen & Zweck:** Iterativ: Der Client-Resolver sendet eine Anfrage an den Nameserver. Dieser antwortet mit der Adresse des nächsten zuständigen Nameservers (Referral/Delegation). Der Client stellt die Anfrage dann selbst an den nächsten Server. Rekursiv: Der angefragte Nameserver übernimmt die komplette Auflösung, fragt nachgelagerte Server selbstständig ab, wartet auf die Antwort und liefert dem Client das finale Ergebnis. Rekursives Routing profitiert stark von Caching.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
