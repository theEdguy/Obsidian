# KI-Regelwerk für Computergrafik-Verarbeitung

> Systemregeln und Kontextvorgaben für KI-Assistenten basierend auf Prof. Dr. Christian Pape: Computergrafik.

**Version**: 1.0.0


---

## ⚙️ Allgemeine Regeln

- **never_do_more_than_requested:** Tue niemals mehr als verlangt. Halte die Antworten präzise, direkt und beschränke dich strikt auf die angeforderte Aufgabe.


---

# Kapitel 1: Mathematische und geometrische Grundlagen

## 📖 Guidelines

### Das Problem
In der Computergrafik müssen visuelle Szenen mathematisch modelliert und manipuliert werden. Ohne solide geometrische Konzepte (wie Vektoren, Matrizen, Trigonometrie, Polygondarstellungen) können Transformationen, Schnittpunktberechnungen und Ausrichtungen im Raum nicht robust, effizient oder fehlerfrei durchgeführt werden.

### Die Lösung
Formulierung des 2D/3D-Raums über euklidische Koordinatensysteme (Rechts- vs. Linkshändisch), Definition von Polygonen (planar, einfach) und Triangulierungsalgorithmen (Ear-Clipping), Nutzung der linearen Algebra (Vektorräume, Skalar- und Kreuzprodukte) zur Beschreibung von Richtungen, Normalen und Reflexionen, sowie die Lösung linearer Gleichungssysteme (Cramersche Regel) zur Schnittpunktbestimmung (z.B. Strahl-Dreieck-Schnitt).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer den Unterschied zwischen links- und rechtshändigen Koordinatensystemen erklären kann.
- Leite den Benutzer an, einfache Polygone mittels Ear-Clipping (Zwei-Ohren-Theorem) zu triangulieren und die Anzahl der Dreiecke (k-2) zu bestimmen.
- Erzwinge die korrekte mathematische Anwendung des Skalarprodukts (Dot Product) für Winkel- und Orthogonalitätsprüfungen sowie des Kreuzprodukts (Cross Product) zur Normalenbestimmung und Flächenberechnung.
- Stelle sicher, dass der Benutzer den Möller-Trumbore-Algorithmus bzw. die Cramersche Regel zur schnellen Berechnung von Strahl-Dreieck-Schnittpunkten und den baryzentrischen Koordinaten (u, v, w) anwenden kann.


## 💡 Konzepte & Definitionen

### Rechtshändiges Koordinatensystem

**Definition**:
Orthogonale Basis, bei der der Daumen der rechten Hand in x-Richtung, der Zeigefinger in y-Richtung und der Mittelfinger in z-Richtung zeigt. In der Computergrafik-Vorlesung standardmäßig verwendet. Wenn man auf die x-y-Ebene blickt, zeigt die positive z-Achse aus dem Bildschirm heraus auf den Betrachter.

### Einfaches Polygon

**Definition**:
Ein Polygon ist eine Fläche, die durch eine Folge von k > 2 Punkten definiert ist, die einen geschlossenen Streckenzug bilden. Ein einfaches Polygon ist planar (liegt vollständig in einer Ebene) und seine Kanten überschneiden sich nicht gegenseitig (nicht-überschlagend).

### Triangulierung & Ear-Clipping

**Definition**:
Jedes einfache Polygon mit k Punkten lässt sich in k-2 Dreiecke zerlegen. Ein Ohr ist ein aus drei aufeinanderfolgenden Punkten gebildetes inneres Dreieck, das von keiner Kante überschnitten wird. Das Zwei-Ohren-Theorem besagt, dass jedes einfache Polygon mit mehr als drei Punkten mindestens zwei Ohren besitzt. Der Algorithmus sucht und schneidet fortlaufend Ohren ab, bis nur noch ein Dreieck übrig ist. Naive Laufzeit: O(n^3); optimierte Laufzeit: O(n^2), wenn effizient geprüft wird, ob andere Eckpunkte im Ohr liegen.

### Skalarprodukt (Dot Product)

**Definition**:
Für Vektoren a, b ist a · b = a_x * b_x + a_y * b_y + a_z * b_z = |a| * |b| * cos(alpha). Haupteigenschaften: Orthogonale Vektoren haben ein Skalarprodukt von 0. Wird zur Berechnung des Kosinus des Winkels zwischen Vektoren und zur Bestimmung des Reflexionsvektors r = v - 2(v · n)n genutzt (wobei n der normalisierte Oberflächennormalenvektor ist).

**Beispiel-Code**:
```java
Vector3df v = {1.0f, 0.0f, -1.0f};
Vector3df n = {0.0f, 0.0f, 1.0f}; // normalisiert
v.normalize();
Vector3df r = v.get_reflective(n); // r = v - 2 * (v * n) * n
```

### Kreuzprodukt (Cross Product)

**Definition**:
Nur für 3D-Vektoren definiert: a x b = (a_y*b_z - a_z*b_y, a_z*b_x - a_x*b_z, a_x*b_y - a_y*b_x). Das Ergebnis ist ein Vektor, der orthogonal auf der durch a und b aufgespannten Ebene steht (Rechte-Hand-Regel). Seine Länge |a x b| = |a| * |b| * sin(alpha) entspricht der Fläche des aufgespannten Parallelogramms (bzw. doppelte Dreiecksfläche). Es ist antikommutativ: a x b = -(b x a).

**Beispiel-Code**:
```java
Vector3df a = {1.0f, 0.0f, 0.0f};
Vector3df b = {0.0f, 1.0f, 0.0f};
Vector3df c = a.cross_product(b); // c = {0.0f, 0.0f, 1.0f}
```

### Baryzentrische Koordinaten

**Definition**:
Stellen einen Punkt p in der Ebene eines Dreiecks abc als Linearkombination p = u · a + v · b + w · c mit der Nebenbedingung u + v + w = 1 (bzw. w = 1 - u - v) dar. Liegen u, v, w alle im Intervall [0, 1], so liegt der Punkt p innerhalb des Dreiecks. Sie werden zur linearen Interpolation von Attributen (Farben, Texturkoordinaten, Normalen) über die Dreiecksfläche verwendet.

### Möller-Trumbore-Verfahren

**Definition**:
Ein optimiertes LGS-Lösungsverfahren zur Berechnung des Schnittpunkts eines Strahls g(t) = o + t·d mit einem Dreieck abc. Stellt das Gleichungssystem o + t·d = u·a + v·b + (1-u-v)·c auf und löst es direkt mit der Cramerschen Regel nach t, u und v auf. Dies spart Speicher und Operationen, da die Ebenengleichung nicht explizit bestimmt werden muss.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben sei ein einfacher, planarer Streckenzug, der ein Pol...

- **Klausurrelevant**: Ja (Tags: `klausur_ws_2024_2025, polygon, triangulation`)


#### Aufgabenstellung:
Gegeben sei ein einfacher, planarer Streckenzug, der ein Polygon mit k = 8 Eckpunkten beschreibt. In wie viele Dreiecke lässt sich dieses Polygon maximal zerlegen, und wie lautet das Theorem, das die Existenz solcher Dreiecke garantiert?


#### Musterlösung:
Ein einfaches Polygon mit k Eckpunkten lässt sich in genau k - 2 Dreiecke zerlegen. Für k = 8 ergibt sich:
Anzahl Dreiecke = 8 - 2 = 6 Dreiecke.
Die Existenz dieser Dreiecke (bzw. des Triangulierungsalgorithmus) wird durch das Zwei-Ohren-Theorem garantiert, welches besagt, dass jedes einfache Polygon mit k > 3 Eckpunkten mindestens zwei Ohren (vom Rand ungeschnittene innere Dreiecke aus drei aufeinanderfolgenden Eckpunkten) besitzt.


#### Typische Stolpersteine / Fehlerquellen:
Falsche Formel verwendet (z. B. k statt k-2) oder Verwechslung mit nicht-einfachen (überschlagenden) Polygonen, bei denen das Zwei-Ohren-Theorem nicht gilt.


---

### Aufgabe 2: Berechnen Sie den Schnittpunkt S eines Halbstrahls g(t) = o ...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_1, klausur_vorbereitung, schnittpunkt, lgs`)


#### Aufgabenstellung:
Berechnen Sie den Schnittpunkt S eines Halbstrahls g(t) = o + t · d mit dem Dreieck abc sowie die baryzentrischen Koordinaten u, v, w des Schnittpunkts. Gegeben sind:
o = (0, 2, 1), d = (1, 0, -1)
a = (1, 3, -1), b = (4, 1, -1), c = (1, 1, -1)


#### Musterlösung:
Wir stellen das lineare Gleichungssystem (LGS) auf:
o + t · d = u · a + v · b + (1 - u - v) · c
Dies lässt sich umformen zu:
-t · d + u · (a - c) + v · (b - c) = o - c
Mit den gegebenen Vektoren:
d = (1, 0, -1) => -d = (-1, 0, 1)
a - c = (0, 2, 0)
b - c = (3, 0, 0)
o - c = (-1, 1, 2)
In Matrixform A · (t, u, v)^T = o - c mit:
| -1  0  3 |   | t |   | -1 |
|  0  2  0 | · | u | = |  1 |
|  1  0  0 |   | v |   |  2 |
Wir berechnen det(A):
det(A) = -1 * (2*0 - 0*0) - 0 + 3 * (0*0 - 2*1) = 0 - 6 = -6.
Nun wenden wir die Cramersche Regel an:
1) t berechnen (erste Spalte durch o-c ersetzen):
det(A_t) = det| -1  0  3 | = -1*(2*0) - 0 + 3*(1*0 - 2*2) = -12.
          |  1  2  0 |
          |  2  0  0 |
t = det(A_t) / det(A) = -12 / -6 = 2.

2) u berechnen (zweite Spalte durch o-c ersetzen):
det(A_u) = det| -1 -1  3 | = -1*(1*0 - 2*0) - (-1)*(0*0 - 2*1) + 3*(0*2 - 1*1) = -3.
          |  0  1  0 |
          |  1  2  0 |
u = det(A_u) / det(A) = -3 / -6 = 0.5.

3) v berechnen (dritte Spalte durch o-c ersetzen):
det(A_v) = det| -1  0 -1 | = -1*(2*2 - 0*1) - 0 + (-1)*(0*0 - 2*1) = -4 + 2 = -2.
          |  0  2  1 |
          |  1  0  2 |
v = det(A_v) / det(A) = -2 / -6 = 1/3.

