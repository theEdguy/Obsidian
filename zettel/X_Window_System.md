---
id: 24033958-4147-43ad-86ec-b397ff8ebeb5
title: "X Window System"
date: 2026-06-01
tags:
  - verteilte_systeme
  - fenstersystem
  - netzwerkprotokoll
  - verteilte-systeme
  - client-server
  - grafik
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[X Window System]]

- **Kernkonzept:** Das [[X Window System]] ist ein netzwerktransparentes [[Fenstersystem]], das die grafische [[Benutzerschnittstelle|Benutzerschnittstellen]] in verteilten [[System]]en ermöglicht, indem es [[Client]]- und [[Server]]-Komponenten über ein [[Protokoll]] entkoppelt.
- **Nutzen & Zweck:** Es löst das [[Problem]] der zentralen Steuerung grafischer [[Ausgabe]]n und [[Eingabe]]n in vernetzten [[Umgebung|Umgebungen]], indem es [[Anwendung]]en erlaubt, auf entfernten [[Maschine|Maschinen]] zu laufen, während die [[Interaktion]] lokal auf einem [[Terminal]] erfolgt. Dies ermöglicht [[Verteilungstransparenz]] und [[Plattformunabhängigkeit]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Echtzeitanwendung|Echtzeitanwendungen]] oder [[System]]e mit hohen [[Latenz]]anforderungen, da das [[X Protokoll]] netzwerkbasiert ist. Alternativen wie [[Wayland]] oder [[Mir]] setzen auf modernere [[Architektur]]en mit direkterer [[Hardware]]-Anbindung und besserer [[Sicherheit]]. Im Gegensatz zu [[Remote Desktop]]-Lösungen (z. B. [[VNC]]) trennt das [[X Window System]] strikt [[Logik]] und [[Darstellung]].
- **Beispiel / Code:** Ein einfacher X-Client in C, der ein Fenster öffnet:
```c
#include <X11/Xlib.h>
#include <stdio.h>

int main() {
    Display *display = XOpenDisplay(NULL);
    if (!display) return 1;
    Window window = XCreateSimpleWindow(display, RootWindow(display, 0), 0, 0, 400, 300, 0, 0, 0);
    XMapWindow(display, window);
    XFlush(display);
    while (1) { /* Ereignisschleife */ }
    return 0;
}
```
Das Beispiel zeigt die Entkopplung: Der [[Code]] läuft auf dem [[Client]], die [[Ausgabe]] erfolgt auf dem [[X Server]].
