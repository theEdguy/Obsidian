---
id: c10c404f-7e85-4321-98bc-23b1b70277f7
title: "X Client"
date: 2026-06-01
tags:
  - verteilte_systeme
  - grafik
  - netzwerkprotokoll
  - client-server
  - x11
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[X Client]]

- **Kernkonzept:** Der [[X Client|X-Client]] ist eine Komponente im [[X Window System]], die als Anwendung fungiert und über das [[X Protokoll]] mit dem [[X Server]] kommuniziert, um grafische [[Benutzerschnittstelle|Benutzerschnittstellen]] auf einem entfernten oder lokalen [[Display]] darzustellen.
- **Nutzen & Zweck:** Der [[X Client|X-Client]] ermöglicht die Trennung von Anwendung und Darstellung in verteilten Systemen, wodurch Anwendungen auf einem [[Server]] ausgeführt und deren Ausgabe auf einem entfernten [[Terminal]] angezeigt werden kann. Dies löst das Problem der [[Verteilungstransparenz]] und ermöglicht [[Plattformunabhängigkeit]] sowie effiziente Nutzung von Ressourcen.
- **Abgrenzung & Grenzen:** Der [[X Client|X-Client]] sollte nicht genutzt werden, wenn lokale Grafikleistung oder geringe Latenz entscheidend sind, da die Kommunikation über das Netzwerk erfolgt. Alternativen wie [[Wayland]] oder lokale GUI-Bibliotheken (z. B. Qt, GTK) bieten bessere Performance für lokale Anwendungen. Zudem ist das [[X Window System]] weniger sicher als moderne Protokolle, da es keine integrierte Verschlüsselung bietet.
- **Beispiel / Code:** Ein einfaches Beispiel für einen X-Client in C:
```c
#include <X11/Xlib.h>
#include <stdio.h>

int main() {
    Display *display = XOpenDisplay(NULL);
    if (!display) {
        fprintf(stderr, "Cannot open display\n");
        return 1;
    }
    int screen = DefaultScreen(display);
    Window window = XCreateSimpleWindow(display, RootWindow(display, screen), 10, 10, 400, 300, 1,
                                         BlackPixel(display, screen), WhitePixel(display, screen));
    XSelectInput(display, window, ExposureMask | KeyPressMask);
    XMapWindow(display, window);
    
    XEvent event;
    while (1) {
        XNextEvent(display, &event);
        if (event.type == Expose) {
            XDrawString(display, window, DefaultGC(display, screen), 50, 50, "Hello, X Client!", 14);
        }
        if (event.type == KeyPress) break;
    }
    XCloseDisplay(display);
    return 0;
}
```
Dieser Code öffnet ein Fenster und zeigt Text an, indem er mit dem X-Server kommuniziert.
