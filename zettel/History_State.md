---
id: a34ba173-ec35-41ed-9412-057510f4de9e
title: "History_State"
date: 2026-05-30
tags:
  - software_engineering
  - zustandsmaschine
  - entwurfsmuster
  - uml
  - verhaltensmuster
  - hierarchische_zustaende
  - draft
source: "Klausur_Referenz"
---

# [[History_State]]

- **Kernkonzept:** Ein **History_State** ist ein spezieller Zustand in einer [[Zustandsmaschine]], der sich den zuletzt aktiven Unterzustand eines [[Kompositum_Zustand]]s merkt. Beim erneuten Betreten des Kompositum-Zustands wird nicht der initiale Unterzustand, sondern der zuvor gespeicherte History-Zustand aktiviert. Dies ermöglicht eine Wiederaufnahme der Zustandsmaschine an der Stelle, an der sie verlassen wurde, ohne den Kontext zu verlieren. History-States existieren in zwei Varianten: *Shallow History* (merkt sich nur die oberste Ebene der Unterzustände) und *Deep History* (merkt sich rekursiv alle verschachtelten Unterzustände).
- **Nutzen & Zweck:** History-States werden eingesetzt, um komplexe Abläufe in [[Zustandsmaschinen]] zu vereinfachen, insbesondere wenn:
- Unterbrechungen (z. B. durch externe Ereignisse) den aktuellen Zustand temporär verlassen, aber später fortgesetzt werden sollen.
- Nutzerinteraktionen (z. B. in [[Benutzeroberflächen]]) einen Kontextwechsel erfordern, der später rückgängig gemacht wird.
- Ressourcen effizient verwaltet werden müssen, indem der letzte Zustand wiederhergestellt wird (z. B. bei [[Session_Management]] in Webanwendungen).

Vorteile:
- Reduziert die Komplexität der Zustandsübergänge, da nicht alle möglichen Rückkehrpfade manuell modelliert werden müssen.
- Verbessert die [[Wartbarkeit]] von Zustandsmaschinen, indem der Zustandskontext implizit erhalten bleibt.
- Ermöglicht eine natürlichere Abbildung realer Abläufe (z. B. "Pause" in einem Workflow).
- **Abgrenzung & Grenzen:** 1. **Einsatzbereich**: History-States sind nur in hierarchischen [[Zustandsmaschinen]] sinnvoll, die [[Kompositum_Zustand]]e verwenden. In flachen Zustandsmaschinen sind sie wirkungslos.

2. **Varianten**: 
   - *Shallow History* (H): Merkt sich nur den direkten Unterzustand des Kompositums. Bei verschachtelten Zuständen wird der initiale Zustand tieferer Ebenen verwendet.
   - *Deep History* (H*): Merkt sich rekursiv alle Unterzustände. Dies kann zu unerwartetem Verhalten führen, wenn die Zustandsstruktur dynamisch verändert wird.

3. **Stolpersteine**:
   - **Initialisierung**: Beim ersten Betreten eines Kompositum-Zustands mit History-State muss ein initialer Unterzustand definiert sein, da noch kein History-Eintrag existiert.
   - **Zyklische Abhängigkeiten**: History-States können zu unendlichen Schleifen führen, wenn sie in Kombination mit [[Zustandsübergang]]en verwendet werden, die den History-State selbst als Ziel haben.
   - **Speicherbedarf**: Deep History kann bei tief verschachtelten Zuständen zu hohem Speicherverbrauch führen.
   - **Thread-Safety**: In parallelen Systemen muss der History-State atomar aktualisiert werden, um Race Conditions zu vermeiden.

4. **Alternativen**: 
   - Manuelle Speicherung des Zustands (z. B. über [[Memento_Pattern]]), wenn mehr Kontrolle über den Kontext benötigt wird.
   - [[Stack-basierte_Zustandsverwaltung]], falls mehrere historische Zustände verwaltet werden müssen.
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Statechart (Mermaid-Syntax) zeigt einen Login-Prozess mit History-State. Beim Verlassen des "Authentifiziert"-Zustands (z. B. durch Timeout) wird der letzte aktive Unterzustand ("Dashboard" oder "Einstellungen") gespeichert und bei Rückkehr wiederhergestellt:', 'uml_diagramm': 'stateDiagram-v2\n    [*] --> Login\n    Login --> Authentifiziert: Erfolgreich\n    state Authentifiziert {\n        [*] --> Dashboard\n        Dashboard --> Einstellungen: Navigiere\n        Einstellungen --> Dashboard: Zurück\n        --\n        state H <<history>>\n    }\n    Authentifiziert --> Timeout: Inaktivität\n    Timeout --> H: Fortsetzen\n    Authentifiziert --> Logout: Abmelden\n    Logout --> Login', 'java_implementation': {'hinweis': 'Eine vereinfachte Java-Implementierung mit Shallow History (ohne Observer-Pattern für bessere Lesbarkeit):', 'code': 'public class StateMachineWithHistory {\n    private enum SubState { DASHBOARD, EINSTELLUNGEN }\n    private enum MainState { LOGIN, AUTHENTIFIZIERT, TIMEOUT, LOGOUT }\n\n    private MainState currentMainState = MainState.LOGIN;\n    private SubState historyState = SubState.DASHBOARD; // Initialwert\n\n    public void login() {\n        if (currentMainState == MainState.LOGIN) {\n            currentMainState = MainState.AUTHENTIFIZIERT;\n            System.out.println("Betrete Authentifiziert (History: " + historyState + ")");\n        }\n    }\n\n    public void navigateTo(SubState target) {\n        if (currentMainState == MainState.AUTHENTIFIZIERT) {\n            historyState = target;\n            System.out.println("Wechsle zu: " + target);\n        }\n    }\n\n    public void timeout() {\n        if (currentMainState == MainState.AUTHENTIFIZIERT) {\n            currentMainState = MainState.TIMEOUT;\n            System.out.println("Timeout - verlasse Authentifiziert");\n        }\n    }\n\n    public void resume() {\n        if (currentMainState == MainState.TIMEOUT) {\n            currentMainState = MainState.AUTHENTIFIZIERT;\n            System.out.println("Fortsetzen bei: " + historyState);\n        }\n    }\n\n    public void logout() {\n        currentMainState = MainState.LOGOUT;\n        System.out.println("Abgemeldet");\n    }\n}', 'erlaeuterung': 'Die `historyState`-Variable speichert den letzten aktiven Unterzustand. Beim `resume()` wird dieser wiederhergestellt, statt den initialen Zustand zu verwenden.'}}
