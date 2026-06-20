---
id: 2924b997-817e-5bd3-aaf5-a27a6de59a5d
title: "LDAP (Lightweight Directory Access Protocol)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_5
  - draft
source: "Kapitel 5: Benennung"
---

# [[LDAP (Lightweight Directory Access Protocol)]]

- **Kernkonzept:** Hierarchischer Verzeichnisdienst für attributbasierte Benennung. Einträge bestehen aus Attribut-Wert-Paaren (z. B. C=NL, O=VU, OU=CS, CN=Main server). Sie werden im Directory Information Tree (DIT) angeordnet. Einträge werden durch ihren Distinguished Name (DN) eindeutig identifiziert, der sich aus Relative Distinguished Names (RDN) zusammensetzt.
- **Nutzen & Zweck:** Hierarchischer Verzeichnisdienst für attributbasierte Benennung. Einträge bestehen aus Attribut-Wert-Paaren (z. B. C=NL, O=VU, OU=CS, CN=Main server). Sie werden im Directory Information Tree (DIT) angeordnet. Einträge werden durch ihren Distinguished Name (DN) eindeutig identifiziert, der sich aus Relative Distinguished Names (RDN) zusammensetzt.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# LDAP Search Filter Beispiel:
# search('(&(C=NL)(O=VU University)(CN=Main server))')
```
