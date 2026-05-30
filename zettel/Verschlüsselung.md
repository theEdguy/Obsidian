---
id: b5f08dbc-0233-4bcd-a09b-f7b01b24e22f
title: "Verschlüsselung"
date: 2026-05-30
tags:
  - software_engineering
  - security
  - kryptografie
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Verschlüsselung]]

- **Kernkonzept:** [[Verschlüsselung]] ist ein [[Sicherheitsverfahren]], bei dem [[Daten]] mit einem [[kryptografischer_Algorithmus|kryptografischen Algorithmus]] (z. B. [[AES-256]]) in eine unlesbare Form umgewandelt werden, um sie vor [[unbefugter_Zugriff|unbefugtem Zugriff]] zu schützen.
- **Nutzen & Zweck:** Sie stellt die [[Vertraulichkeit]] und [[Integrität]] von [[Daten]] sicher, insbesondere bei der [[Übertragung]] (z. B. [[HTTPS]]) oder [[Speicherung]] (z. B. [[Datenbank]]). Ohne sie können [[Daten]] leicht [[abgefangen]] oder [[manipuliert]] werden.
- **Abgrenzung & Grenzen:** Im Gegensatz zur [[Zugriffskontrolle]] (die regelt, *wer* auf [[Daten]] zugreifen darf) schützt sie [[Daten]] unabhängig vom [[Zugriffsrecht]]. Sie sollte nicht mit [[Hashing]] verwechselt werden, das [[Daten]] irreversibel transformiert (z. B. für [[Passwort]]-Speicherung).
- **Beispiel / Code:** ```java
// Beispiel für AES-256-Verschlüsselung in Java
Cipher cipher = Cipher.getInstance("AES/CBC/PKCS5Padding");
cipher.init(Cipher.ENCRYPT_MODE, secretKey, ivParameterSpec);
byte[] encryptedData = cipher.doFinal(data.getBytes());
```