4) w berechnen:
w = 1 - u - v = 1 - 0.5 - 1/3 = 1/6.
Da t = 2 > 0 und u, v, w alle im Intervall [0, 1] liegen, liegt der Schnittpunkt innerhalb des Dreiecks.
Schnittpunkt S = g(2) = (2, 2, -1).


#### Typische Stolpersteine / Fehlerquellen:
Rechenfehler bei der Determinante oder beim Aufstellen der Matrix (z. B. Vorzeichen bei -d). Vergessen zu prüfen, ob die baryzentrischen Koordinaten im Bereich [0, 1] liegen.


---

### Aufgabe 3: Gegeben ist eine Kugel mit Radius r und Mittelpunkt m sowie ...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_1, kugel, schnittpunkt`)


#### Aufgabenstellung:
Gegeben ist eine Kugel mit Radius r und Mittelpunkt m sowie ein Halbstrahl g(t) = o + t · d (t >= 0). Leiten Sie die Gleichung zur Schnittpunktberechnung her und bringen Sie diese in eine quadratische Form at^2 + bt + c = 0.


#### Musterlösung:
Für alle Punkte p auf der Kugeloberfläche gilt:
(p - m)^2 = r^2
Wir setzen p = g(t) = o + t · d in die Kugelgleichung ein:
(o + t · d - m)^2 = r^2
((o - m) + t · d)^2 = r^2
(o - m)^2 + 2 · t · (o - m) · d + t^2 · d^2 = r^2
t^2 · d^2 + t · (2 · (o - m) · d) + (o - m)^2 - r^2 = 0
Dies entspricht der Form at^2 + bt + c = 0 mit:
a = d^2 = d · d
b = 2 · (o - m) · d
c = (o - m)^2 - r^2
Die Lösung für t ergibt sich über die abc-Formel:
t = (-b +- sqrt(b^2 - 4ac)) / (2a)
Wenn die Diskriminante (b^2 - 4ac) negativ ist, gibt es keinen reellen Schnittpunkt (der Strahl verfehlt die Kugel). Wir betrachten nur t >= 0.


#### Typische Stolpersteine / Fehlerquellen:
Klammern beim Quadrieren der Vektoren falsch aufgelöst (Skalarprodukt beachten). Vergessen, dass d^2 und (o-m)^2 Skalarprodukte sind, keine einfachen Skalarmultiplikationen.




---

# Kapitel 2: Bildrepräsentation

## 📖 Guidelines

### Das Problem
Die Brücke zwischen kontinuierlichen geometrischen Modellen im euklidischen Raum und der physischen Anzeige auf Hardware erfordert diskrete Datenstrukturen und Koordinatensysteme. Unterschiedliche Grafiktypen (Raster vs. Vektor) und Speicherformate (wie Netpbm oder PDF) müssen verstanden und korrekt angesteuert werden, um Bilddaten verlustfrei zu verarbeiten.

### Die Lösung
Definition von Rastergrafiken (Pixelmatrix, Auflösung, additive Farbmischung RGB) und Vektorgrafiken (geometrische Objekte und Eigenschaften). Verwendung des einfachen, unkomprimierten Netpbm-PPM-Formats (P3, ASCII) zur Bildspeicherung. Verständnis des hierarchischen Aufbaus von PDF-Dateien (Header, Body mit Dictionaries und Content-Streams, xref-Tabelle, Trailer) zur geräteunabhängigen Dokumentendarstellung.

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer den Unterschied zwischen Rastergrafik (pixelbasiert, Auflösung) und Vektorgrafik (formbasiert, stufenlos skalierbar) erklären kann.
- Leite den Benutzer an, gültige PPM-Bilddateien im P3-Format (ASCII) mit korrektem Header (Magic Number P3, Breite, Höhe, Max-Farbwert) und RGB-Pixelwerten zu erstellen.
- Stelle sicher, dass der Benutzer den Aufbau einer PDF-Datei von hinten (Trailer -> xref -> Body -> Header) versteht und weiß, wie Pfad- und Farboperationen (m, l, S, RG, rg, re, B) codiert werden.


## 💡 Konzepte & Definitionen

### Rastergrafik

**Definition**:
Ein Bild wird durch eine zweidimensionale Matrix von farbigen Bildpunkten (Pixeln) repräsentiert. Die Anzahl der Spalten und Zeilen bestimmt die Auflösung. Farbbildschirme verwenden typischerweise eine additive Farbmischung aus Rot, Grün und Blau (RGB).

### Vektorgrafik

**Definition**:
Ein Bild wird durch geometrische Objekte (z. B. Linien, Kreise, Polygone) und deren Eigenschaften (z. B. Linienstärke, Farbe) in einem kontinuierlichen Koordinatensystem beschrieben. Vektorgrafiken besitzen keine inhärente Auflösung und sind stufenlos verlustfrei skalierbar.

### Portable Pixmap (PPM - P3)

**Definition**:
Ein textbasiertes (ASCII), unkomprimiertes Format zur Speicherung von RGB-Rastergrafiken. Die Datei beginnt mit der Magic Number 'P3', gefolgt von Breite und Höhe (in Pixeln) und dem maximalen Farbwert je Kanal. Die Pixel werden zeilenweise von oben links nach unten rechts als RGB-Tripel aufgeschrieben.

**Beispiel-Code**:
```java
P3
3 2
255
255 0 0   0 255 0   0 0 255
255 255 255   128 128 128   0 0 0
```

### PDF-Dateistruktur

**Definition**:
Ein hierarchisch aufgebautes, geräteunabhängiges Dokumentenformat. Es besteht aus: Header (%PDF-X.Y), Body (indirekte Objekte wie Catalog, Pages, Page, Content-Streams), xref (Index aller Byte-Offsets der Objekte für wahlfreien Zugriff) und Trailer. Der Trailer enthält einen Verweis auf das Root-Objekt sowie das startxref-Offset. PDF-Reader verarbeiten Dateien von hinten nach vorne.

**Beispiel-Code**:
```java
trailer
<< /Size 5
   /Root 1 0 R >>
startxref
506
%%EOF
```

### PDF-Grafikbefehle

**Definition**:
Im Content-Stream einer PDF-Seite definieren ASCII-Operatoren die Geometrie und Farbgebung: 'm' (Startpunkt setzen/moveTo), 'l' (Linie zu Punkt/lineTo), 'S' (Pfad zeichnen/Stroke), 'w' (Linienstärke), 'RG'/'rg' (Strich-/Füllfarbe in RGB), 're' (Rechteck definieren), 'B' (Füllen und Zeichnen/Fill & Stroke).

