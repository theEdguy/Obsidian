---
id: de674d7f-b08e-4780-8fe9-947b829d8043
title: "Relative Distinguished Name (RDN)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensauflösung
  - ldap
  - verzeichnisdienst
  - hierarchische-benennung
  - skalierbarkeit
  - attributbasierte-suche
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Relative Distinguished Name (RDN)]]

- **Kernkonzept:** Ein **Relative Distinguished Name (RDN)** ist ein eindeutiger [[Name|Namen]] innerhalb eines [[Verzeichnisdienst|Verzeichnisdienstes]], der einen [[Knoten|Knoten]] in einer hierarchischen Struktur durch ein [[Attribut-Wert-Paar|Attribut-Wert-Paar]] identifiziert. RDNs bilden die Basis für den [[Pfad|Pfad]] eines [[Distinguished Name (DN)|Distinguished Names (DN)]] in [[LDAP]] oder ähnlichen Systemen.
- **Nutzen & Zweck:** RDNs lösen das Problem der eindeutigen [[Adressierung|Adressierung]] von [[Eintrag|Einträgen]] in hierarchischen [[Namensraum|Namensräumen]], indem sie eine skalierbare und strukturierte [[Benennung|Benennung]] ermöglichen. Sie vereinfachen die [[Suche|Suche]] und [[Verwaltung|Verwaltung]] von [[Objekt|Objekten]] in [[Verzeichnisdienst|Verzeichnisdiensten]] wie [[LDAP]] oder [[X.500]], indem sie lokale Eindeutigkeit innerhalb eines [[Kontext|Kontexts]] garantieren.
- **Abgrenzung & Grenzen:** RDNs sind nicht geeignet für flache oder attributbasierte [[Namensraum|Namensräume]], in denen keine Hierarchie existiert (z. B. reine [[Schlüssel-Wert-Speicher|Schlüssel-Wert-Speicher]]). Im Gegensatz zu [[DNS]]-Namen, die auf Pfadsegmenten basieren, sind RDNs immer an [[Attribut|Attribute]] gebunden. Für dynamische oder häufig wechselnde [[Struktur|Strukturen]] können RDNs zu [[Verwaltung|Verwaltung]]saufwand führen, da die Hierarchie explizit gepflegt werden muss.
- **Beispiel / Code:** {'ldap_eintrag': {'dn': 'CN=Main server,OU=Computer Science,O=VU University,C=NL', 'rdn': 'CN=Main server', 'attribute': [{'HostName': 'star'}, {'HostAddress': '192.31.231.42'}]}, 'erläuterung': 'Der **RDN** `CN=Main server` identifiziert den Eintrag eindeutig innerhalb der [[Organizational Unit (OU)|Organizational Unit]] `Computer Science`. Der vollständige [[Distinguished Name (DN)|DN]] setzt sich aus mehreren RDNs zusammen und bildet den Pfad im [[Directory Information Tree (DIT)|Directory Information Tree]].'}
