<!-- /TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 1. Szenenrepräsentation](#folien-1-szenenrepräsentation)
	- [1.1 Motivation](#11-motivation)
		- [Aufgabe](#aufgabe)
		- [Grundlage](#grundlage)
		- [Anforderungen](#anforderungen)
	- [1.2 Euklidischer Raum 欧几里得](#12-euklidischer-raum-欧几里得)
		- [1.2.1 Punkte](#121-punkte)
		- [1.2.2 Vektoren](#122-vektoren)
		- [1.2.3 Skalarprodukt 点乘 (标量)](#123-skalarprodukt-点乘-标量)
		- [1.2.4 Kreuzprodukt 叉乘](#124-kreuzprodukt-叉乘)
		- [1.2.5 Spatprodukt 三乘积](#125-spatprodukt-三乘积)
	- [1.3 Homogene Koordinaten 齐次坐标（投影坐标）](#13-homogene-koordinaten-齐次坐标投影坐标)
		- [1.3.1 Punkte in der 2D Ebene](#131-punkte-in-der-2d-ebene)
		- [1.3.2 Linien in der 2D Ebene](#132-linien-in-der-2d-ebene)
		- [1.3.3 Dualität 二元性](#133-dualität-二元性)
		- [1.3.4 Kurven 2. Ordnung](#134-kurven-2-ordnung)
		- [1.3.5 3D Gerade & Ebene](#135-3d-gerade-ebene)
		- [1.3.6 Anwendungsbeispiel -- 3D Rekonstruktion](#136-anwendungsbeispiel-3d-rekonstruktion)
	- [1.4 Starrkörperbewegung](#14-starrkörperbewegung)
		- [1.4.1 Motivation](#141-motivation)
		- [1.4.2 Definition](#142-definition)
		- [1.4.3 Repräsentation](#143-repräsentation)
		- [1.4.4 Rotation](#144-rotation)
			- [1.4.4.1 Rotationsmatrix](#1441-rotationsmatrix)
			- [1.4.4.2 Rotationsachse](#1442-rotationsachse)
			- [1.4.4.3 Eulerwinkel](#1443-eulerwinkel)
			- [1.4.4.4 Quaternionen](#1444-quaternionen)
		- [1.4.5 Homogene Koordinaten](#145-homogene-koordinaten)
		- [1.4.6 Drall](#146-drall)

<!-- /TOC -->

# Folien 1. Szenenrepräsentation

---
## 1.1 Motivation

### Aufgabe
**Vermessung, Rekonstruktion und Analyse** der 3D Welt mittels 2D Aufnahmen einer Kamera
- Position und Bewegung von Objekten
- Position und Bewegung der Kamera
- Räumliche Geometrie von Objekten
- Objektzustände und Objektrelationen

### Grundlage
Beschreibung der **geometrischen Beziehungen** der 3D Welt und der Kamera **durch** Koordinatensysteme, Punkte und Vektoren.

### Anforderungen
- Genauigkeit
- Komplexität

---
## 1.2 Euklidischer Raum 欧几里得

### 1.2.1 Punkte
Kartesisches (orthogonales) Koordinatensysteme:

![Alt text](Figures\Folien_1_1.png)

### 1.2.2 Vektoren
Ein Vektor ist definiert durch ein Punktepaar (p,q)

![Alt text](Figures\Folien_1_2.png)

**Punkte und Vektoren** im Raum in *Form von Koordinaten* zu beschreiben.

Ermöglicht die **Berechnung** von *Distanzen, Winkel, Längen (Kurven), Volumen (Regionen)*. Dazu benötigt man eine *Metrik* 度量 .

### 1.2.3 Skalarprodukt 点乘 (标量)

Skalarprodukt zwischen zwei Vektoren

![Alt text](Figures\Folien_1_3.png)

**Euklidische Norm** -- Länge eines Vektors

![Alt text](Figures\Folien_1_4.png)

**Winkel zwischen zwei Vektoren**

![Alt text](Figures\Folien_1_5.png)
![Alt text](Figures\Folien_1_6.png)

Falls Theta = 90, Produkt gleich wie 0

### 1.2.4 Kreuzprodukt 叉乘

![Alt text](Figures\Folien_1_7.png)
![Alt text](Figures\Folien_1_8.png)

**Schiefsymmetrisch**

![Alt text](Figures\Folien_1_9.png)

**Betrag** des Kreuzprodukts -- **Fläche** des von den Vektoren aufgespannten Parallelogramms

![Alt text](Figures\Folien_1_10.png)

### 1.2.5 Spatprodukt 三乘积

Skalar, das dem Volumen des von den drei Vektoren aufgespannten Spats entspricht.

![Alt text](Figures\Folien_1_11.png) (zyklisch vertauscht)

---
## 1.3 Homogene Koordinaten 齐次坐标（投影坐标）

### 1.3.1 Punkte in der 2D Ebene
- 2D Punkte

![Alt text](Figures\Folien_1_12.png)

![Description](Figures\Folien_1_14.png)

- 2D Vektoren

![Alt text](Figures\Folien_1_13.png)

**Der Ursprung** [0,0,0] ist in homogenen Koordinaten *nicht definiert*.

### 1.3.2 Linien in der 2D Ebene

Veranschaulichung der Darstellung einer Geraden in der Ebene (in grün) mit homogenen Koordinaten (in blau).

![Alt text](Figures\Folien_1_19.png)

Zweidimensionale **Geragengleichung** in homogenen Koordinaten mit x3 = 1

![Alt text](Figures\Folien_1_15.png)

Die **Geradengleichung** hat *drei Parameter I*, aber nur *zwei Freiheitsgrade*
![Alt text](Figures\Folien_1_20.png)

Die **Parameter** sind durch zwei unterschiedliche Punkte *auf der Geraden* gegeben
![Alt text](Figures\Folien_1_16.png)

Der **Schnittpunkt** zweier Geraden ergibt sich zu
![Alt text](Figures\Folien_1_17.png)

**Parallele Geraden** schneiden sich im Unendlichen
![Alt text](Figures\Folien_1_18.png)

### 1.3.3 Dualität 二元性

Dualitätsprinzip bei Punkten und Linien in der Ebene in homogenen Koordinaten:

- Punkt und Gerade
- Verbindungsgerade zweier Punkte & Schnittpunkt zweier Geraden

können in folgenden Beziehungen vertauscht werden :

- ![Alt text](Figures\Folien_1_21.png)
- ![Alt text](Figures\Folien_1_22.png)

### 1.3.4 Kurven 2. Ordnung

Kurven 2. Ordnung sind **Kegelschnitte** und beschreiben *Ellipsen, Parabeln, Hyperbeln und Geradenpaare in der Ebene*.

Sie ergeben sich durch Nullsetzen einer quadratischen Funktion :

![Alt text](Figures\Folien_1_23.png)

und werden *durch 5 Punkte* in allgemeiner Lage beschrieben.

In **homogenen Koordinaten** ergibt sich folgende äquivalente Gleichung :
![Alt text](Figures\Folien_1_24.png)

### 1.3.5 3D Gerade & Ebene

- Darstelung einer **Geraden** in homogenen Koordinaten :
![Alt text](Figures\Folien_1_25.png)
- Darstelung einer **Ebene** in homogenen Koordinaten :
![Alt text](Figures\Folien_1_26.png)

- **Dualität**
![Alt text](Figures\Folien_1_27.png)

- **Ebene** durch 3 Punkte definiert:
![Alt text](Figures\Folien_1_28.png)
- **Punkt** durch Schnitt dreier Ebenen definiert:
![Alt text](Figures\Folien_1_29.png)

### 1.3.6 Anwendungsbeispiel -- 3D Rekonstruktion

Zwei Lösungsmöglichkeiten:        
- **Einpassen des Modells** in eine gemessene Punktewolke über eine Ausgleichungsrechnung 通过补偿计算，将模型拟合到测量点云中
- Gleichzeitiges **Schätzen** der *Punktewolke und der Modellparameter* 同时估计点云和模型参数

---
## 1.4 Starrkörperbewegung

### 1.4.1 Motivation
- Position und Bewegung einer Kamera
- Position und Bewegung von Objekten
- Position und Bewegung von Objektteilen

### 1.4.2 Definition
![Alt text](Figures\Folien_1_32.png)
- Die **Bewegung eines starren Körpers** erhält zu jedem Zeitpunkt den Abstand zwischen jedem beliebigen Punktepaar (p,q) auf dem Körper.
- **Bewegung des Körpers** vollständig **durch** die *Trajektorie eines Punktes auf dem Körper* und *einem Körperbezogenen Koordinatensystem* gegeben.

![Alt text](Figures\Folien_1_30.png) mit ![Alt text](Figures\Folien_1_31.png)

- **Starrkörperbewegung** -- die Norm und das Kreuzprodukt beliebiger Vektoren auf dem Körper erhalten bleibt:

![Alt text](Figures\Folien_1_33.png)

- Das bedeutet, die **Abstände, Winkel, Orientierungen und Volumen** *bleiben erhalten*.

### 1.4.3 Repräsentation
- Die Beziehung **g=(R,T)** zwischen den *Koordinaten des körperbezogenen Koordinatensystems eines starren Körpers* und den *Weltkoordinatensystem* wird vollständig durch eine **Translation T** und eine **Rotation R** beschrieben.
![Alt text](Figures\Folien_1_34.png)

- Die Geschwindigkeit der Körper-Koordinaten ist über die **Translationsgeschwindigkeit v** und die **Winkelgeschwindigkeit w** gegeben
![Alt text](Figures\Folien_1_35.png)

### 1.4.4 Rotation

#### 1.4.4.1 Rotationsmatrix


#### 1.4.4.2 Rotationsachse

#### 1.4.4.3 Eulerwinkel

#### 1.4.4.4 Quaternionen

### 1.4.5 Homogene Koordinaten

### 1.4.6 Drall