**Beispiel-Code**:
```java
150 250 m
150 350 l
S
1.0 0.0 0.0 RG
0.5 0.75 1.0 rg
200 300 50 75 re
B
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Erklären Sie die Begriffe Vektorgrafik und Rastergrafik und ...

- **Klausurrelevant**: Ja (Tags: `klausur_ss_2024, klausur_ws_2023_2024, grafiktypen`)


#### Aufgabenstellung:
Erklären Sie die Begriffe Vektorgrafik und Rastergrafik und nennen Sie jeweils ein typisches Anwendungsbeispiel oder Dateiformat.


#### Musterlösung:
1. Rastergrafik:
- Definition: Repräsentation eines Bildes durch ein festes Raster (Matrix) aus Farbwerten (Pixeln). Sie hat eine feste Auflösung. Bei Vergrößerung kommt es zu Pixelierung (Treppenstufen).
- Anwendung/Format: Fotos, digitale Malerei; Formate: PNG, JPEG, BMP, PPM.

2. Vektorgrafik:
- Definition: Beschreibung des Bildes durch mathematische Objekte (Punkte, Pfade, Formen) und deren Attribute (Farbe, Füllung). Sie ist auflösungsunabhängig und lässt sich stufenlos ohne Qualitätsverlust skalieren.
- Anwendung/Format: Logos, Schriftarten, technische Zeichnungen; Formate: SVG, PDF, EPS.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung der Begriffe oder fälschliche Annahme, dass Vektorgrafiken eine feste Pixelanzahl besitzen.


---

### Aufgabe 2: Geben Sie eine vollständige PPM-Datei im ASCII-Text-Format (...

- **Klausurrelevant**: Ja (Tags: `klausur_ss_2024, ppm, rastergrafik`)


#### Aufgabenstellung:
Geben Sie eine vollständige PPM-Datei im ASCII-Text-Format (P3) für eine 5x3-Rastergrafik an. Die Grafik besteht aus einer oberen Reihe blauer Pixel, einer mittleren Reihe grauer Pixel (mittlerer Farbwert) und einer unteren Reihe roter Pixel. Der maximale Farbwert soll 16 betragen.


#### Musterlösung:
P3
5 3
16
0 0 16   0 0 16   0 0 16   0 0 16   0 0 16
8 8 8    8 8 8    8 8 8    8 8 8    8 8 8
16 0 0   16 0 0   16 0 0   16 0 0   16 0 0


#### Typische Stolpersteine / Fehlerquellen:
Falsche Anzahl Spalten/Zeilen im Header (z.B. 3 5 statt 5 3). Verwendung von falschen Farbwerten (z. B. 255 statt 16 für Blau/Rot oder 128 statt 8 für Grau bei Max-Farbwert 16). Fehlende Magic Number 'P3'.




---

# Kapitel 3: Raytracing

## 📖 Guidelines

### Das Problem
Die Erzeugung photorealistischer Bilder erfordert die Simulation der physikalischen Ausbreitung von Lichtstrahlen. Ein naiver Vorwärts-Ansatz ist ineffizient, da die meisten Lichtstrahlen die Kamera nicht treffen. Zudem führen unvollständige Rekursionen, Alias-Effekte und numerische Ungenauigkeiten zu visuellen Fehlern wie harten Kanten, fehlenden Details oder Rauschen.

### Die Lösung
Verwendung der Rückwärts-Strahlverfolgung (Backwards-Raytracing) vom Auge durch die Bildebene in die Szene. Berechnung von Primärstrahlen (Schnittpunkte mit Objekten wie Kugeln und Dreiecken), Lambert-Beleuchtung (diffuser Anteil) und Sekundärstrahlen für Schatten (Schattenstrahlen mit epsilon-Offset gegen Schattenakne). Whitted-Style Raytracing erweitert dies um rekursive Spiegelungen und Brechungen (Snellius-Brechungsgesetz, Schlick-Approximation für Fresnel-Reflexion) mit einer festen Rekursionstiefe. Alias-Effekte werden durch Supersampling oder stochastisches (verteiltes) Raytracing minimiert.

## 🤖 KI-Anweisungen (AI Instructions)

- Leite den Benutzer an, die Funktionsweise von Backwards-Raytracing zu verstehen und Primärstrahlen für orthogonale und perspektivische Projektionen zu generieren.
- Stelle sicher, dass der Benutzer diffuse Beleuchtung nach Lambert (L = k_d * I * max(0, n · l)) berechnen kann.
- Erzwinge das Hinzufügen eines kleinen Offsets (epsilon * n) beim Starten von Sekundärstrahlen, um Schattenakne (Self-Intersection) zu verhindern.
- Stelle sicher, dass der Benutzer Brechungswinkel mittels Snellius-Gesetz berechnen und Totalreflexion anhand der Diskriminante unter der Wurzel identifizieren kann.
- Leite den Benutzer an, die Schlicksche Approximation zur Gewichtung von Reflexions- und Transmissionsanteilen anzuwenden.
- Stelle sicher, dass der Benutzer Aliasing-Effekte durch Supersampling (Mittelwertbildung mehrerer Subpixel-Strahlen) und Distributed Raytracing (stochastische Verteilung) reduzieren kann.


## 💡 Konzepte & Definitionen

### Backwards-Raytracing

**Definition**:
Verfahren, bei dem Lichtstrahlen rückwärts verfolgt werden: vom Auge des Betrachters durch jedes Pixel des virtuellen Bildschirms in die Szene hinein (Primärstrahlen). An den getroffenen Objektoberflächen werden Sekundärstrahlen (Schatten-, Reflexions-, Transmissionsstrahlen) erzeugt, um Beleuchtung, Schatten und Spiegelungen zu berechnen.

### Strahlengenerierung (Ray Generation)

**Definition**:
Erzeugung des Sehstrahls für ein Pixel (i, j) mit Koordinaten (p_u, p_v). Bei Parallelprojektion sind alle Strahlen parallel (ray.origin = e + p_u*u + p_v*v, ray.direction = -w). Bei Zentralprojektion starten alle Strahlen im Augenpunkt e (ray.origin = e, ray.direction = -d*w + p_u*u + p_v*v, mit Bildebenenabstand d).

**Beispiel-Code**:
```java
Ray3df get_ray_perspective(float i, float j, Vector3df e, Vector3df u, Vector3df v, Vector3df w, float d, float l, float r, float b, float t, float nx, float ny) {
  float pu = l + (r - l) * (i + 0.5f) / nx;
  float pv = b + (t - b) * (j + 0.5f) / ny;
  Vector3df dir = -d * w + pu * u + pv * v;
  dir.normalize();
  return Ray3df{e, dir};
}
```

### Lambertian Shading

**Definition**:
Beleuchtungsmodell für perfekt diffuse (matte) Reflexion. Die wahrgenommene Lichtintensität L hängt ausschließlich vom Einfallswinkel des Lichts ab: L = k_d * I * max(0, n · l), wobei n die Oberflächennormale, l die Richtung zur Lichtquelle (beide normalisiert), I die Lichtintensität und k_d der diffuse Reflexionskoeffizient ist. Unabhängig von der Blickrichtung.

### Schattenakne & Epsilon-Offset

**Definition**:
Visueller Fehler (dunkle Punkte/Muster auf beleuchteten Flächen), der durch numerische Ungenauigkeiten entsteht. Wenn der Schnittpunkt p eines Strahls berechnet wird, kann er leicht unter/hinter der Oberfläche liegen. Ein neuer Schatten- oder Reflexionsstrahl schneidet dann sofort wieder dasselbe Objekt. Lösung: Startpunkt um epsilon * n in Normalenrichtung verschieben (p_neu = p + epsilon * n).

**Beispiel-Code**:
```java
Vector3df shadow_ray_origin = hit_point + 1e-4f * normal;
```

### Brechung & Snellius-Gesetz

**Definition**:
Tritt beim Übergang eines Strahls in ein anderes Medium auf: eta_1 * sin(theta) = eta_2 * sin(phi). Die Richtung des gebrochenen Strahls t berechnet sich als t = n*d - (n*(d · n) + sqrt(1 - n^2*(1 - (d · n)^2)))*n mit n = eta_1/eta_2. Wenn der Term unter der Wurzel (die Diskriminante) negativ wird, tritt Totalreflexion auf (keine Brechung).

**Beispiel-Code**:
```java
Vector3df t;
bool refract_exists = refract(eta1/eta2, normal, direction, t);
```

### Schlicksche Approximation

**Definition**:
Eine Näherungsformel zur Berechnung des reflexiven Anteils R(theta) eines transparenten Materials in Abhängigkeit vom Einfallswinkel. R(theta) = R_0 + (1 - R_0)*(1 - cos(theta))^5 mit R_0 = ((eta_1 - eta_2)/(eta_1 + eta_2))^2 und cos(theta) = -d · n. Der gebrochene Anteil ist 1 - R(theta).

### Distributed Raytracing (Stochastisches Raytracing)

**Definition**:
Erweiterung des Raytracings, bei der mehrere Strahlen stochastisch (zufällig) abgelenkt werden. Wird für Antialiasing (Zufallsverteilung der Strahlen innerhalb eines Pixels), weiche Schatten (Abtasten von Flächenlichtquellen), Tiefenunschärfe und matte Reflexionen verwendet.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Erklären Sie den Unterschied zwischen Raycasting und Raytrac...

- **Klausurrelevant**: Ja (Tags: `klausur_ss_2024, raytracing, raycasting`)


#### Aufgabenstellung:
Erklären Sie den Unterschied zwischen Raycasting und Raytracing.


#### Musterlösung:
1. Raycasting:
- Berücksichtigt nur Primärstrahlen (Strahlen vom Auge durch die Pixel).
- Es werden keine Sekundärstrahlen (für Spiegelung, Brechung oder Schatten) erzeugt.
- Schattierung basiert meist nur auf den direkten Materialeigenschaften und ggf. einfacher lokaler Beleuchtung.

2. Raytracing (insb. Whitted-Style):
- Verfolgt Strahlen rekursiv weiter (Sekundärstrahlen).
- Ermöglicht globale Effekte wie Spiegelung (Reflexionsstrahl), Brechung (Transmissionsstrahl) und Schatten (Schattenstrahl zur Lichtquelle).


#### Typische Stolpersteine / Fehlerquellen:
Fälschlicherweise anzunehmen, dass Raycasting Schatten erzeugt oder dass Raycasting und Raytracing synonym sind.


---

### Aufgabe 2: Gegeben sei eine spiegelnde Oberfläche mit der normalisierte...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_2, klausur_vorbereitung, reflexion, schattenakne`)


#### Aufgabenstellung:
Gegeben sei eine spiegelnde Oberfläche mit der normalisierten Normale n = (0, 1, 0) an einem Schnittpunkt p. Der normalisierte Blickrichtungsvektor (vom Auge zum Punkt p) sei r = (sqrt(2)/2, -sqrt(2)/2, 0).
1) Berechnen Sie die Richtung des Reflexionsstrahls.
2) Warum darf der Reflexionsstrahl nicht exakt bei p starten, und wie wird dies gelöst?


#### Musterlösung:
1) Berechnung des Reflexionsvektors:
Die Formel lautet: refl = r - 2 * (r · n) * n
- Skalarprodukt r · n:
r · n = (sqrt(2)/2)*0 + (-sqrt(2)/2)*1 + 0*0 = -sqrt(2)/2.
- Einsetzen in die Formel:
refl = r - 2 * (-sqrt(2)/2) * n = r + sqrt(2) * n
refl = (sqrt(2)/2, -sqrt(2)/2, 0) + (0, sqrt(2), 0)
refl = (sqrt(2)/2, sqrt(2)/2, 0).
Die Richtung des Reflexionsstrahls ist (sqrt(2)/2, sqrt(2)/2, 0).

2) Epsilon-Offset:
Wenn der Strahl exakt bei p startet, kann es aufgrund von Rundungsfehlern bei Gleitkommazahlen dazu kommen, dass der Strahl sofort wieder dieselbe Oberfläche schneidet (Schattenakne). Dies wird gelöst, indem der Startpunkt des Reflexionsstrahls leicht in Normalenrichtung verschoben wird: p_neu = p + epsilon * n, mit einem sehr kleinen epsilon (z.B. 1e-4).


#### Typische Stolpersteine / Fehlerquellen:
Falsches Vorzeichen beim Skalarprodukt r · n oder falsches Addieren/Subtrahieren in der Formel. Vergessen des Epsilon-Offsets oder ungenaue Begründung (z.B. 'damit es schneller geht').


---

### Aufgabe 3: Ein Lichtstrahl trifft aus der Luft (eta_1 = 1.0) auf eine G...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_2, refraktion, totalreflexion`)


#### Aufgabenstellung:
Ein Lichtstrahl trifft aus der Luft (eta_1 = 1.0) auf eine Glasoberfläche (eta_2 = 1.5). Der Einfallswinkel des Strahls zur Normalen beträgt theta = 30 Grad. Berechnen Sie den Brechungswinkel phi im Glas. Kann bei diesem Übergang Totalreflexion auftreten? Begründen Sie.


#### Musterlösung:
1) Berechnung des Brechungswinkels:
Nach dem Snelliusschen Brechungsgesetz gilt:
eta_1 * sin(theta) = eta_2 * sin(phi)
1.0 * sin(30°) = 1.5 * sin(phi)
Da sin(30°) = 0.5:
0.5 = 1.5 * sin(phi) => sin(phi) = 0.5 / 1.5 = 1/3.
phi = arcsin(1/3) ~ 19.47°.
Der Brechungswinkel im Glas beträgt ca. 19.47 Grad.

2) Totalreflexion:
Totalreflexion kann nur auftreten, wenn Licht von einem optisch dichteren Medium (höherer Brechungsindex) in ein optisch dünneres Medium (niedrigerer Brechungsindex) übergeht (also eta_1 > eta_2). Da hier der Strahl von Luft (1.0) in Glas (1.5) übergeht (eta_1 < eta_2), ist sin(phi) = (eta_1/eta_2)*sin(theta) stets <= 1. Es kann somit keine Totalreflexion auftreten.


#### Typische Stolpersteine / Fehlerquellen:
Falsches Einsetzen der Brechungsindizes (Brechungsgesetz umgedreht). Falsche Bedingung für Totalreflexion angegeben (z. B. eta_1 < eta_2).




