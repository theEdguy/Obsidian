---
id: d83dbdd8-3530-472d-a102-0e87fb69eb48
title: "Single_Sign_On"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - authentifizierung
  - sicherheit
  - oauth2
  - openid_connect
  - saml
  - identity_management
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Single_Sign_On]]

- **Kernkonzept:** Single_Sign_On (SSO) ist ein [[Authentifizierungsmechanismus]], der es Benutzern ermöglicht, sich einmalig mit ihren Anmeldedaten (z. B. Benutzername und Passwort) zu authentifizieren und anschließend auf mehrere, unabhängige [[Softwaresysteme]] oder [[Dienste]] zuzugreifen, ohne sich erneut anmelden zu müssen. SSO basiert auf einer zentralen [[Authentifizierungsinstanz]] (z. B. ein [[Identity_Provider]]), die die Identität des Benutzers validiert und [[Authentifizierungstoken]] (z. B. [[JSON_Web_Token]] oder SAML-Assertions) an die beteiligten Systeme übermittelt. Diese Token dienen als Nachweis der erfolgreichen Authentifizierung und ermöglichen den Zugriff auf die jeweiligen Ressourcen.
- **Nutzen & Zweck:** SSO wird eingesetzt, um die Benutzerfreundlichkeit in komplexen [[IT_Infrastrukturen]] zu erhöhen, indem die Anzahl der erforderlichen Anmeldungen reduziert wird. Weitere Vorteile sind:

- **Vereinfachte Verwaltung**: Benutzerkonten und Berechtigungen können zentral über den [[Identity_Provider]] verwaltet werden, was den administrativen Aufwand verringert.
- **Sicherheit**: Durch die zentrale Authentifizierung können Sicherheitsrichtlinien (z. B. [[Multi_Faktor_Authentifizierung]]) konsistent durchgesetzt werden. Zudem reduziert SSO das Risiko von Passwort-Fatigue, da Benutzer sich weniger Passwörter merken müssen.
- **Skalierbarkeit**: Neue [[Dienste]] oder Systeme können nahtlos in die bestehende SSO-Infrastruktur integriert werden, ohne dass Benutzer zusätzliche Anmeldedaten benötigen.
- **Compliance**: SSO erleichtert die Einhaltung von Datenschutz- und Sicherheitsvorschriften (z. B. [[GDPR]]), da Authentifizierungsprozesse zentral protokolliert und überwacht werden können.

Typische Anwendungsfälle sind Unternehmensportale, Cloud-Dienste (z. B. [[Microsoft_365]] oder [[Google_Workspace]]) oder föderierte Identitätsmanagement-Systeme (z. B. in der öffentlichen Verwaltung).
- **Abgrenzung & Grenzen:** SSO ist nicht mit folgenden Konzepten zu verwechseln:

- **[[Passwort_Manager]]**: Diese speichern und verwalten Anmeldedaten lokal oder in der Cloud, erfordern aber weiterhin manuelle Eingaben oder automatisierte Formularausfüllungen. SSO hingegen eliminiert die Notwendigkeit wiederholter Anmeldungen durch Token-basierte Authentifizierung.
- **[[Session_Management]]**: Während SSO die initiale Authentifizierung übernimmt, regelt das Session-Management die Aufrechterhaltung des Benutzerstatus innerhalb eines einzelnen Systems. SSO kann jedoch mit Session-Management kombiniert werden, um nahtlose Übergänge zwischen Systemen zu ermöglichen.
- **[[Föderiertes_Identitätsmanagement]]**: SSO ist ein Teilbereich des föderierten Identitätsmanagements, das zusätzlich die sichere Weitergabe von Identitätsinformationen zwischen vertrauenswürdigen Domänen (z. B. Unternehmen oder Organisationen) ermöglicht.

