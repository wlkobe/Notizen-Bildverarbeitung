<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 5 Bildrepräsentation, vergleich und Digitalisierung](#folien-5-bildrepräsentation-vergleich-und-digitalisierung)
	- [5.1 Bildanalyse](#51-bildanalyse)
		- [5.1.1 Motivation der Lehrveranstaltung](#511-motivation-der-lehrveranstaltung)
		- [5.1.2 Beispiel: Deep Learning Architektur](#512-beispiel-deep-learning-architektur)
	- [5.2 Bildrepräsentation](#52-bildrepräsentation)
		- [5.2.1 Digitale Bilder im Ortsraum](#521-digitale-bilder-im-ortsraum)
			- [5.2.1.1 Art der Information](#5211-art-der-information)
			- [5.2.1.2 Pixel](#5212-pixel)
			- [5.2.1.3 Pixel und Voxel](#5213-pixel-und-voxel)
			- [5.2.1.4 Auflösung](#5214-auflösung)
			- [5.2.1.5 Quantisierung](#5215-quantisierung)
			- [5.2.1.6 Speicherbedarf](#5216-speicherbedarf)
			- [5.2.1.7 Nachbarschaftsoperationen](#5217-nachbarschaftsoperationen)
			- [5.2.1.8 Distanzen](#5218-distanzen)
		- [5.2.2 Bilder als Vektoren](#522-bilder-als-vektoren)
		- [5.2.3 Zerlegung und Rekonstruktion](#523-zerlegung-und-rekonstruktion)
			- [5.2.3.1 Unüberwachtes Lernen](#5231-unüberwachtes-lernen)
			- [Basisbilder](#basisbilder)
		- [5.2.4 Wellenzahlraum](#524-wellenzahlraum)
			- [5.2.4.1 Periodische Basisbilder im Ortsraum](#5241-periodische-basisbilder-im-ortsraum)
			- [5.2.4.2 2D Fouriertransformation](#5242-2d-fouriertransformation)
			- [5.2.4.3 2D Diskrete Fouriertransformation](#5243-2d-diskrete-fouriertransformation)
			- [5.2.4.4 Komplexe Basisbilder](#5244-komplexe-basisbilder)
		- [5.2.5 Fouriertransformation](#525-fouriertransformation)
			- [5.2.5.1 Beispiel](#5251-beispiel)
			- [5.2.5.2 Separabilität](#5252-separabilität)
			- [5.2.5.3 Faltungstheorem](#5253-faltungstheorem)
	- [5.3 2D Signalverarbeitung](#53-2d-signalverarbeitung)
		- [5.3.1 Nachbarschaftsoperationen](#531-nachbarschaftsoperationen)
			- [5.3.1.1 Bedeutung](#5311-bedeutung)
			- [5.3.1.2 Definition](#5312-definition)
			- [5.3.1.3 Diskrete Faltung](#5313-diskrete-faltung)
			- [5.3.1.4 Faltung & Korrelation](#5314-faltung-korrelation)
				- [5.3.1.4.1 Randbehandlung](#53141-randbehandlung)
				- [5.3.1.4.2 Effektive Berechnung](#53142-effektive-berechnung)
					- [5.3.1.4.2.1 IPP Vergleich](#531421-ipp-vergleich)
			- [5.3.1.5 Faltung](#5315-faltung)
				- [5.3.1.5.1 Punktantwort](#53151-punktantwort)
				- [5.3.1.5.2 Transferfunktion](#53152-transferfunktion)
	- [5.4 Digitale Kamera](#54-digitale-kamera)
		- [5.4.1 Digitalisierung](#541-digitalisierung)
			- [5.4.1.1 Mathematische Beschreibung](#5411-mathematische-beschreibung)
			- [5.4.1.2 Intensitätsmittelung](#5412-intensitätsmittelung)
			- [5.4.1.3 Abtastung](#5413-abtastung)
			- [5.4.1.4 Abtasttheorem](#5414-abtasttheorem)
			- [5.4.1.5 Ortsbegrenzung](#5415-ortsbegrenzung)
			- [5.4.1.6 Perfekte Rekonstruktion](#5416-perfekte-rekonstruktion)
		- [5.4.2 Aliasing](#542-aliasing)
			- [5.4.2.1 Moire-Effekt](#5421-moire-effekt)

<!-- /TOC -->

# Folien 5 Bildrepräsentation, vergleich und Digitalisierung

---

## 5.1 Bildanalyse

**Bildanalyse** ist ein *spezieller Teilbereich der Mustererkennung* und damit Teilgebiet der künstlichen Intelligenz
图像分析是模式识别的一个特殊部分，因此也是人工智能的一部分

**Mustererkennung** hat seinen Ursprung in den *Ingenieurswissenschaften* und das **Maschinelle Lernen** entstand in der *Informatik*
模式识别起源于计算机科学中的工程和机器学习

Beide Forschungsfelder behandeln den gleichen Stoff mit unterschiedlichen Akzenten
两个研究领域都用不同的口音对待同一种物质

Wir fokussieren uns in dieser Veranstaltung auf die **signaltheoretischen Aspekte** zum Erzeugen von *geeigneten Repräsentationen von Bildern*.
在这种情况下，我们专注于信号理论方面，以产生适当的图像表示

![Alt text](Figures\Folien_5_1.png)
![Alt text](Figures\Folien_5_2.png)

*Repräsentationen von Bildern oder Bildausschnitten* werden in **Merkmalsvektoren**, auch **Deskriptoren** genannt, abgelegt
图像或图像部分的表示存储在特征向量中，也称为描述符

Diese **Repräsentationen** können *von Hand entworfen* werden, oder *über eine Lernarchitektur anhand von Daten* gelernt werden, wobei dann der *Entwurf der Lernarchitektur* und die *Auswahl der Lerndaten* **von Hand** ausgeführt werden muss
这些表示可以手工设计或通过学习架构从数据中学习，然后学习架构的设计和学习数据的选择必须手工完成

Beim **Lernen von Merkmalsvektoren** werden vorrangig *unüberwachte Lernmethoden* eingesetzt.
在学习特征向量时，优先考虑无监督学习方法

### 5.1.1 Motivation der Lehrveranstaltung

![Alt text](Figures\Folien_5_3.png)

- Wie wird ein **Bildverarbeitungsproblem** gelöst?
  - Mathematische Modelle für 数学模型
    - Geometrie und Physik der Welt 世界的几何和物理
    - **Zusammenhang** zwischen *Bilddaten und visuellen Zuständen* 图像数据与视觉状态之间的关系
    - **Zusammenhang** zwischen *visuellen Zuständen*. 视觉状态之间的关系

### 5.1.2 Beispiel: Deep Learning Architektur

![Alt text](Figures\Folien_5_4.png)

- Beispiel von gelernten Filtermasken zur **Merkmalsextraktion** auf unterschiedlichen Abstraktionsebenen (lokal - global)
用于在不同抽象级别（本地 - 全局）的特征提取的学习过滤器掩码的示例

- Diese **gelernten Filtermasken** besitzen viele Eigenschaften, welche von Hand entworfene Filter ebenfalls besitzen
这些学习过滤掩模具有许多属性，这些属性也具有手工设计的滤波器

- Um gelernte Filtermasken zu **bewerten**, ist auch *ein gutes Verständnis* über den Entwurf von Filtern und deren Implementierung *nötig*.
评估学习过滤器掩模需要很好地理解过滤器的设计及其实现

---

## 5.2 Bildrepräsentation

### 5.2.1 Digitale Bilder im Ortsraum

#### 5.2.1.1 Art der Information

![Alt text](Figures\Folien_5_5.png)

Bilder stellen eine flächenhafte Verteilung der Bestrahlungsstärke E eines bestimmten Ausschnittes der Umwelt in einer Ebene (x, y) dar.
图像表示平面（x，y）中环境的特定部分的辐照度E的平面分布

#### 5.2.1.2 Pixel

**Digitalisierung** ist die *Rasterung eines Bildes E(x)* mit kontinuierlichen Koordinaten x = [x, y]T auf eine zweidimensionale Bildmatrix {G = G(p)}p mit den Rasterpunkten p = [m, n]T.
数字化是将具有连续坐标x = [x，y] T的图像E（x）光栅化到具有光栅点p = [m，n] T的二维图像矩阵{G = G（p）} p上

![Alt text](Figures\Folien_5_6.png)

Einen Bildpunkt auf dem Gitter nennt man **Pixel (picture element)** mit der rechteckigen Pixelfläche ∆x×∆y
网格上的像素被称为具有矩形像素区域Δx×Δy的像素（像素）

Die **Pixelposition p = [m, n]T** wird mit einem Zahlenpaar angegeben, wobei m als Zeilenindex und n als Spaltenindex bezeichnet wird
像素位置p由一对数字表示，其中m称为行索引，n是列索引

M ist die Zeilenanzahl und N die Spaltenanzahl der Bildmatrix.
M是行数，N是图像矩阵的列数

#### 5.2.1.3 Pixel und Voxel

Jedes **Pixel** repäsentiert eine rechteckige Region, eine Elementarzelle, des Gitters
每个像素表示网格的矩形区域，基本单元格

Der dazugehörige Wert entspricht der **mittleren Bestrahlungsstärke**
相应的值对应于平均辐照度

In der Bildverarbeitung kommen auch **drei- oder höherdimensionale Signale** vor
在图像处理中，也发生三维或更高维信号
- Farbbilder (RGB-Kanalbilder)
彩色图像（RGB通道图像）
- Reihe von Schnittbildern (z.B. Tomographie)
系列截面图像（例如 : 断层扫描）
- Videosequenz von Grau- oder Farbbildern
灰度或彩色图像的视频序列

3-D Bilder bestehen aus **Voxel** (volume element), deren Wert **G(m, n, l)** den *mittleren Grauwert eines Würfelelementes* an der Stelle (x, y, z) repräsentieren.
3-D图像由体素（体积元素）组成，其值G（m，n，l）表示位置（x，y，z）处的立方体元素的平均灰度值

#### 5.2.1.4 Auflösung

Je niedriger die Abtastung, desto kleiner die Auflösung des digitalen Bildes
采样越低，数字图像的分辨率越小

**Welche räumliche (und zeitliche) Auflösung ist nötig/sinnvoll?**
哪种空间（和时间）分辨率是必要/有用的？

Die *Frage ist abhängig von der Aufgabe*:
问题取决于任务：
- **Bildbetrachtung**: Pixelgröße sollte z.B. *kleiner als die visuelle Auflösung* des menschlichen Sehsystems sein
图片评论：例如，像素尺寸应小于人类视觉系统的视觉分辨率
- **Objekterkennung**: Pixelgröße sollte z.B. *kleiner sein als die kleinsten Objekte*, die untersucht werden sollen
对象检测：例如，像素大小应小于要检查的最小对象
- **Bildbewegungen**: Die **Zeitdiskretisierung** muss so fein sein, das z.B. alle zu analysierenden Pixel trotz *Pixelverschiebungen* zwischen zwei aufeinanderfolgenden Bildern *innerhalb einer ROI* (Region of Interest) verbleiben.
图像移动：时间离散化必须非常精细，例如，尽管两个连续图像之间的像素移位，但是要分析的所有像素仍保持在ROI（感兴趣区域）内

#### 5.2.1.5 Quantisierung

Der kontinuierliche Wertebereich der gemessenen Bestrahlungsstärke wird auf eine begrenzte Anzahl Q (Quantisierungsstufen) diskreter Grauwerte abgebildet
测量的辐照度的连续值范围被映射到离散灰度值的有限数量Q（量化水平）

**Wieviele Quantisierungsstufen sind nötig?**
需要多少量化级别？

Diese Frage hängt wieder von der Aufgabe ab:
这个问题又取决于任务：

- Wie hoch ist der **Kontrast** in den Bildbereichen, in denen ich z.B. ein Objekt erkennen möchte
我喜欢的图像区域的对比度是多少,想要识别一个物体

- Ab wieviel **Quantisierungsstufen** nimmt der *Mensch Grauwertübergange als kontinuierlich* war?
从多少量化级别来看，人类将灰度级转换视为连续的？

- Werden **falsche Kanten** erzeugt?
是否创建错误的边缘？

#### 5.2.1.6 Speicherbedarf

**Standardmäßig** werden *Grauwertbilder* bzw ein Farbkanal mit einer *Farb-Bit-Tiefe von 8 Bit*, was 256 ganzzahligen Wertestufen entspricht, quantisiert
默认情况下，灰度级图像或颜色位深度为8位的颜色通道（对应于256个整数值级别）被量化

Für eine **Standardauflösung von 640 × 480 Pixel** (z.B Graphikstandard VGA=Video Graphics Array), einer Farbtiefe von 8 Bit (z.B RGB-Farbraum) pro Farbkanal und einer Bildwiederholrate von 25 Hertz (PAL Fernsehnorm), ergibt sich folgender Speicherbedarf
对于640×480像素的标准分辨率（例如图形标准VGA =视频图形阵列），每个颜色通道的颜色深度为8位（例如RGB颜色空间），图像重复率为25赫兹（PAL电视标准）结果遵循内存要求

![Alt text](Figures\Folien_5_7.png)

#### 5.2.1.7 Nachbarschaftsoperationen

**Objekte** bedecken fast immer eine *zusammenhängende Region von einzelnen Pixeln*
对象几乎总是覆盖单个像素的连续区域

Zur **Beschreibung eines Objektes** bzw einer Bildregion spielt die Auswertung von **Nachbarschaftsbeziehungen** eine **grundlegende Rolle**
对于对象或图像区域的描述，对邻居关系的分析起着基本作用

Ein **direkter Nachbarpixel** muss eine *gemeinsame Kante oder mindestens eine gemeinsame Ecke aufweisen*
直接相邻像素必须具有公共边缘或至少具有公共角

**Prinzipiell** können aber auch *größere Nachbarschaften für einen Pixel* definiert werden, wobei *nicht alle Nachbarpixel direkt angrenzen*.
原则上，也可以为一个像素定义较大的邻域，但并非所有相邻像素都直接相邻

#### 5.2.1.8 Distanzen

Jeder **Gitterpunkt p** eines diskreten Bildes hat einen **Gittervektor**
离散图像的每个网格点p具有网格矢量

![Alt text](Figures\Folien_5_8.png)

Damit ergibt sich die **euklidische Distanz** auf einem diskreten Gitter wie folgt:
这会在离散网格上产生欧几里德距离，如下所示：

![Alt text](Figures\Folien_5_9.png)

Es lassen sich noch **weitere Distanzen** auf einem Gitter definieren, die jedoch *für praktische Anwendungen*, wie z.B Vermessungsaufgaben, nicht relevant sind, da sie **richtungsabhängig** sind.
可以在网格上定义其他距离，但这些距离与实际应用无关，例如测量任务，因为它们是方向相关的

![Alt text](Figures\Folien_5_10.png)

### 5.2.2 Bilder als Vektoren

### 5.2.3 Zerlegung und Rekonstruktion

#### 5.2.3.1 Unüberwachtes Lernen

Generatives Modell:
![Alt text](Figures\Folien_5_11.png)

![Alt text](Figures\Folien_5_13.png)
![Alt text](Figures\Folien_5_14.png)

Gütekriterium:
![Alt text](Figures\Folien_5_12.png)

**Anwendungen**
- PCA, ICA, NMF, ..
- K-Means, Gaussian Mixtures, Fuzzy-C-means, ..
- Codebook/Representation learning, Klassifikation, ...

#### Basisbilder

Man kann sich jedes M×N Bild G als gewichtete Summe aus M×N unterschiedlichen Basisbildern Bm,n mit den einzelnen Grauwerten Gm,n als Gewichte vorstellen:
可以将每个M×N图像G想象为M×N个不同基本图像Bm，n的加权和，其中各个灰度值Gm，n作为权重：

![Alt text](Figures\Folien_5_15.png)

Jedes **Basisbild Bm,n** hat **nur** *an einem Bildpunkt (m, n) den Wert eins*, an allen *anderen Bildpunkten den Wert null*:
每个基本图像Bm，n仅在一个图像点（m，n）处具有值1，并且在所有其他图像点处的值为零：

![Alt text](Figures\Folien_5_17.png)

Diese **Basisbilder bilden eine orthonormale Basis**, da das *innere Produkt* zweier unterschiedlicher Basisvektoren:
这些基本图像形成了一个标准正交基础，因为两个不同基向量的内积：

![Alt text](Figures\Folien_5_16.png)

*immer null* ergibt und das *innere Produkt eines Basisbildes mit sich selbst immer eins*
始终为零，基本图像的内在产品本身就是一个

Die **Basisvektoren** spannen damit einen M × N - dimensionalen Vektorraum auf
因此，基矢量跨越M×N维向量空间

Ein **Bild** entspricht also einem *M×N - dimensionalen Vektor* in diesem Vektorraum
因此，图像对应于该向量空间中的M×N维向量

Ändert man nun die Koordinaten, geht keine Bildinformation verloren, sondern nur die Koordinaten werden verändert
如果现在更改坐标，则不会丢失任何图像信息，只会更改坐标
>Das bedeutet, die gleiche Information wird aus einem anderen „Blickwinkel“ betrachtet.
这意味着从不同的“视角”查看相同的信息

### 5.2.4 Wellenzahlraum

#### 5.2.4.1 Periodische Basisbilder im Ortsraum

![Alt text](Figures\Folien_5_18.png)
![Alt text](Figures\Folien_5_19.png)

Ein **zweidimensionales periodisches Muster** (G(x) = r cos(2πk>x − ’)) ist gegeben durch:
- Wellenzahl-Vektor k = [k1, k2]T
- Wellenlänge λ
- Betrag des Wellenzahl-Vektors |k| = 1/λ
- Amplitude r
- Abstand des ersten Maximums vom Ursprung ∆x
- Phasenwinkel ’ = 2π∆x=λ = 2π∆xjkj

#### 5.2.4.2 2D Fouriertransformation

Die **kontinuierliche 2D Fouriertransformation** zerlegt eine kontinuierliche 2D Bildfunktion in periodische Strukturen unterschiedlicher Wellenlänge und Richtung.
连续2D傅立叶变换将连续2D图像函数分解为不同波长和方向的周期性结构

![Alt text](Figures\Folien_5_20.png)

#### 5.2.4.3 2D Diskrete Fouriertransformation

Die **2D-DFT** bildet komplexwertige (oder reellwertige) M×N-Matrizen auf komplexwertige M × N-Matrizen ab:
2D-DFT将复值（或实值）MxN矩阵映射到复值MxN矩阵：

![Alt text](Figures\Folien_5_21.png)

Die **inverse 2D-DFT** ergibt sich entsprechend zu:

![Alt text](Figures\Folien_5_22.png)

Die Matrizen Wu,v können als Basisbilder aufgefasst werden, die einen N × M dimensionalen Vektorraum über dem Körper der komplexen Zahlen aufspannen
矩阵Wu，v可以被认为是跨越复数体上的N×M维空间的基本图像

Deswegen kann die **DFT** auch als eine *Koordinatentransformation in einem komplexen N × M-dimensionalen Vektorraum* verstanden werden
因此，DFT也可以被理解为复N×M维向量空间中的坐标变换

#### 5.2.4.4 Komplexe Basisbilder

![Alt text](Figures\Folien_5_23.png)

Die **2D DFT** berechnet die **Projektionen des Bildes G** *auf alle Basisbilder Wu,v des Fourierraums*, also die Komponenten Gˆ u,v von G in Richtung der Basisbilder
2D DFT计算图像G在傅立叶空间的所有基本图像Wu，v上的投影，即在基本图像的方向上的G的分量G u，v

**Real- und Imaginärteil der Basisbilder** sind *abgetastete periodische Muster mit unterschiedlichen Wellenzahl-Vektoren k* von ganzzahligen Vektorkomponenten k1 = u, k2 = v.
基本图像的实部和虚部是采样周期模式，其中不同的波数矢量k为整数矢量分量k1 = u，k2 = v

### 5.2.5 Fouriertransformation

#### 5.2.5.1 Beispiel

![Alt text](Figures\Folien_5_24.png)

#### 5.2.5.2 Separabilität

Durch die **Eigenschaft der Separabilität** können Probleme aus dem Zweidimensionalen auf den eindimensionalen Fall zurückgeführt werden
由于可分离性，可以将问题从二维情况归因于一维情况

Das **Prinzip** findet in der Bildverarbeitung *sehr oft Anwendung*, weil es *getrennte Berechnungen entlang von Zeilen und Spalten der Bildmatrix erlaubt*
该原理经常用于图像处理，因为它允许沿图像矩阵的行和列进行单独计算

Eine mehrdimensionale Funktion ist **separabel** falls gilt:
在以下情况下，多维函数是可分离的：
![Alt text](Figures\Folien_5_25.png)

![Alt text](Figures\Folien_5_26.png)

Die **Singulärwertzerlegung (SVD)** erzeugt eine **Matrixzerlegung** in eine gewichtete Summe von separablen Matrizen
奇异值分解（SVD）生成矩阵分解为可分离阵列的加权和

Damit kann überprüft werden, ob eine Matrix **separabel** ist
这可用于检查矩阵是否可分离

![Alt text](Figures\Folien_5_27.png)

#### 5.2.5.3 Faltungstheorem

Die **diskrete 2D Faltung** ist eine der **bedeutendsten Operationen** der Bildverarbeitung im Ortsraum (siehe auch Filterung):
离散2D卷积是空间中最重要的图像处理操作之一（另请参见过滤）:

![Alt text](Figures\Folien_5_28.png)

Das bedeutet, die **Faltung im Ortsraum** ist äquivalent zu einer **komplexen Multiplikation im Fourierraum**
这意味着空间卷积相当于傅立叶空间中的复数乘法

**Faltungstheorem**:
![Alt text](Figures\Folien_5_29.png)

Diese **Eigenschaft** wird vor allem dazu verwendet eine Menge an Faltungen von einem Bild mit unterschiedlichen Faltungskernen schnell zu berechnen, indem man alle Kerne und das Bild in den Fourierraum transformiert, jeden Kern mit dem Bild multipliziert, und dann alle Ergebnisbilder in den Ortsraum rücktransformiert
此属性主要用于通过将所有内核和图像转换为傅里叶空间，将每个内核与图像相乘，然后将所有结果图像反向转换为位置空间，从具有不同卷积内核的图片中快速计算一组卷积

Zusätzliche **Beschleunigung** erreicht man durch *effiziente Berechnung der DFT mit der FFT*
通过FFT有效地计算DFT来实现额外的加速

---

## 5.3 2D Signalverarbeitung

### 5.3.1 Nachbarschaftsoperationen

#### 5.3.1.1 Bedeutung

**Nachbarschaftsoperationen** sind wahrscheinlich die wichtigsten und am meisten verwendeten Operationen in der Bildverarbeitung
邻域操作可能是最重要和最常用的图像处理操作

Das liegt daran, dass die **wesentliche Information** eines Bildes *in der räumlichen Konfiguration der Grauwerte verborgen ist*
这是因为图像的基本信息隐藏在灰度值的空间配置中

**Nachbarschaftsoperationen** *geben Auskunft über bestimmte Eigenschaften* der räumlichen Konfiguration innerhalb eines kleinen Bildausschnittes
邻域操作在小图像细节内提供有关空间配置的特定属性的信息

Damit **liefern sie die Grundlage** zur Analyse von Bildern und für komplexere Muster- und Objekterkennungsaufgaben.
它们为分析图像和更复杂的图案和对象识别任务提供了基础

Einige **Eigenschaften** von Nachbarschaftsoperatoren:
邻里运营商的一些属性：
- Detektion einfacher lokaler Strukturen, wie Kanten, Ecken, Linien und homogene Bereiche,
检测简单的局部结构，如边缘，角落，线和均匀区域，
- Korrektur von Störungen,
干扰校正，
- Texturanalyse, usw.
纹理分析等

#### 5.3.1.2 Definition

Ein **Nachbarschaftsoperator N** **verknüpft** durch eine geeignete Operation die Werte *in einer Nachbarschaft* um einen Bildpunkt und schreibt das Ergebnis **zurück** an diesen Punkt
邻域运算符N通过适当的操作将邻域中的值与一个像素相关联，并将结果写回该点

Diese **Operation** wird *für alle Punkte im Bild durchgeführt*
对图像中的所有点执行此操作

![Alt text](Figures\Folien_5_30.png)

Das **Gebiet M** wird als *Maske oder Fenster* bezeichnet
区域M称为掩模或窗口

Die **Größe und Form von M** bestimmen die Eingangswerte aus g bzw. G zur Berechnung von g' bzw. G'.
M的大小和形状分别确定g和G的输入值，以分别计算g'和G'。

**Unterschiedliche Arten von Operatoren**:
不同类型的运营商：
- Nichtlinear, verschiebungsvariant (ortsadaptiv)
非线性，位移可变（适应位置）
- Nichtlinear, verschiebungsinvariant (translationsinvariant)
非线性，移位不变量（平移不变量）
- Linear, verschiebungsvariant
线性，位移可变
- Linear, verschiebungsinvariant = LSI-Operator (linear, shift-invariant)
线性，verschiebungsinvariant = LSI-Operator（线性，移位不变）

**Kenngrößen/Eigenschaften einer Maske**:
面具的特征/属性：
- Lage des Bezugspunkts bzw. Ankers (meistens im Zentrum)
参考点的位置或Ankers（主要在中心）
- Maskengröße gerade oder ungerade
面罩尺寸均匀或奇数
- Maskenfunktion symmetrisch oder nicht
掩模功能是否对称

>**Achtung**: Bei gerader Maskengröße verschiebt sich das Ergebnisbild um einen halben Pixel
注意：使用直接掩模大小时，结果图像会移动半个像素

>Das **führt zu** Fehlern bei der Kombination des Ergebnisbildes mit dem Ausgangsbild
这导致结果图像与输出图像的组合中的错误

>**Hinweis**: Grundsätzlich kann jede Verschiebung mit einem LSI-Operator erzeugt werde
注意：基本上每个班次都可以通过LSI操作员生成

#### 5.3.1.3 Diskrete Faltung

![Alt text](Figures\Folien_5_32.png)

Bei der **diskreten Faltung** wird jeder Bildpunkt im Bereich der Maske mit einem Wichtungsfaktor multipliziert, die Produkte addiert und die Summe an die Position des Ankers geschrieben.
在离散卷积的情况下，掩模区域中的每个像素乘以加权因子，将乘积加在一起，并将总和写入电枢的位置

#### 5.3.1.4 Faltung & Korrelation

**Diskrete Faltung** mit quadratischer Maske und Anker im Zentrum:
在中心使用方形面具和锚点进行离散折叠：

![Alt text](Figures\Folien_5_33.png)

**Diskrete Korrelation** mit quadratischer Maske und Anker im Zentrum:
在中心与方形掩模和锚点的离散相关：

![Alt text](Figures\Folien_5_34.png)

>Wenn eine Maske symmetrisch ist h−m,−n = hm,n, wird sie durch eine Spiegelung nicht verändert
如果掩模是对称的h-m，-n = hm，n，则它不会被反射改变

>Damit unterscheiden sich Faltung und Korrelation für symmetrische Masken nicht.
因此，对称掩模的卷积和相关性没有差别。

##### 5.3.1.4.1 Randbehandlung

Am Rand des Bildes geht der Bereich der Maske über den Bildrand hinaus
在图像的边缘，掩模的区域超出图像的边缘

Was für Bildpunkte sollen dort angenommen werden? Wenn die *Faltung im Ortsraum einer Multiplikation im Fourierraum entsprechen* soll, dann muss die *Bildmatrix als periodisch wiederholende Struktur* betrachtet werden
那里应该接受什么样的像素？如果空间空间中的卷积对应于傅立叶空间中的乘法，那么图像矩阵必须被视为周期性重复结构

Wird das angenommen spricht man auch von **zyklischer Faltung**
如果假设这一点，人们也会谈到循环卷积

**In der Praxis** wird jedoch zwischen drei anderen Methoden gewählt, wobei zwischen *geringen Artefakten und schneller Berechnung* **abgewägt** werden muss
然而，在实践中，还需要在低伪像和快速计算之间权衡其他三种方法
- Rand mit Nullen auffüllen (schnell aber viel Artefakte)
用零填充边距（快速但很多工件）
- Rand spiegeln
镜边
- Rand extrapolieren (z.B Grauwert fortführen, Überbetonung der Ränder).
外推边缘（例如，继续灰度值，过度强调边缘）

##### 5.3.1.4.2 Effektive Berechnung

Wie man eine **diskrete Faltung** mit der *geringstmöglichen Anzahl an Rechenoperationen* berechnet **hängt** zum einen von der *Maskengröße* und zum anderen von den *Eigenschaften des Faltungskerns* ab
如何使用最少数量的计算操作来计算离散卷积取决于掩码大小和卷积核的属性

**Separabilität** und **Symmetrie** sind die beiden Eigenschaften, deren *konsequente Ausnutzung große Beschleunigungen erlauben*
可分离性和对称性是两个属性，其一致使用允许很大的加速度

Ab einer **bestimmten Maskengröße** *lohnt sich* die *zusätzliche Hin- und Rücktransformation in den Fourierraum*, um eine wenig rechenaufwendige Multiplikation im Frequenzbereich auszuführen (Filter können eventuell schon vor der Laufzeit transformiert werden)
从某个掩模大小开始，额外来回转换到傅立叶空间是值得的，以便在频域中执行一点计算密集的乘法（滤波器可能在运行时之前被转换）

**Weitere Möglichkeiten** der Beschleunigung sind die *Zerlegung von Filtermasken* und *Lookup-Tabellen*
加速的其他可能性包括滤波器掩码和查找表的分解

Sind die **Filterkerne sehr klein**, können *alle möglichen Multiplikationen vorab berechnet werden und in Lookup-Tabellen abgelegt* werden
如果滤波器内核非常小，则可以预先计算所有可能的乘法并将其存储在查找表中

Manchmal ist es möglich die **Faltung mit einer großen Filtermaske** *in ein sequentielles Ausführen von Faltungen mit kleineren Masken zu überführen*.
有时可以将带有大滤波器掩码的卷积转换为带有较小滤波器的卷积的顺序执行

###### 5.3.1.4.2.1 IPP Vergleich

![Alt text](Figures\Folien_5_35.png)

Vergleich verschiedener Möglichkeiten der beschleunigten Berechnung von Faltungen in Abhängigkeit von der Größe der Filtermasken
比较根据滤光片掩模的大小加速计算卷积的不同可能性

Benutzt wurde eine für Bildverarbeitung optimierte C-Bibliothek, die Intel Integrated Performance Primitives (Intel® IPP).
它使用了一个名为Intel Integrated Performance Primitives（英特尔®IPP）的图像处理优化C库

#### 5.3.1.5 Faltung

##### 5.3.1.5.1 Punktantwort

Die **Punktantwort∗ oder point spread function (PSF)** ist die Antwort einer Faltungsoperation auf ein Punktbild (Basisbild) und ist mit der Faltungsmaske identisch:
点响应*或点扩散函数（PSF）是对点图像（基本图像）进行卷积运算的答案，与折叠掩码相同：

P = H ∗ Bm,n = H

Die **Punktantwort** zeigt, wie sich jeder Pixel in die Nachbarschaft ausbreitet
答案显示每个像素如何传播到邻域

Da die Faltung ein **LSI-Operator** ist, für sie also das Superpositionsprinzip gilt und sie verschiebungsinvariant ist, ist das **Ergebnis einer Faltung** vollständig durch die Antwort auf ein beliebiges Basisbild bestimmt.
由于卷积是LSI算子，即它具有叠加原理并且是移位不变的，因此卷积的结果完全由对任何基本图像的答案决定

##### 5.3.1.5.2 Transferfunktion

Die *Fouriertransformierte einer Faltungsmaske oder PSF* heißt **Transferfunktion (TF) eines Filters∗**
卷积掩模或PSF的傅立叶变换称为滤波器的传递函数（TF）*

Die **TF** gibt für jeden Wellenzahlvektor den Faktor an, mit dem die entsprechende periodische Struktur durch eine Filteroperation multipliziert wird
TF为每个波数矢量指示相应的周期结构乘以滤波操作的因子

Da dieser **Faktor komplex** ist, wird **sowohl** die Amplitude, **als auch** die Phase der periodischen Struktur verändert
由于该因子很复杂，周期性结构的幅度和相位都会发生变化

Man *sieht also welche Frequenzen* im Bild wie **stark gefiltert werden**
因此，您可以看到图片中的哪些频率被过滤掉了

Damit ist die **TF sehr nützlich**, um einen *Filter mit speziellen Eigenschaften* zu entwickeln.
因此，TF对于开发具有特殊属性的过滤器非常有用

---

## 5.4 Digitale Kamera

### 5.4.1 Digitalisierung

#### 5.4.1.1 Mathematische Beschreibung

Die **Transformation** von einem kontinuierlichen Bild zu einer *räumlich begrenzten Bildmatrix* kann **mathematisch in drei Schritte zerlegt** werden:
从连续图像到空间受限图像矩阵的转换可以在数学上分解为三个步骤：

- Die Mittelung der Intensität,
强度平均，
- die Abtastung und
抽样和
- die Ortsbegrenzung
位置限制

Aus den **Zusammenhängen** lassen sich
从连接可以
- das Abtasttheorem und
采样定理和
- der Aliasing-Effekt erklären. Außerdem liefert das Abtasttheorem die Bedingung für eine perfekte
解释别名效应. 此外，采样定理为采样点的完美
- Rekonstruktion aus Abtastpunkten.
重建提供了条件

#### 5.4.1.2 Intensitätsmittelung

Die **Intensität für einen Bildpunkt** wird gleichmäßig über die Fläche der einzelnen Photodioden gemittelt (ideale CCD Kamera)
像素的强度在各个光电二极管的区域上均匀平均（理想的CCD相机）

Das **entspricht** einer *Faltung der kontinuierlichen Bildfunktion* E(x, y) z.B mit einer rechteckigen Kastenfunktion r1(x, y):
这对应于连续图像函数E（x，y）的卷积，例如矩形框函数r1（x，y）：

![Alt text](Figures\Folien_5_36.png)

wobei die Punktantwort folgendermaßen gegeben ist:
点响应的地方如下：

![Alt text](Figures\Folien_5_37.png)

Diese **Faltung** bewirkt eine *Glättung des Bildes*, wobei feine Details verloren gehen.
这种卷积使图像平滑，失去了细节

![Alt text](Figures\Folien_5_40.png)

Eine **Faltung im Ortsraum (x, y)** entspricht einer *Multiplikation im Fourierraumˆ*
空间（x，y）中的卷积对应于傅里叶空间中的乘法

Dabei ist (k1, k2)T der Wellenzahlvektor
其中(k1，k2)T是波数矢量

![Alt text](Figures\Folien_5_38.png)

wobei die **optische Transferfunktion** folgendermaßen gegeben ist:
光学传递函数如下：

![Alt text](Figures\Folien_5_39.png)

**Im Fourierraum** führt die Multiplikation des Bildspektrums mit der optischen Transferfunktion zu einer Dämpfung hoher Wellenzahlen.
在傅里叶空间中，图像光谱与光学传递函数的相乘导致高波数的衰减

#### 5.4.1.3 Abtastung

Die **Abtastung des geglätteten Bildes** wird an den Gitterpunkten eines zweidimensionalen Gitters mit konstanten Gitterpunktabständen durchgeführt
在具有恒定网格间距的二维网格的网格点处执行平滑图像的扫描

Dadurch geht alle Bildinformation außerhalb der Gitterpunkte verloren
结果，网格点之外的所有图像信息都丢失了

**Mathematisch** entspricht das einer Multiplikation der Bildfunktion E1(x, y) im Ortsraum mit einem zweidimensionalen Deltakamm:
在数学方面，这对应于空间域中图像函数E1（x，y）与二维delta梳的相乘：

![Alt text](Figures\Folien_5_41.png)

Dies **entspricht im Fourierraum** einer Faltung des Bildspektrums Eˆ1(k1, k2) mit einem Deltakamm des reziproken Gitters
在傅立叶空间中，这对应于图像光谱E1（k1，k2）与参考proch网格的三角梳的卷积

![Alt text](Figures\Folien_5_42.png)

#### 5.4.1.4 Abtasttheorem

#### 5.4.1.5 Ortsbegrenzung

#### 5.4.1.6 Perfekte Rekonstruktion

### 5.4.2 Aliasing

#### 5.4.2.1 Moire-Effekt