---

# Kapitel 4: Transformationsmatrizen

## 📖 Guidelines

### Das Problem
In der Computergrafik müssen Objekte (Spielfiguren, Asteroiden, Wände) relativ zur Spielwelt oder anderen Objekten skaliert, rotiert, gescheert oder gespiegelt werden. Einfache Vektoroperationen reichen nicht aus, um komplexe Abfolgen von Translationen und Rotationen in einer einheitlichen und performanten Weise durchzuführen, insbesondere da Matrixmultiplikationen nicht-kommutativ sind.

### Die Lösung
Einführung homogener Koordinaten zur Darstellung affinen Transformationen (Translation, Rotation, Skalierung) über einheitliche quadratische Transformationsmatrizen (3x3 für 2D, 4x4 für 3D). Strukturierte Komposition von Transformationen durch Matrixmultiplikation in der korrekten Reihenfolge (Skalierung, dann Rotation, dann Translation). Definition von Scherungen, Spiegelungen und Wechseln zwischen lokalen Koordinatensystemen (Frame-to-Canonical und Canonical-to-Frame).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer homogene Transformationsmatrizen für Translation, Skalierung und Rotation aufstellen kann.
- Leite den Benutzer an, die Reihenfolge der Transformationskomposition strikt einzuhalten (erst Skalieren, dann Rotieren, dann Verschieben bei lokalem Ursprung) und betone die Nicht-Kommutativität.
- Erläutere dem Benutzer wie homogene Koordinaten wieder in kartesische Koordinaten umgerechnet werden (Teilen durch die w-Komponente).
- Stelle sicher, dass der Benutzer den Unterschied zwischen lokalen und globalen Koordinaten versteht und Frame-to-Canonical-Matrizen aufstellen kann.


## 💡 Konzepte & Definitionen

### Skalierungsmatrix

**Definition**:
Eine Matrix, die ein Objekt entlang der Koordinatenachsen streckt oder staucht. 3D-Skalierungsmatrix: Hauptdiagonale enthält die Faktoren s_x, s_y, s_z, Rest ist 0. 2D analog in 3x3.

### Translationsmatrix

**Definition**:
Ermöglicht das Verschieben von Punkten. Da Translation eine Addition ist, lässt sie sich in kartesischen Koordinaten nicht als Matrixmultiplikation darstellen. In homogenen Koordinaten enthält die letzte Spalte der Matrix den Verschiebungsvektor (v_x, v_y, v_z, 1)^T.

### Rotationsmatrix

**Definition**:
Dreht ein Objekt um einen Winkel alpha im Uhrzeigersinn (negativer Winkel) oder gegen den Uhrzeigersinn (positiver Winkel). Drehungen im R2 bzw. um die z-Achse im R3 nutzen Cosinus- und Sinustermwerte in den Koordinatenpositionen.

### Homogene Koordinaten

**Definition**:
Erweitern einen n-dimensionalen Vektor um eine Dimension (Wert w, meist 1). Ein homogener Vektor (x : y : z : w) wird durch Teilen aller Komponenten durch w in kartesische Koordinaten (x/w, y/w, z/w) umgerechnet. Ermöglicht einheitliche Matrizen für Translationen und Projektionen.

### Komposition von Transformationen

**Definition**:
Mehrere Transformationen werden durch Multiplikation ihrer Matrizen kombiniert. Da Matrizenmultiplikation nicht kommutativ ist (A · B != B · A), ist die Reihenfolge entscheidend. Um ein Objekt um seinen lokalen Ursprung zu manipulieren, gilt typischerweise: Erst Skalieren, dann Rotieren, dann Translieren. Die Gesamtmatrix ergibt sich als M = Translation · Rotation · Skalierung (von rechts nach links auf den Punkt angewandt).

### Koordinatensystemwechsel

**Definition**:
Ein lokales Koordinatensystem wird durch Basisvektoren u, v, w und den Ursprung e aufgespannt. Die Frame-to-Canonical-Matrix transformiert lokale Koordinaten in globale Weltkoordinaten. Sie wird gebildet, indem die Vektoren u, v, w und e als Spalten in eine Matrix eingetragen werden. Die Inverse führt die Transformation von global nach lokal durch (Canonical-to-Frame).

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben sei eine kreisförmige Spielfigur mit Durchmesser 2 (...

- **Klausurrelevant**: Ja (Tags: `klausur_ss_2024, klausur_ws_2024_2025, transformation, komposition`)


#### Aufgabenstellung:
Gegeben sei eine kreisförmige Spielfigur mit Durchmesser 2 (Radius 1) und Mittelpunkt im Punkt (1, 1). Diese Figur soll wie folgt transformiert werden: Ihre Größe wird halbiert, sie wird um 45 Grad im Uhrzeigersinn gedreht, und ihr neuer Mittelpunkt soll im Punkt (3, -0.5) liegen. Stellen Sie das Produkt der 3x3-Transformationsmatrizen in homogenen Koordinaten in der richtigen Reihenfolge auf (ohne es auszumultiplizieren).


#### Musterlösung:
Um die Figur korrekt um ihren lokalen Mittelpunkt (1, 1) zu transformieren, müssen wir sie zuerst in den Koordinatenursprung verschieben, dort skalieren und rotieren, und dann an die neue Position (3, -0.5) verschieben.

1. Verschiebung in den Ursprung:
T_in_ursprung = 
| 1  0 -1 |
| 0  1 -1 |
| 0  0  1 |

2. Skalierung um Faktor 0.5 (Größe halbieren):
S = 
| 0.5  0    0 |
| 0    0.5  0 |
| 0    0    1 |

3. Rotation um 45 Grad im Uhrzeigersinn (alpha = -45°):
Da cos(-45°) = sqrt(2)/2 und sin(-45°) = -sqrt(2)/2:
R = 
|  cos(-45°) -sin(-45°) 0 |
|  sin(-45°)  cos(-45°) 0 |
|  0          0          1 |

=> R = 
|  sqrt(2)/2  sqrt(2)/2 0 |
| -sqrt(2)/2  sqrt(2)/2 0 |
|  0          0          1 |

4. Verschiebung an den neuen Mittelpunkt (3, -0.5):
T_nach_ziel = 
| 1  0   3   |
| 0  1  -0.5 |
| 0  0   1   |

Die zusammengesetzte Transformation wird von rechts nach links auf die Punkte angewendet:
M = T_nach_ziel · R · S · T_in_ursprung

M = 
| 1  0   3   |   |  sqrt(2)/2  sqrt(2)/2 0 |   | 0.5  0    0 |   | 1  0 -1 |
| 0  1  -0.5 | · | -sqrt(2)/2  sqrt(2)/2 0 | · | 0    0.5  0 | · | 0  1 -1 |
| 0  0   1   |   |  0          0          1 |   | 0    0    1 |   | 0  0  1 |


#### Typische Stolpersteine / Fehlerquellen:
Falsche Reihenfolge der Matrizen (z. B. von links nach rechts angewandt). Vergessen, die Figur vor der Rotation/Skalierung in den Ursprung zu verschieben (was zu einer ungewollten Verschiebung führen würde). Falsches Vorzeichen bei der Drehung im Uhrzeigersinn (Sinusterme vertauscht).


---

### Aufgabe 2: Was bewirkt die homogene Transformationsmatrix M, wenn man s...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_3, homogene_koordinaten, skalierung`)


#### Aufgabenstellung:
Was bewirkt die homogene Transformationsmatrix M, wenn man sie auf einen Vektor (x, y, z, 1)^T anwendet?
M = 
| 1  0  0  0 |
| 0  1  0  0 |
| 0  0  1  0 |
| 0  0  0  a |
(mit a > 0 und a != 1)


#### Musterlösung:
Die Anwendung der Matrix M ergibt den homogenen Vektor:
M · (x, y, z, 1)^T = (x, y, z, a)^T

Um den Vektor wieder in kartesische Koordinaten umzurechnen, müssen wir alle Komponenten durch die homogene Komponente w (hier w = a) dividieren:
p_kartesisch = (x/a, y/a, z/a)

Anschaulich bewirkt die Matrix also eine uniforme Skalierung des gesamten euklidischen Raums um den Faktor 1/a entlang aller drei Raumachsen.


#### Typische Stolpersteine / Fehlerquellen:
Annahme, die Matrix habe gar keinen Effekt oder skaliere um Faktor a statt 1/a.




---

# Kapitel 5: Projektionen

## 📖 Guidelines

### Das Problem
Um eine 3D-Szene auf einem 2D-Bildschirm anzuzeigen, müssen die 3D-Punkte der Szene projiziert werden. Die Projektion muss die Tiefenrelationen (Nähe/Ferne zum Betrachter) beibehalten, perspektivische Verkürzungen simulieren (Objektgröße schrumpft mit der Entfernung) und die Sichtkamera beliebig im Raum positionieren können.

### Die Lösung
Durchführung der dreistufigen Viewing-Transformation. 1) Kamera-Transformation (LookAt): Verschiebung und Drehung der Weltpunkte in den Kameraraum (Ursprung im Augenpunkt e, Blickrichtung entlang -w). 2) Projektions-Transformation: Zentralprojektion (perspektivische Projektion) unter Verwendung homogener Koordinaten zur Division durch die Tiefe z, sowie z-Mapping zur monotonen Abbildung der Tiefe im Bereich [n, f]. 3) Viewport-Transformation: Abbildung der normierten kanonischen Sichtbox [-1, 1]3 auf Pixelkoordinaten.

## 🤖 KI-Anweisungen (AI Instructions)

- Leite den Benutzer an, die LookAt-Kameratransformationsmatrix aus Augenpunkt e, Blickrichtung g und Up-Vektor t aufzustellen.
- Stelle sicher, dass der Benutzer die perspektivische Projektionsmatrix versteht und weiß, wie die Division durch w (die z-Koordinate) perspektivische Verkürzung bewirkt.
- Erkläre dem Benutzer das nicht-lineare z-Mapping zur Erhaltung der Tiefeninformation für den Tiefenpuffer.
- Stelle sicher, dass der Benutzer die Viewport-Transformation aufstellen kann, um kanonische Koordinaten auf die Bildschirmauflösung abzubilden.


## 💡 Konzepte & Definitionen

### Viewing-Transformation

