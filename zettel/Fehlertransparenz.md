---
id: f937618d-0f0b-4865-bd9d-153f473a6094
title: "Fehlertransparenz"
date: 2026-06-01
tags:
  - verteilte_systeme
  - transparenz
  - fehlertoleranz
  - client_server
  - middleware
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Fehlertransparenz]]

- **Kernkonzept:** Fehlertransparenz verbirgt [[Ausfall|Ausfälle]] von [[Komponente|Komponenten]] oder [[Kommunikationskanal|Kommunikationskanälen]] vor dem [[Nutzer|Nutzer]] oder der [[Anwendung|Anwendung]], sodass das [[System]] trotz [[Fehler|Fehlern]] funktionsfähig bleibt.
- **Nutzen & Zweck:** Das Konzept existiert, um die [[Zuverlässigkeit]] und [[Verfügbarkeit]] von verteilten [[System|Systemen]] zu erhöhen. Es löst das [[Problem]], dass [[Nutzer|Nutzer]] oder [[Anwendung|Anwendungen]] nicht mit [[Fehler|Fehlern]] wie [[Serverausfall|Serverausfällen]] oder [[Netzwerkstörung|Netzwerkstörungen]] konfrontiert werden sollen.
- **Abgrenzung & Grenzen:** Fehlertransparenz sollte nicht genutzt werden, wenn die [[Komplexität]] des [[Systems]] unnötig erhöht wird oder wenn [[Echtzeitanforderung|Echtzeitanforderungen]] eine sofortige [[Fehlererkennung]] erfordern. Alternativen wie [[Fehlertoleranz]] oder [[Redundanz]] können in solchen Fällen besser geeignet sein. Im Gegensatz zu [[Ortstransparenz]] oder [[Migrationstransparenz]] fokussiert sich Fehlertransparenz ausschließlich auf das Verbergen von [[Ausfall|Ausfällen]].
- **Beispiel / Code:** Ein Beispiel für Fehlertransparenz ist ein [[Client-Stub]] in einem [[RPC-System]], der bei einem [[Serverausfall]] automatisch eine [[Anfrage]] an einen [[Backup-Server]] weiterleitet, ohne dass der [[Nutzer]] dies bemerkt:

```
try {
    result = remoteCall(server1, request);
} catch (ServerFailureException e) {
    result = remoteCall(backupServer, request); // Transparente Weiterleitung
}
```