**Stolpersteine und Grenzen**:
- **Single Point of Failure**: Die zentrale [[Authentifizierungsinstanz]] wird zum kritischen Angriffsziel. Ein Ausfall oder eine Kompromittierung kann den Zugriff auf alle angebundenen Systeme blockieren oder gefährden.
- **Komplexität**: Die Implementierung von SSO erfordert eine sorgfältige Planung, insbesondere bei der Integration heterogener Systeme oder Legacy-Anwendungen. Protokolle wie [[OAuth_2.0]], [[OpenID_Connect]] oder [[SAML]] müssen korrekt konfiguriert werden.
- **Sicherheitsrisiken**: Unsachgemäß implementierte SSO-Lösungen können Sicherheitslücken aufweisen, z. B. durch schwache Token-Verschlüsselung oder fehlende Validierung von Redirect-URIs.
- **Datenschutz**: Die zentrale Speicherung von Benutzerdaten wirft Datenschutzfragen auf, insbesondere wenn der [[Identity_Provider]] in einer anderen Jurisdiktion betrieben wird.
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Sequenzdiagramm (textuell beschrieben) veranschaulicht den typischen Ablauf einer SSO-Authentifizierung mit [[OAuth_2.0]] und [[OpenID_Connect]]:\n\n```mermaid\nsequenceDiagram\n    participant Benutzer as Benutzer\n    participant Client as Client-Anwendung\n    participant IDP as Identity Provider (IDP)\n    participant Ressource as Ressourcen-Server\n\n    Benutzer->>Client: Zugriffsanfrage (z. B. Webseite)\n    Client->>IDP: Authentifizierungsanfrage (Redirect zu IDP)\n    IDP->>Benutzer: Anmeldemaske (Login)\n    Benutzer->>IDP: Eingabe von Anmeldedaten\n    IDP->>Benutzer: Weiterleitung mit Autorisierungscode\n    Benutzer->>Client: Autorisierungscode übermittelt\n    Client->>IDP: Token-Anfrage (Autorisierungscode + Client-Credentials)\n    IDP->>Client: ID-Token + Access-Token\n    Client->>Ressource: Anfrage mit Access-Token\n    Ressource->>Client: Geschützte Ressource (z. B. Daten)\n```\n\n**Erläuterung der Schritte**:\n1. Der Benutzer fordert Zugriff auf eine Client-Anwendung an.\n2. Die Client-Anwendung leitet den Benutzer zur Authentifizierung an den [[Identity_Provider]] weiter.\n3. Der Benutzer meldet sich beim IDP an (ggf. mit [[Multi_Faktor_Authentifizierung]]).\n4. Der IDP sendet einen Autorisierungscode an die Client-Anwendung zurück.\n5. Die Client-Anwendung tauscht den Autorisierungscode gegen ein [[JSON_Web_Token]] (JWT) und ein Access-Token beim IDP ein.\n6. Die Client-Anwendung verwendet das Access-Token, um auf geschützte Ressourcen des Ressourcen-Servers zuzugreifen.', 'java_code_snippet': {'beschreibung': 'Das folgende Java-Codebeispiel zeigt eine vereinfachte Implementierung eines OAuth 2.0-Clients mit der Bibliothek *Spring Security OAuth2*. Der Client validiert ein vom [[Identity_Provider]] erhaltenes [[JSON_Web_Token]] (JWT) und extrahiert Benutzerinformationen:\n\n```java\nimport org.springframework.security.oauth2.client.OAuth2AuthorizedClient;\nimport org.springframework.security.oauth2.client.annotation.RegisteredOAuth2AuthorizedClient;\nimport org.springframework.security.oauth2.core.OAuth2AccessToken;\nimport org.springframework.security.oauth2.core.oidc.user.OidcUser;\nimport org.springframework.web.bind.annotation.GetMapping;\nimport org.springframework.web.bind.annotation.RestController;\n\n@RestController\npublic class SsoController {\n\n    @GetMapping("/userinfo")\n    public String getUserInfo(@RegisteredOAuth2AuthorizedClient OAuth2AuthorizedClient authorizedClient,\n                             @AuthenticationPrincipal OidcUser oidcUser) {\n        OAuth2AccessToken accessToken = authorizedClient.getAccessToken();\n        String tokenValue = accessToken.getTokenValue();\n        \n        // Extrahiere Benutzerinformationen aus dem ID-Token (JWT)\n        String userName = oidcUser.getName();\n        String email = oidcUser.getEmail();\n        \n        return String.format("Benutzer: %s, E-Mail: %s, Access-Token: %s", \n                            userName, email, tokenValue);\n    }\n}\n```\n\n**Hinweise**:\n- Die Annotation `@RegisteredOAuth2AuthorizedClient` injiziert das autorisierte Client-Objekt, das das Access-Token enthält.\n- `@AuthenticationPrincipal OidcUser` stellt die Benutzerinformationen bereit, die aus dem ID-Token des [[Identity_Providers]] extrahiert wurden.\n- In einer Produktionsumgebung sollte das Access-Token sicher gespeichert und vor Missbrauch geschützt werden (z. B. durch kurze Gültigkeitsdauern und [[Token_Revocation]]).'}}