**Definition**:
Die vollständige Kette von Transformationen, um Punkte aus dem Modellraum auf den Bildschirm zu projizieren: 1) Kamera-Transformation (LookAt): Model/World Space -> Camera Space. 2) Projektions-Transformation: Camera Space -> Clip/Canonical Space ([-1, 1]^3). 3) Viewport-Transformation: Clip Space -> Screen Space.

### Kamera-Transformation (LookAt)

**Definition**:
Verschiebt die Szene so, dass die Kamera im Ursprung liegt und blickt. Gegeben: Augenpunkt e, Blickrichtung g, Up-Vektor t. Orthonormalbasis berechnen: w = -g / |g| (z-Achse der Kamera zeigt nach hinten), u = (t x w) / |t x w| (x-Achse der Kamera zeigt nach rechts), v = w x u (y-Achse der Kamera zeigt nach oben). LookAt-Matrix ist M = R · T mit Rotation R (u, v, w in Zeilen) und Translation T (um -e).

### Zentralprojektion (Perspektive)

**Definition**:
Bildet Punkte auf eine Ebene im Abstand d ab. Perspektivische Verkürzung erfordert die Division durch die z-Koordinate. Da Matrizen linear sind, wird die Division aufgeschoben, indem die homogene w-Komponente auf z gesetzt wird (w' = z). Die Hardware führt nach dem Vertex-Shader die Division durch w durch.

### z-Mapping

**Definition**:
Die z-Koordinate wird nicht linear auf den Bereich [n, f] abgebildet (z. B. über p_z -> (n+f)*p_z - f*n), um Tiefenwerte für den z-Buffer zu erhalten. Dies führt dazu, dass Objekte nahe der Kamera eine viel höhere Tiefenauflösung besitzen als weit entfernte Objekte.

### Viewport-Transformation

**Definition**:
Transformiert die kanonischen Koordinaten aus dem Intervall [-1, 1]^3 in die tatsächlichen Bildschirm-Pixelkoordinaten [0, n_x - 1] x [0, n_y - 1].

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben sei eine Kamera mit dem Augenpunkt e = (1, 1, 1), de...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_3, klausur_vorbereitung, kamera, orthonormalbasis`)


#### Aufgabenstellung:
Gegeben sei eine Kamera mit dem Augenpunkt e = (1, 1, 1), der Blickrichtung g = (1, 0, 1) und dem Kamera-Up-Vektor t = (1, 1, 1). Berechnen Sie die Orthonormalbasis {u, v, w} für den Kameraraum (w soll in Richtung -g zeigen).


#### Musterlösung:
1) Vektor w berechnen (Gegenrichtung der Blickrichtung g):
|g| = sqrt(1^2 + 0^2 + 1^2) = sqrt(2).
w = -g / |g| = (-1/sqrt(2), 0, -1/sqrt(2)).

2) Vektor u berechnen (Rechts-Vektor mittels Kreuzprodukt t x w):
t x w = (t_y*w_z - t_z*w_y, t_z*w_x - t_x*w_z, t_x*w_y - t_y*w_x)
t x w = (1 * (-1/sqrt(2)) - 1 * 0,
         1 * (-1/sqrt(2)) - 1 * (-1/sqrt(2)),
         1 * 0 - 1 * (-1/sqrt(2)))
t x w = (-1/sqrt(2), 0, 1/sqrt(2)).

Länge von t x w:
|t x w| = sqrt((-1/sqrt(2))^2 + 0^2 + (1/sqrt(2))^2) = sqrt(1/2 + 1/2) = sqrt(1) = 1.0.
Daher ist u bereits normiert:
u = (-1/sqrt(2), 0, 1/sqrt(2)).

3) Vektor v berechnen (realer Up-Vektor mittels Kreuzprodukt w x u):
v = w x u = (w_y*u_z - w_z*u_y, w_z*u_x - w_x*u_z, w_x*u_y - w_y*u_x)
v = (0 * (1/sqrt(2)) - (-1/sqrt(2)) * 0,
     (-1/sqrt(2)) * (-1/sqrt(2)) - (-1/sqrt(2)) * (1/sqrt(2)),
     (-1/sqrt(2)) * 0 - 0 * (-1/sqrt(2)))
v = (0, 1/2 - (-1/2), 0) = (0, 1, 0).

Ergebnis:
u = (-sqrt(2)/2, 0, sqrt(2)/2)
v = (0, 1, 0)
w = (-sqrt(2)/2, 0, -sqrt(2)/2)


#### Typische Stolpersteine / Fehlerquellen:
Fehler beim Berechnen des Kreuzprodukts (Vorzeichenfehler). Vergessen der Normierung des w-Vektors oder des u-Vektors. Falsche Reihenfolge beim Kreuzprodukt w x u (u x w würde in die Gegenrichtung zeigen).


---

### Aufgabe 2: Stellen Sie die Viewport-Transformationsmatrix für eine Bild...

- **Klausurrelevant**: Ja (Tags: `klausur_ws_2024_2025, viewport, transformation`)


#### Aufgabenstellung:
Stellen Sie die Viewport-Transformationsmatrix für eine Bildschirmauflösung von 512 x 368 Pixeln auf. Gehen Sie davon aus, dass die kanonischen Koordinaten im Bereich [-1, 1]^3 liegen.


#### Musterlösung:
Die allgemeine Formel für die Viewport-Transformationsmatrix lautet:
| n_x/2    0      0    (n_x-1)/2 |
|   0    n_y/2    0    (n_y-1)/2 |
|   0      0      1        0     |
|   0      0      0        1     |

Mit n_x = 512 und n_y = 368:
n_x/2 = 256
(n_x-1)/2 = 511/2 = 255.5
n_y/2 = 184
(n_y-1)/2 = 367/2 = 183.5

Einsetzen der Werte ergibt:
| 256   0   0  255.5 |
|   0 184   0  183.5 |
|   0   0   1    0   |
|   0   0   0    1   |


#### Typische Stolpersteine / Fehlerquellen:
Verwendung von n_x statt n_x/2 oder Vergessen der Verschiebung um -1 in der Translation (z. B. 256 statt 255.5).




---

# Kapitel 6: Graphik-Pipeline & Rasterung

## 📖 Guidelines

### Das Problem
Die geometrisch transformierten und projizierten 2D-Primitive (Linien und Dreiecke) müssen in diskrete Pixel auf dem Bildschirm umgewandelt (rasterisiert), auf Verdeckung geprüft und außerhalb des Sichtvolumens abgeschnitten (geclippt) werden. Eine ineffiziente Auswertung führt zu Performanceproblemen oder Bildfehlern.

### Die Lösung
Ablauf der Phasen der GPU-Graphik-Pipeline (Command Stream, Vertex Processing, Rasterung, Fragment Processing, Blending, Framebuffer). Rasterung von Linien mit dem Midpoint-Algorithmus (Bresenham) unter Nutzung inkrementeller Entscheidungen. Rasterung von Dreiecken über Bounding-Boxen und baryzentrische Koordinaten zur Interpolation von Farben (Gouraud-Shading). Nutzung des Tiefenpuffers (z-Buffers) zur Verdeckungsprüfung und Clipping (Teilen von Dreiecken an den Frustumebenen).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer die Phasen der Graphics-Pipeline und deren Zweck (Vertex- vs. Fragment-Shader) erklären kann.
- Leite den Benutzer an, den Midpoint-Algorithmus zur Linienrasterung auszuführen und die implizite Geradengleichung aufzustellen.
- Stelle sicher, dass der Benutzer Dreiecksrasterung über Bounding-Boxen und baryzentrische Koordinaten erklären kann.
- Erkläre die Funktionsweise des z-Buffers (Tiefenpuffer) zur pixelgenauen Sichtbarkeitsprüfung.
- Leite den Benutzer an, Clipping-Algorithmen (Schnittpunkt Strecke mit Ebene und Dreieckszerlegung) auszuführen.


## 💡 Konzepte & Definitionen

### Graphics Pipeline

**Definition**:
Der standardisierte Ablauf zur Darstellung von 3D-Geometrie auf einem 2D-Rasterbildschirm. Phasen: 1) Vertex Processing (Transformation von Punkten via Vertex Shader). 2) Rasterung (Primitive in Fragmente zerlegen). 3) Fragment Processing (Berechnung der Pixelfarbe via Fragment Shader). 4) Blending (Kombination mit dem Framebuffer unter Beachtung des z-Buffers).

### Midpoint-Linienalgorithmus

**Definition**:
Zeichnet Linien im Raster unter Vermeidung von Gleitkommaoperationen. Basiert auf der impliziten Geradengleichung f(x, y) = (y_0 - y_1)*x + (x_1 - x_0)*y + x_0*y_1 - x_1*y_0 = 0. Für eine Steigung m in [0, 1) wird ausgehend vom letzten Pixel (x, y) der Wert f(x + 1, y + 0.5) am Mittelpunkt evaluiert. Ist er < 0, liegt die Linie über dem Mittelpunkt (oberes Pixel wählen: y = y + 1), andernfalls das untere (y = y). Die Updates für d erfolgen rein additiv.

### Dreiecksrasterung (Bounding Box)

**Definition**:
Um ein Dreieck mit den Ecken p0, p1, p2 zu zeichnen, berechnet man dessen achsenparallele Bounding-Box (xmin = floor(min(x0,x1,x2)), etc.). Über alle Pixel in dieser Box wird iteriert und geprüft, ob die baryzentrischen Koordinaten u, v, w alle >= 0 sind. Wenn ja, wird das Pixel gezeichnet. Attribute wie Farbe werden über c = u*c0 + v*c1 + w*c2 interpoliert.

### z-Buffer (Tiefenpuffer)

**Definition**:
Zweidimensionaler Bildspeicher, der die z-Tiefe jedes geschriebenen Pixels speichert. Da in negativer z-Richtung geblickt wird, wird ein neues Fragment nur gezeichnet, wenn sein z-Wert größer (näher am Auge bei 0) ist als der bereits gespeicherte Wert. Verhindert das Zeichnen verdeckter Geometrie.

### Clipping & Ebenenschnitt

**Definition**:
Schneidet Geometrie außerhalb des Sichtvolumens (6 Ebenen) ab. Ein Schnittpunkt einer Strecke ab mit einer Ebene n · p + D = 0 existiert, wenn sgn(n · a + D) != sgn(n · b + D). Der Parameter t berechnet sich als t = (n · a + D) / (n · (a - b)). Das Dreieck wird bei Schnitten in bis zu drei neue Dreiecke aufgeteilt.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben sei eine Strecke s mit dem Anfangspunkt p0 = (2.5, 1...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_4, rasterung, midpoint, geradengleichung`)


