---
id: 155b9699-0539-4d75-9ee6-e87491dd57ae
title: "SOAP (Simple Object Access Protocol)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - protokoll
  - webservices
  - kommunikation
  - xml
  - architektur
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[SOAP (Simple Object Access Protocol)]]

- **Kernkonzept:** SOAP ist ein [[Protokoll|Protokolle]] für den [[Nachrichtenaustausch|Nachrichtenaustausch]] in [[verteilte Systeme|verteilten Systemen]], das auf [[XML]] basiert und [[plattformunabhängig|plattformunabhängige]] [[Kommunikation]] über [[Netzwerk]]e ermöglicht.
- **Nutzen & Zweck:** SOAP existiert, um [[standardisierte|standardisierte]] und [[strukturierte|strukturierte]] [[Kommunikation]] zwischen [[Komponente|Komponenten]] in [[heterogene|heterogenen]] Systemen zu ermöglichen. Es löst das [[Problem]] der [[Interoperabilität]] zwischen verschiedenen [[Programmiersprache|Programmiersprachen]] und [[Systemarchitektur|Systemarchitekturen]], indem es [[Nachrichten]] in einem einheitlichen [[Format]] überträgt.
- **Abgrenzung & Grenzen:** SOAP sollte nicht genutzt werden, wenn [[Performance]] oder [[Einfachheit]] im Vordergrund stehen, da es durch sein [[XML]]-Format und zusätzliche [[Protokoll]]-Overheads langsamer und komplexer als Alternativen wie [[REST]] ist. Im Gegensatz zu [[REST]] ist SOAP [[zustandsbehaftet|zustandsbehaftet]], was es weniger geeignet für [[skalierbare|skalierbare]] [[Webservice|Webservices]] macht. Für [[einfache|einfache]] [[CRUD]]-Operationen oder [[ressourcenorientierte|ressourcenorientierte]] Systeme ist [[REST]] oft die bessere Wahl.
- **Beispiel / Code:** Ein SOAP-Beispiel für einen [[Dienstaufruf|Dienstaufruf]] zur Erstellung eines Buckets in Amazon S3:

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:aws="http://s3.amazonaws.com/doc/2006-03-01/">
   <soapenv:Header>
      <aws:Credentials>
         <aws:AccessKeyId>AKIAIOSFODNN7EXAMPLE</aws:AccessKeyId>
         <aws:SecretAccessKey>wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY</aws:SecretAccessKey>
      </aws:Credentials>
   </soapenv:Header>
   <soapenv:Body>
      <aws:CreateBucket>
         <aws:Bucket>mybucket</aws:Bucket>
      </aws:CreateBucket>
   </soapenv:Body>
</soapenv:Envelope>
```

Vergleich mit REST: `PUT http://mybucket.s3.amazonaws.com/` (einfacher HTTP-Aufruf).
