---
id: 60768f72-28cb-4b67-b961-387f8d278e93
title: "Interzeptoren (Request-Level, Message-Level)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - middleware
  - verteilte-systeme
  - architektur
  - interzeption
  - erweiterbarkeit
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Interzeptoren (Request-Level, Message-Level)]]

- **Kernkonzept:** Interzeptoren [[Interzeptor|unterbrechen]] den Kontrollfluss in [[Middleware|Middleware-Systemen]], um das Verhalten von [[Aufruf|Aufrufen]] oder [[Nachricht|Nachrichten]] anzupassen. Man unterscheidet Request-Level- (auf [[Operation|Operationsebene]]) und Message-Level-Interzeptoren (auf [[Protokoll|Protokollebene]]).
- **Nutzen & Zweck:** Interzeptoren ermöglichen die flexible Anpassung von [[Middleware|Middleware]] für spezifische [[Anwendung|Anwendungen]], ohne deren Kernfunktionalität zu ändern. Sie lösen das [[Problem]] der starren, massentauglichen [[Standardisierung|Standardisierung]] in verteilten Systemen, indem sie [[Erweiterung|Erweiterungen]] oder [[Transformation|Transformationen]] (z. B. Logging, Authentifizierung) modular einbinden.
- **Abgrenzung & Grenzen:** Interzeptoren sollten nicht genutzt werden, wenn die [[Komplexität]] des Systems unnötig erhöht wird oder [[Performance|Performance-kritische]] Pfade beeinträchtigt werden. Alternativen wie [[Wrapper]] oder [[Adapter]] eignen sich besser für statische [[Interface|Interface-Anpassungen]], während Interzeptoren dynamische [[Kontrollfluss|Kontrollfluss-Änderungen]] ermöglichen. Bei einfachen [[Client-Server|Client-Server]]-Modellen sind sie oft überdimensioniert.
- **Beispiel / Code:** // Request-Level-Interzeptor (Java RMI-ähnlich)
public class LoggingInterceptor implements InvocationHandler {
    private Object target;
    
    public LoggingInterceptor(Object target) {
        this.target = target;
    }
    
    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        System.out.println("Vor Aufruf: " + method.getName());
        Object result = method.invoke(target, args);
        System.out.println("Nach Aufruf: " + method.getName());
        return result;
    }
}

// Message-Level-Interzeptor (z. B. in CORBA)
public class EncryptionInterceptor extends org.omg.PortableInterceptor.Interceptor {
    public void send_request(ClientRequestInfo ri) {
        byte[] payload = ri.get_request_body();
        byte[] encrypted = encrypt(payload);
        ri.set_request_body(encrypted);
    }
}