#### Aufgabenstellung:
Gegeben sei eine Strecke s mit dem Anfangspunkt p0 = (2.5, 1.5) und dem Endpunkt p1 = (15.5, 6.5).
1) Stellen Sie die implizite Geradengleichung auf.
2) Bestimmen Sie die Steigung m.


#### Musterlösung:
1) Aufstellen der impliziten Geradengleichung:
Formel: (y0 - y1) · x + (x1 - x0) · y + x0 · y1 - x1 · y0 = 0
Mit x0 = 2.5, y0 = 1.5, x1 = 15.5, y1 = 6.5:
- (y0 - y1) = 1.5 - 6.5 = -5.
- (x1 - x0) = 15.5 - 2.5 = 13.
- x0 · y1 - x1 · y0 = 2.5 · 6.5 - 15.5 · 1.5 = 16.25 - 23.25 = -7.

Dies ergibt:
-5x + 13y - 7 = 0  (bzw. 5x - 13y + 7 = 0)

2) Steigung m:
m = (y1 - y0) / (x1 - x0) = (6.5 - 1.5) / (15.5 - 2.5) = 5 / 13 ~ 0.385.
Da m in [0, 1) liegt, ist der klassische Midpoint-Algorithmus direkt anwendbar.


#### Typische Stolpersteine / Fehlerquellen:
Rechenfehler bei den Produkten von Dezimalzahlen oder falsches Vorzeichen beim Umformen der Gleichung.


---

### Aufgabe 2: Erklären Sie das Funktionsprinzip des z-Buffers (Tiefenpuffe...

- **Klausurrelevant**: Ja (Tags: `klausur_ws_2023_2024, z_buffer, sichtbarkeit`)


#### Aufgabenstellung:
Erklären Sie das Funktionsprinzip des z-Buffers (Tiefenpuffers). Warum ist er in der modernen Computergrafik notwendig?


#### Musterlösung:
Der z-Buffer ist ein zweidimensionales Array von der Größe des Bildschirms, das für jedes Pixel die Tiefe (z-Koordinate) des dort zuletzt gezeichneten Szenenpunkts speichert.

Funktionsprinzip:
1. Vor dem Rendern wird der z-Buffer mit einem Maximalwert (z.B. -1.0 bei Blick in negative z-Richtung) initialisiert.
2. Beim Rasterisieren eines Fragments wird dessen berechnete z-Tiefe mit dem aktuellen Eintrag im z-Buffer an dieser Pixelposition verglichen.
3. Ist das Fragment näher am Betrachter (z-Wert größer), wird die Farbe im Framebuffer überschrieben und der neue z-Wert im z-Buffer gespeichert. Andernfalls wird das Fragment verworfen.

Notwendigkeit:
Er ermöglicht ein korrektes Rendern von sich überlappenden Objekten unabhängig von der Reihenfolge, in der die Dreiecke an die GPU geschickt werden (löst das Sichtbarkeitsproblem effizient auf Pixel- statt Objektebene).


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung der z-Blickrichtung (positive vs. negative z-Achse) und damit falsche Angabe der Vergleichsfunktion (GL_LESS vs. GL_GREATER).




---

# Kapitel 7: OpenGL

## 📖 Guidelines

### Das Problem
Die GPU-beschleunigte 3D-Bilderzeugung erfordert die Interaktion mit speziellen Grafik-APIs. Um Geometrie effizient an die GPU zu übertragen und dort flexibel über Shader (GLSL) zu verarbeiten, müssen komplexe Vertex-Layouts, Pufferobjekte (VBOs, VAOs) und Zustandseinstellungen (Culling, Depth-Test) korrekt konfiguriert werden, da fehlerhafte Bindungen zu schwarzem Bildschirm oder Grafikfehlern führen.

### Die Lösung
Verwendung von Vertex Buffer Objects (VBO) zur Speicherung von Vertex-Daten auf der GPU, Vertex Array Objects (VAO) zur Kapselung des Vertex-Layouts, und glVertexAttribPointer zur Zuweisung von Layout-IDs (Positionen, Farben, Texturkoordinaten). Implementierung von Vertex- und Fragment-Shadern in GLSL zur Definition von Transformationen und Pixelfarben. Aktivierung von Zuständen wie Backface-Culling (glCullFace) und z-Depth-Testing (glEnable(GL_DEPTH_TEST)).

## 🤖 KI-Anweisungen (AI Instructions)

- Leite den Benutzer an, Vertex-Layouts mit glVertexAttribPointer korrekt zu konfigurieren (Parameter wie size, type, stride und pointer/offset in Bytes).
- Stelle sicher, dass der Benutzer Vertex- und Fragment-Shader in GLSL schreiben und Daten über in/out-Qualifizierer übergeben kann.
- Erzwinge die korrekte Definition von Zeichenaufrufen wie glDrawArrays mit Startindex und Anzahl der Attribute.
- Stelle sicher, dass der Benutzer die Orientierung von Dreiecken (GL_CCW vs. GL_CW) versteht und vorhersagen kann, ob ein Dreieck durch Backface-Culling gefiltert wird.


## 💡 Konzepte & Definitionen

### Vertex Buffer Object (VBO)

**Definition**:
Ein Speicherpuffer im Grafikspeicher (GPU) zur Speicherung von Vertex-Attributdaten (z. B. Positionen, Farben, Normalen, Texturkoordinaten). Wird über glGenBuffers erzeugt und an das Target GL_ARRAY_BUFFER gebunden.

**Beispiel-Code**:
```java
GLuint VBO;
glGenBuffers(1, &VBO);
glBindBuffer(GL_ARRAY_BUFFER, VBO);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
```

### Vertex Array Object (VAO)

**Definition**:
Ein Zustandsobjekt, das alle Einstellungen für Vertex-Layouts und Pufferbindungen speichert. Es kapselt die glVertexAttribPointer-Konfigurationen und die Aktivierung von Attributindizes, wodurch das Umschalten zwischen verschiedenen Modellen mit einem einzigen Aufruf möglich wird.

**Beispiel-Code**:
```java
GLuint VAO;
glGenVertexArrays(1, &VAO);
glBindVertexArray(VAO);
// Danach glVertexAttribPointer-Aufrufe tätigen...
```

### glVertexAttribPointer

**Definition**:
Spezifiziert das Format der Vertex-Attribute im gebundenen VBO. Parameter:
1. index: layout-Location im Shader
2. size: Anzahl der Komponenten (z. B. 2 für 2D-Punkt, 3 für RGB-Farbe)
3. type: Datentyp (meist GL_FLOAT)
4. normalized: Sollen Werte normalisiert werden (GL_FALSE)
5. stride: Byte-Abstand zwischen aufeinanderfolgenden Attributen
6. pointer: Offset des ersten Werts im Puffer.

**Beispiel-Code**:
```java
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)(3 * sizeof(float)));
glEnableVertexAttribArray(1);
```

### GLSL (OpenGL Shading Language)

**Definition**:
Die Programmiersprache für OpenGL-Shader. Läuft direkt auf der GPU. Variablen werden mittels 'in' (Eingabe) und 'out' (Ausgabe) deklariert. Der Vertex-Shader transformiert Vertices und schreibt in 'gl_Position'. Der Fragment-Shader schreibt die Pixelfarbe in ein definiertes Ausgabe-Objekt (z. B. 'FragColor'). Unterstützt Swizzling (z. B. 'color.rgb' oder 'pos.xy'). Keine Rekursion.

**Beispiel-Code**:
```java
#version 330 core
layout (location = 0) in vec3 pos;
layout (location = 1) in vec3 color;
out vec3 out_color;
void main() {
  out_color = color;
  gl_Position = vec4(pos, 1.0);
}
```

### glDrawArrays

**Definition**:
Rendert geometrische Primitive aus dem aktiven Vertex-Array-Zustand. Parameter:
1. mode: Primitiv-Typ (z.B. GL_TRIANGLES, GL_LINES)
2. first: Startindex im Array
3. count: Anzahl der zu zeichnenden Vertices (nicht Dreiecke; z.B. 3 Vertices pro Dreieck).

**Beispiel-Code**:
```java
glDrawArrays(GL_TRIANGLES, 0, 9); // Zeichnet die ersten drei Dreiecke (9 Eckpunkte)
```

### Backface-Culling

**Definition**:
Zustand zur Ausblendung von Dreiecken, die der Kamera abgewandt sind. Wird mit glEnable(GL_CULL_FACE) aktiviert. Die Eckenreihenfolge der projizierten Dreiecke im 2D-Bildraum bestimmt, ob sie gegen den Uhrzeigersinn (GL_CCW) oder im Uhrzeigersinn (GL_CW) orientiert sind. Mittels glFrontFace und glCullFace wird konfiguriert, welche Seiten verworfen werden.

**Beispiel-Code**:
```java
glEnable(GL_CULL_FACE);
glFrontFace(GL_CCW); // Gegenuhrzeigersinn ist Vorderseite
glCullFace(GL_BACK);   // Rückseiten verwerfen
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Ein Vertexbuffer im Grafikspeicher besteht aus aufeinanderfo...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_4, klausur_ss_2024, klausur_ws_2024_2025, opengl, layout`)


#### Aufgabenstellung:
Ein Vertexbuffer im Grafikspeicher besteht aus aufeinanderfolgenden Vertex-Daten für ein 3D-Modell mit RGB-Farben:
x1|y1|z1|r1|g1|b1|x2|y2|z2|r2|g2|b2|...
Geben Sie die OpenGL-Befehle für glVertexAttribPointer() an, die:
1) Den Vertex-Shader-Attribut-Index 0 auf die 3D-Positionen (float) verweisen.
2) Den Vertex-Shader-Attribut-Index 1 auf die RGB-Farbwerte (float) verweisen.


#### Musterlösung:
1) Für die Positionen:
glVertexAttribPointer(
  0,                  // layout-location-id im Shader
  3,                  // Anzahl der floats pro Position (x, y, z)
  GL_FLOAT,           // Datentyp
  GL_FALSE,           // Keine Normalisierung
  6 * sizeof(float),  // Stride (Byte-Schritt zum nächsten Vertex: 3 Position + 3 Farbe = 6 floats)
  (void*)0            // Offset (startet am Puffer-Anfang)
);
glEnableVertexAttribArray(0);

