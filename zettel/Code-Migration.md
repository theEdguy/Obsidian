---
id: 8c604ca7-eb55-4eed-9ef7-5672fda226a2
title: "Code-Migration"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - virtualisierung
  - prozesse
  - portabilität
  - architektur
  - prozessverwaltung
  - cloud_computing
  - lastverteilung
  - mobile_computing
  - netzwerkoptimierung
  - mobilitaet
  - heterogenitaet
  - code_management
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Code-Migration]]

- **Kernkonzept:** Unter [[Code-Migration|Code-Migration]] versteht man das dynamische Verschieben von ausführbarem [[Code]] oder [[Prozess|Prozessen]] – einschließlich deren [[Zustand|Zuständen]] – zwischen verschiedenen [[Knoten|Knoten]] in [[Verteiltes_System|verteilten Systemen]], um [[Berechnung|Berechnungen]] effizienter zu verteilen, [[Ressource|Ressourcen]] optimal zu nutzen oder [[Heterogenität]] zu überwinden. Dies umfasst sowohl die Anpassung an [[Schnittstelle|Schnittstellen]] oder [[Hardware]]-Änderungen als auch die bedarfsgerechte Verlagerung zu [[Client|Clients]] oder [[Datenquelle|Datenquellen]] mittels abstrakter [[Maschine|Maschinen]] wie [[Virtuelle_Maschine|VMs]] oder [[Java_Virtual_Machine|JVMs]].
- **Nutzen & Zweck:** [[Code-Migration]] löst zentrale [[Problem|Probleme]] in [[Verteilte_System|verteilten Systemen]], indem sie [[Kompatibilität]] zwischen heterogenen [[Plattform|Plattformen]] oder [[Architektur|Architekturen]] ermöglicht und [[Performance]], [[Skalierbarkeit]] sowie [[Fehlertoleranz]] durch dynamische [[Lastverteilung]] oder [[Virtualisierung]] optimiert. Sie reduziert [[Netzwerk|Netzwerklatenz]] und [[Energieverbrauch]] in [[Rechenzentrum|Rechenzentren]], indem [[Code]] oder [[Prozess|Prozesse]] gezielt zu [[Client|Clients]], [[Datenquelle|Datenquellen]] oder weniger ausgelasteten [[Knoten|Knoten]] verschoben werden – etwa in [[Mobile_Computing|mobilen Szenarien]], [[Cloud_Computing|Cloud-Umgebungen]] oder [[Edge_Computing|Edge-Computing-Kontexten]]. Zudem ermöglicht sie flexible [[Anpassung|Anpassungen]] an sich ändernde [[Systemanforderung|Systemanforderungen]] ohne manuelle Intervention, z. B. durch [[Code-on-Demand]] oder [[Mobile_Agents|mobile Agenten]].
- **Abgrenzung & Grenzen:** [[Code-Migration]] ist ungeeignet, wenn die [[Komplexität]] der Anpassung den Nutzen übersteigt – etwa bei stark [[Hardware]]-abhängigem [[Code]] oder wenn der [[Overhead]] der Migration (z. B. durch [[Serialisierung]] des [[Zustand|Zustands]]) die [[Vorteile]] überwiegt. Sie unterscheidet sich von [[Remote_Procedure_Call|RPCs]] oder [[Nachrichtenübertragung|Nachrichtenübertragungen]], da hier nicht nur [[Aufruf|Aufrufe]] oder [[Daten]] übertragen werden, sondern der [[Code]] selbst (und ggf. dessen [[Ausführungszustand]]) physisch verschoben wird. Bei [[Echtzeitsystem|Echtzeitanforderungen]] kann die [[Latenz]] der Migration kritisch sein, während in [[Sicherheit]]-kritischen Anwendungen Risiken wie [[Daten]]-Lecks, [[Angriff|Angriffsflächen]] oder [[Malware|Schadcode]]-Einschleusung bestehen. Alternativen wie [[Containerisierung]], [[Virtualisierung]] oder [[Isolation|strikte Isolation]] sind vorzuziehen, wenn keine vollständige [[Prozess]]-Verschiebung erforderlich ist oder [[Zustandsabhängigkeit|zustandsbehaftete]] [[Prozess|Prozesse]] problematisch sind.
- **Beispiel / Code:** Ein Beispiel für [[Code-on-Demand]] (CoD) in [[Java]], bei dem ein [[Client]] dynamisch [[Code]] von einem [[Server]] lädt und lokal ausführt:

```java
// Client-seitige Code-Migration via URLClassLoader
URLClassLoader loader = new URLClassLoader(new URL[] { new URL("http://server.com/code.jar") });
Class<?> dynamicClass = loader.loadClass("DynamicTask");
Runnable task = (Runnable) dynamicClass.newInstance();
task.run(); // Lokale Ausführung des migrierten Codes
```

Ein weiteres Szenario zeigt [[Remote_Evaluation_(REV)|Remote Evaluation (REV)]], bei dem [[Code]] zur [[Datenquelle]] verschoben wird:

```pseudocode
// Client fordert Code an und führt ihn mit lokalen Daten aus
code = load_code_from_repository("service_x")
exec(code, local_data)

// Server verarbeitet Ergebnis nach der Migration
result = handle_request(client_data)
```

Für [[Mobile_Agents|mobile Agenten]] wird zusätzlich der [[Ausführungszustand]] übertragen, z. B. durch [[Serialisierung]] des [[Thread-Kontext|Thread-Kontexts]]:

```java
// Serialisierung eines mobilen Agenten
ByteArrayOutputStream bos = new ByteArrayOutputStream();
ObjectOutputStream oos = new ObjectOutputStream(bos);
oos.writeObject(agent); // Agent inkl. Zustand
byte[] serializedAgent = bos.toByteArray();

// Deserialisierung auf dem Zielknoten
ByteArrayInputStream bis = new ByteArrayInputStream(serializedAgent);
ObjectInputStream ois = new ObjectInputStream(bis);
MobileAgent migratedAgent = (MobileAgent) ois.readObject();
migratedAgent.resume(); // Fortsetzung der Ausführung
```

Ein praktisches Beispiel für [[Hardware]]-unabhängige Migration ist die Ausführung von [[Java]]-Bytecode auf verschiedenen [[Plattform|Plattformen]]:

```java
public class MigratingCode {
    public static void main(String[] args) {
        System.out.println("Dieser Code läuft auf jeder [[Java_Virtual_Machine|JVM]], unabhängig von der [[Hardware]].");
    }
}
```

Oder die [[Virtualisierung]] einer [[x86]]-Anwendung auf [[ARM]]-Hardware mittels [[QEMU]].