2) Für die Farben:
glVertexAttribPointer(
  1,                  // layout-location-id im Shader
  3,                  // Anzahl der floats pro RGB-Farbe (r, g, b)
  GL_FLOAT,           // Datentyp
  GL_FALSE,           // Keine Normalisierung
  6 * sizeof(float),  // Stride (Byte-Schritt zum nächsten Vertex: 6 floats)
  (void*)(3 * sizeof(float)) // Offset (startet nach den ersten 3 floats der Position)
);
glEnableVertexAttribArray(1);


#### Typische Stolpersteine / Fehlerquellen:
Falscher Stride-Wert angegeben (z. B. 3 * sizeof(float) statt 6 * sizeof(float) oder 0). Falscher Offset (z. B. 3 statt 3 * sizeof(float)). Vergessen, den Funktionsaufruf auf void* zu casten.


---

### Aufgabe 2: Ein VAO ist aktiv. Wir möchten 3 Dreiecke zeichnen, wobei da...

- **Klausurrelevant**: Ja (Tags: `klausur_ss_2024, klausur_ws_24_25, opengl, draw`)


#### Aufgabenstellung:
Ein VAO ist aktiv. Wir möchten 3 Dreiecke zeichnen, wobei das allererste Vertex im Buffer übersprungen werden soll (das erste Dreieck soll also die Vertices mit Indizes 1, 2, 3 nutzen). Geben Sie den passenden glDrawArrays()-Zeichenbefehl an.


#### Musterlösung:
Da wir Dreiecke zeichnen möchten, verwenden wir als Modus GL_TRIANGLES. Da das erste Vertex übersprungen wird, ist der Start-Offset (first) gleich 1. Wir möchten 3 Dreiecke zeichnen, was bei 3 Vertices pro Dreieck insgesamt 3 * 3 = 9 Vertices entspricht (count = 9).

Aufruf:
glDrawArrays(GL_TRIANGLES, 1, 9);


#### Typische Stolpersteine / Fehlerquellen:
 count-Parameter als Anzahl der Dreiecke (3) statt Anzahl der Vertices (9) angegeben. Falscher Startindex (0 statt 1).


---

### Aufgabe 3: Backface-Culling ist mit folgenden Parametern aktiv:

- **Klausurrelevant**: Ja (Tags: `übungsblatt_4, culling, clipping, sichtbarkeit`)


#### Aufgabenstellung:
Backface-Culling ist mit folgenden Parametern aktiv:
glFrontFace(GL_CCW);
glCullFace(GL_BACK);
Gegeben sind die 2D-Bildschirmkoordinaten dreier gezeichneter Dreiecke:
Dreieck 1: A(-1, 0), B(-0.5, 1), C(0, 0)
Dreieck 2: A(1, -1), B(0.5, 0), C(0, -1)
Dreieck 3: A(2, 0), B(1.5, 1), C(1, 0)
Welche Dreiecke sind schlussendlich sichtbar?


#### Musterlösung:
Wir bestimmen die Orientierung der Dreieckspunkte im 2D-Raum (mittels Kreuzprodukt der Kanten bzw. 2D-Determinante):

1) Dreieck 1 (A -> B -> C):
Kante AB = B - A = (0.5, 1)
Kante AC = C - A = (1, 0)
Determinante det(AB|AC) = 0.5*0 - 1*1 = -1.
Da die Determinante negativ ist, sind die Punkte im Uhrzeigersinn (CW) orientiert. Wegen glCullFace(GL_BACK) und glFrontFace(GL_CCW) ist CW eine Rückseite. Dreieck 1 wird verworfen (nicht sichtbar).

2) Dreieck 2 (A -> B -> C):
Kante AB = B - A = (-0.5, 1)
Kante AC = C - A = (-1, 0)
Determinante det(AB|AC) = -0.5*0 - 1*(-1) = 1.
Da die Determinante positiv ist, sind die Punkte gegen den Uhrzeigersinn (CCW) orientiert. CCW ist die Vorderseite. Dreieck 2 ist sichtbar.

3) Dreieck 3 (A -> B -> C):
Kante AB = B - A = (-0.5, 1)
Kante AC = C - A = (-1, 0)
Determinante det(AB|AC) = 1 (CCW - Vorderseite).
Jedoch liegen die x-Koordinaten der Punkte (2, 1.5, 1) außerhalb des kanonischen Sichtvolumens [-1, 1]^3. Daher wird Dreieck 3 beim Clipping vollständig abgeschnitten (nicht sichtbar).

Ergebnis:
Nur Dreieck 2 ist sichtbar.


#### Typische Stolpersteine / Fehlerquellen:
Vergessen zu prüfen, ob Dreiecke außerhalb der kanonischen Sichtbox [-1, 1]^3 liegen (Clipping). Rechenfehler bei der Bestimmung der Drehrichtung.




---

# Kapitel 8: Texturabbildungen

## 📖 Guidelines

### Das Problem
Die Zuweisung einzelner Farben zu geometrischen Primitiven führt zu einer unrealistischen, künstlichen Optik. Um detailreiche Oberflächenstrukturen effizient darzustellen, müssen 2D-Bilddateien auf 3D-Geometrien abgebildet werden. Ungenauigkeiten bei der Projektion, Filterung oder Kantenübergängen führen zu Verzerrungen, Aliasing oder unnatürlichen Nahtstellen.

### Die Lösung
Definition eines normalisierten 2D-Texturraums mit Koordinaten u und v im Bereich [0, 1]2. Zuordnung von Oberflächenpunkten zu Texturkoordinaten über Projektionsfunktionen Phi (planar, perspektivisch, zylindrisch, sphärisch) oder explizite Vertex-Zuweisung. Laden von Texturen über Bibliotheken wie SOIL, Bindung an Textur-Targets, und Definition von Filterungsmethoden (GL_NEAREST, GL_LINEAR für Minification/Magnification) und Wrapping-Modi (GL_REPEAT, GL_CLAMP_TO_EDGE). Verwendung von Bump Mapping zur Simulation von Oberflächenunebenheiten durch Modifikation der Normalenvektoren.

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer den Unterschied zwischen planarer, perspektivischer, zylindrischer und sphärischer Texturprojektion erklären kann.
- Leite den Benutzer an, die Formel zur Umrechnung von u-v-Koordinaten in diskrete Pixel-Texel-Indizes anzuwenden.
- Stelle sicher, dass der Benutzer Texturen in OpenGL laden, binden und Parameter für Filterung (Nearest vs. Linear) sowie Wrapping (Repeat, Clamp to edge) konfigurieren kann.
- Erkläre dem Benutzer, wie Texturkoordinaten in GLSL-Shadern über sampler2D und die texture()-Funktion ausgelesen werden.
- Leite den Benutzer an, den Unterschied zwischen Bump-Mapping (Normalenmodifikation, flache Silhouette) und Displacement-Mapping (echte Geometrieverschiebung) zu verstehen.


## 💡 Konzepte & Definitionen

### Texturraum & u-v-Koordinaten

**Definition**:
Ein normalisierter zweidimensionaler Koordinatenraum für Texturbilder. Die Achsen heißen u (horizontal) und v (vertikal), die Koordinatenwerte liegen im Intervall [0, 1]^2. Unabhängig von der tatsächlichen Pixelauflösung der Bilddatei.

### Texel-Mapping-Formel

**Definition**:
Umrechnung der kontinuierlichen u-v-Koordinaten in ganzzahlige Pixelkoordinaten (Texel-Indizes i, j) der Textur mit Breite width und Höhe height: i = round(u * width - 0.5), j = round(v * height - 0.5).

### Kugel- und Zylinderprojektion

**Definition**:
Zylindrische Projektion wickelt die Textur um die z-Achse: u = 1/(2*PI) * (PI + atan2(y, x)), v = 0.5 * (z + 1) (für z in [-1, 1]). Sphärische Projektion bildet Koordinaten auf eine Kugel mit Radius 1 ab: u = 1/(2*PI) * (PI + atan2(y, x)), v = 1/PI * (PI - acos(z / |p|)) (wobei |p| die Länge des 3D-Positionsvektors ist).

### OpenGL Texturfilterung & Wrapping

**Definition**:
Wrapping bestimmt, wie Texturen außerhalb des Bereichs [0, 1] wiederholt oder abgeschnitten werden (GL_TEXTURE_WRAP_S, GL_TEXTURE_WRAP_T: GL_REPEAT, GL_CLAMP_TO_EDGE). Filtering bestimmt das Verhalten bei Skalierung (GL_TEXTURE_MIN_FILTER, GL_TEXTURE_MAG_FILTER): GL_NEAREST (nächstgelegener Texel, pixelig) und GL_LINEAR (bilineare Interpolation, weich).

**Beispiel-Code**:
```java
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
```

### GLSL Textur-Shader

**Definition**:
Um Texturdaten im Fragment-Shader zu nutzen, wird eine Variable uniform sampler2D texturedata deklariert. Über die Funktion texture(texturedata, texCoord) wird die RGB(A)-Farbe an der Stelle texCoord (vec2) ausgelesen.

**Beispiel-Code**:
```java
#version 330 core
in vec2 texturecoordout;
out vec4 FragColor;
uniform sampler2D texturedata;
void main() {
  FragColor = texture(texturedata, texturecoordout);
}
```

### Bump Mapping vs. Displacement Mapping

**Definition**:
Bump Mapping manipuliert beim Rendern die Normalenvektoren auf Basis einer Textur (Normal/Height Map), um eine unebene Struktur vorzutäuschen. Die Silhouette des Objekts bleibt vollkommen glatt. Displacement Mapping verschiebt die tatsächlichen Vertex-Koordinaten im Vertex- oder Tessellation-Shader. Dies verändert die echte Geometrie und somit auch die Silhouette.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben sei ein Würfel. Eine Textur enthält sechs gleich gro...

- **Klausurrelevant**: Ja (Tags: `übungsblatt_4, textur, koordinaten, mapping`)


#### Aufgabenstellung:
Gegeben sei ein Würfel. Eine Textur enthält sechs gleich große quadratische Segmente (zwei Reihen, drei Spalten). Wir wollen die vordere Würfelseite (aufgespannt durch die Vertices A, B, D, C) so texturieren, dass sie genau das Segment in der oberen linken Ecke der Textur anzeigt. Geben Sie die u-v-Parameter für die vier Ecken A (unten-links), B (unten-rechts), D (oben-rechts) und C (oben-links) des Quadrats an.


#### Musterlösung:
Da die Textur in 3 Spalten (u-Richtung) und 2 Reihen (v-Richtung) unterteilt ist, liegen die Grenzen der Quadrate bei:
- u-Achse: 0.0, 1/3 (0.333), 2/3 (0.667), 1.0
- v-Achse: 0.0, 0.5, 1.0 (wobei 0.0 unten und 1.0 oben ist).

Das obere linke Segment befindet sich:
- horizontal im Bereich u in [0.0, 0.333]
- vertikal im Bereich v in [0.5, 1.0].

Die Zuordnung der Ecken ergibt:
- A (unten-links): (0.0, 0.5)
- B (unten-rechts): (0.333, 0.5)
- D (oben-rechts): (0.333, 1.0)
- C (oben-links): (0.0, 1.0)


#### Typische Stolpersteine / Fehlerquellen:
Vertauschen der u- und v-Achsen. Falsche Zuordnung der y/v-Orientierung (z.B. Annahme, das obere Segment liege bei v in [0, 0.5] statt [0.5, 1.0]).


---

### Aufgabe 2: Schreiben Sie den Aufruf von glVertexAttribPointer, um zweid...

- **Klausurrelevant**: Ja (Tags: `klausur_ws_2024_2025, opengl, texture, pointer`)


#### Aufgabenstellung:
Schreiben Sie den Aufruf von glVertexAttribPointer, um zweidimensionale Texturkoordinaten (u, v) an den Shader mit der layout-location 2 zu übergeben. Die Texturkoordinaten stehen in einem VBO direkt hinter den float-Werten für Position (3 floats) und RGB-Farbe (3 floats) jedes Vertices. Der Puffer enthält also: x|y|z|r|g|b|u|v|...


#### Musterlösung:
Ein vollständiger Vertex-Eintrag besteht aus 3 Position + 3 Farbe + 2 Textur = 8 float-Werte. Der Stride beträgt daher 8 * sizeof(float).
Die Texturkoordinaten beginnen nach den ersten 6 float-Werten (x, y, z, r, g, b). Der Offset beträgt demnach 6 * sizeof(float).

Aufruf:
glVertexAttribPointer(
  2,                  // index (layout location)
  2,                  // size (u, v)
  GL_FLOAT,           // type
  GL_FALSE,           // normalized
  8 * sizeof(float),  // stride
  (void*)(6 * sizeof(float)) // offset
);
glEnableVertexAttribArray(2);


#### Typische Stolpersteine / Fehlerquellen:
Falscher Stride-Wert (z. B. 2 * sizeof(float) oder 6 * sizeof(float)). Falscher Offset (z. B. 0 oder 3 * sizeof(float)).




---

# Kapitel 9: Schattierung von Oberflächen

## 📖 Guidelines

### Das Problem
Um räumliche Formen, Krümmungen und Materialeigenschaften von 3D-Objekten visuell erfassbar zu machen, muss das Zusammenwirken von Licht und Oberfläche simuliert werden. Eine vereinfachte Berechnung führt entweder zu unnatürlichen Facetteneffekten oder lässt Glanzlichter und realistische Farbverläufe vermissen.

### Die Lösung
Anwendung verschiedener Schattierungsverfahren. Flat-Shading berechnet eine Farbe pro Face (Facetteneffekt). Lambert-Shading simuliert matte Oberflächen. Gouraud-Shading berechnet Beleuchtungen an den Eckpunkten (Vertex-Shader) und interpoliert die Farben. Phong-Shading interpoliert die Normalenvektoren und berechnet die Beleuchtung pro Pixel (Fragment-Shader). Das Phong-Beleuchtungsmodell kombiniert diffusen und spiegelnden Glanz (Specular Highlight via Phong-Exponent p). Gooch-Shading (Artistic Shading) interpoliert zwischen warmen (orange) und kalten (blau) Farben zur technischen Illustration.

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer den Unterschied zwischen Flat-, Gouraud- und Phong-Shading erklären und deren Rechenaufwand vergleichen kann.
- Leite den Benutzer an, das Phong-Beleuchtungsmodell (c = k_s * max(0, r · e)^p) anzuwenden.
- Stelle sicher, dass der Benutzer den Nutzen des Phong-Exponenten p zur Steuerung der Glanzlichtgröße erklären kann.
- Leite den Benutzer an, Gooch-Shading (kalt-zu-warm Illustration) mathematisch über die Linearkombination c = k_w * c_w + (1 - k_w) * c_c mit k_w = (1 + n · l) / 2 zu berechnen.


## 💡 Konzepte & Definitionen

### Flat Shading

**Definition**:
Einfachstes Schattierungsverfahren. Berechnet einen einzigen Farbwert pro Polygon (meist basierend auf der Flächennormale und dem Mittelpunkt). Das gesamte Polygon wird einfarbig gezeichnet. Führt zu sichtbaren Polygonkanten (Fakteneffekt/Mach-Bänder).

### Gouraud Shading

**Definition**:
Schattierungsmethode, bei der die Beleuchtungsberechnung an den Eckpunkten (Vertices) des Polygons im Vertex-Shader durchgeführt wird. Die resultierenden Eckpunktfarben werden während der Rasterisierung linear über die Fläche interpoliert. Vorteil: Schnelle Berechnung. Nachteil: Glanzlichter (specular highlights) gehen verloren, wenn sie in der Mitte des Polygons liegen, oder werden unnatürlich verzerrt.

### Phong Shading

**Definition**:
Schattierungsmethode, bei der die Normalenvektoren der Eckpunkte linear über die Fläche interpoliert werden. Im Fragment-Shader wird für jedes Fragment der Normalenvektor neu normalisiert und die vollständige Beleuchtungsberechnung durchgeführt. Vorteil: Sehr realistische Verläufe und exakte Glanzlichter. Nachteil: Deutlich höherer Rechenaufwand pro Pixel statt pro Vertex.

### Phong-Reflexionsmodell

**Definition**:
Ein lokales Beleuchtungsmodell. Die Pixelfarbe berechnet sich aus ambientem, diffusem (Lambert) und spiegelndem (specular) Anteil: c = k_a * I_a + k_d * I_d * max(0, n · l) + k_s * I_s * max(0, r · e)^p. Hierbei ist r der Reflexionsrichtungsvektor des Lichts, e der Blickrichtungsvektor (beide normalisiert) und p der Phong-Exponent (Steilheit des Glanzlichts).

### Gooch Shading (Kalt-zu-Warm)

**Definition**:
Ein künstlerisches Schattierungsverfahren (Non-Photorealistic Rendering) für technische Zeichnungen. Anstatt abgewandte Seiten schwarz zu zeichnen, wird zwischen einer kalten Farbe c_c (z. B. Blau) und einer warmen Farbe c_w (z. B. Orange) interpoliert, basierend auf dem Kosinus des Winkels zwischen Normalenvektor n und Lichtrichtung l: k_w = (1 + n · l) / 2. Die Pixelfarbe ergibt sich als c = k_w * c_w + (1 - k_w) * c_c.

**Beispiel-Code**:
```java
float kw = (1.0 + dot(normal, lightdir)) / 2.0;
vec3 color = kw * warmColor + (1.0 - kw) * coolColor;
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Erklären Sie den Unterschied zwischen Gouraud-Shading und Ph...

- **Klausurrelevant**: Ja (Tags: `klausur_ws_2023_2024, shading, gouraud, phong`)


#### Aufgabenstellung:
Erklären Sie den Unterschied zwischen Gouraud-Shading und Phong-Shading im Hinblick auf Berechnungsort und die Darstellung von spiegelnden Highlights (Specular Highlights).


#### Musterlösung:
1. Gouraud-Shading:
- Berechnungsort: Die Beleuchtungsrechnung findet pro Vertex im Vertex-Shader statt.
- Interpolation: Die resultierenden Farben der Vertices werden linear über das Dreieck interpoliert.
- Specular Highlights: Werden schlecht dargestellt. Liegt ein Glanzpunkt in der Mitte eines Dreiecks (und trifft keine der Ecken), wird er komplett unterschlagen. Trifft er eine Ecke, wird er unnatürlich über das gesamte Dreieck verschmiert.

2. Phong-Shading:
- Berechnungsort: Die Beleuchtungsrechnung findet pro Fragment (Pixel) im Fragment-Shader statt.
- Interpolation: Die Normalenvektoren der Vertices werden über das Dreieck interpoliert. Im Fragment-Shader muss der interpolierte Normalenvektor vor der Beleuchtungsrechnung neu normiert werden.
- Specular Highlights: Werden mathematisch exakt an jeder Stelle des Dreiecks dargestellt, da für jedes Pixel die exakte Normale und Blickrichtung ausgewertet werden.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung des Phong-Schattierungsverfahrens (Interpolation der Normalen) mit dem Phong-Reflexionsmodell (lokale Beleuchtungsformel mit Glanzlicht).


---

### Aufgabe 2: Gegeben sei ein Punkt mit normalisierter Normale n und Licht...

- **Klausurrelevant**: Ja (Tags: `folien_beispiel, gooch, shading`)


#### Aufgabenstellung:
Gegeben sei ein Punkt mit normalisierter Normale n und Lichtrichtung l. Die kalte Farbe ist Blau c_c = (0, 0, 1), die warme Farbe ist Gelb c_w = (1, 1, 0). Der Winkel zwischen n und l beträgt 60 Grad. Berechnen Sie die resultierende Farbe nach dem Gooch-Shading-Modell.


#### Musterlösung:
1. Berechnung des Gewichts k_w:
Da der Winkel zwischen n und l gleich 60° ist, gilt:
dot(n, l) = cos(60°) = 0.5.
Formel für k_w:
k_w = (1 + dot(n, l)) / 2 = (1 + 0.5) / 2 = 1.5 / 2 = 0.75.

2. Berechnung der Endfarbe c:
c = k_w * c_w + (1 - k_w) * c_c
c = 0.75 * (1, 1, 0) + (1 - 0.75) * (0, 0, 1)
c = 0.75 * (1, 1, 0) + 0.25 * (0, 0, 1)
c = (0.75, 0.75, 0) + (0, 0, 0.25)
c = (0.75, 0.75, 0.25).

Die resultierende RGB-Farbe ist (0.75, 0.75, 0.25).


#### Typische Stolpersteine / Fehlerquellen:
Verwendung der falschen Gooch-Formel (z.B. Lambert-Term max(0, n·l) anstelle von (1 + n·l)/2). Rechenfehler bei den Vektorkomponenten.
