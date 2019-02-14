<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 7 Geometrische Transformationen und Punktoperatoren](#folien-7-geometrische-transformationen-und-punktoperatoren)
	- [7.1 Geometrische Transformationen](#71-geometrische-transformationen)
		- [7.1.1 Anwendungen](#711-anwendungen)
		- [7.1.2 Definition](#712-definition)
		- [7.1.3 Existenz der Rückwärtsabbildung](#713-existenz-der-rückwärtsabbildung)
		- [7.1.4 Polynomiale 2D Abbildungen](#714-polynomiale-2d-abbildungen)
		- [7.1.5 Affine 2D Abbildung](#715-affine-2d-abbildung)
		- [7.1.6 Perspektivische 2D Abbildung](#716-perspektivische-2d-abbildung)
		- [7.1.7 Interpolation der Helligkeitserte](#717-interpolation-der-helligkeitserte)
			- [7.1.7.1 Ideale Interpolation](#7171-ideale-interpolation)
			- [7.1.7.2 Interpolationsarten](#7172-interpolationsarten)
			- [7.1.7.3 Beispiel](#7173-beispiel)
	- [7.2 Punktoperatoren](#72-punktoperatoren)
		- [7.2.1 Anwendungen](#721-anwendungen)
		- [7.2.2 Definition](#722-definition)
		- [7.2.3 Homogene Operatoren](#723-homogene-operatoren)
			- [7.2.3.1 Beispiele](#7231-beispiele)
		- [7.2.4 Inhomogene Operatoren](#724-inhomogene-operatoren)

<!-- /TOC -->

# Folien 7 Geometrische Transformationen und Punktoperatoren

---

## 7.1 Geometrische Transformationen

### 7.1.1 Anwendungen

**Geometrische Transformationen** beeinflussen das „Wo“ eines Bildpunktes und werden in einer Reihe von Bildverarbeitungsanwendungen benötigt z.B
几何变换影响像素的“位置”，并且在许多图像处理应用中需要，例如，
- Verzeichnungen eliminieren
消除扭曲
- Bilder zusammenfügen (Stitching)
拼接图片（拼接）
- Bilder registrieren
注册图片

**Geometrische Transformationen** können in *parametrischer Form* oder als *Vektorfeld* angegeben werden
几何变换可以以参数形式或矢量场指定
Die **Transformation** beinhaltet zwei Schritte:
转型包括两个步骤：
- Transformation der Koordinaten
坐标转换
- Interpolation der Bildwerte.
插值图像值

### 7.1.2 Definition

**Geometrische Transformationen** definieren einen funktionalen Zusammenhang zwischen den Koordinaten x und x' von Punkten zweier Bilder
几何变换定义了两个图像的点的坐标x和x'之间的函数关系

Dabei wird zwischen **zwei Arten unterschieden**:
有两种类型：

- **Vorwärtsabbildung** 下一张图片 -- x' = M(x)

![Alt text](Figures\Folien_7_1.png)

- **Rückwärtsabbildung** 反向映射 -- x = M−1(x')

![Alt text](Figures\Folien_7_2.png)

### 7.1.3 Existenz der Rückwärtsabbildung

Liegt die **Transformation** *in parametrischer Form* vor und ist die Transformationsvorschrift nach den Koordinaten differenzierbar, dann kann man anhand der *Determinante der Jakobi-Matrix∗ J(M(x))* feststellen, **ob eine inverse Transformation existiert**
如果变换是参数形式并且如果变换规则根据坐标是可微分的，那么可以从Jakobi矩阵的行列式确定* J（M（x））是否存在逆变换

![Alt text](Figures\Folien_7_3.png)
![Alt text](Figures\Folien_7_4.png)

### 7.1.4 Polynomiale 2D Abbildungen

Viele **Vektorfelder** können durch *polynomiale Transformationen* approximiert werden
许多矢量场可以通过多项式变换来近似

![Alt text](Figures\Folien_7_5.png)

Diese **Transformationen** sind stets *linear in den Koeffizienten ark, brk* aber *polynomial in den Koordinaten x, y*
这些变换在系数ark，brk中始终是线性的，但在坐标x，y中是多项式的

Die **bilineare Transformation** ist eine einfache und häufig benutzte polynomiale Transformation
双线性变换是一种简单且经常使用的多项式变换

![Alt text](Figures\Folien_7_6.png)

### 7.1.5 Affine 2D Abbildung

![Alt text](Figures\Folien_7_8.png)

Die **affine Abbildung** ist eine *lineare Koordinatentransformation*, die die elementaren Transformationen Translation, Rotation, Dilatation, Stauchung und Scherung ermöglicht
仿射图是线性坐标变换，允许平移，旋转，扩张，压缩和剪切的基本变换

![Alt text](Figures\Folien_7_7.png)

### 7.1.6 Perspektivische 2D Abbildung

Um die **geometrische Abbildung** einer **projizierten Fläche** zwischen *zwei Kameraaufnahmen aus unterschiedlichen Blickwinkeln* zu beschreiben, benötigt man eine **nichtlineare, sogenannte perspektivische Abbildung**
为了描述来自不同角度的两个相机图像之间的投影区域的几何图像，需要非线性的，所谓的每光谱成像

![Alt text](Figures\Folien_7_9.png)
![Alt text](Figures\Folien_7_10.png)

Es werden **mindestens** *4 nichtkollineare Punkte* benötigt, um die perspektivischen Parameter zu bestimmen
至少需要4个非共线点来确定透视参数

Bei mehr als vier Punkten findet man eine Lösung z.B über die Methode der kleinsten Quadrate
如果存在多于四个点，则可以找到解决方案，例如，使用最小二乘法

### 7.1.7 Interpolation der Helligkeitserte

#### 7.1.7.1 Ideale Interpolation

Wie bereits im Abschnitt **Digitalisierung-Rekonstruktion** gesehen, erhält man eine **Interpolation der Abtastpunkte** *über eine Faltung mit einem Interpolationsfilter h*:
如在数字化重建部分中已经看到的，通过具有插值滤波器h的卷积获得采样点的插值：

![Alt text](Figures\Folien_7_11.png)

Die **perfekte Interpolationsfunktion** wäre eine unendlich ausgedehnte SincFunktion
完美的插值函数是无限扩展的sinc函数

![Alt text](Figures\Folien_7_12.png)

Da **in der Praxis** **nur lokale** *Interpolationsfilter angewendet* werden, um den Rechenaufwand niedrig zu halten, geht bei **geometrischen Operationen** im Allgemeinen *Bildinformation verloren*.
由于实际上仅使用局部插值滤波器来保持较低的计算量，因此几何操作通常会丢失图像信息

#### 7.1.7.2 Interpolationsarten

In der Praxis werden im Wesentlichen **drei unterschiedliche Interpolationsarten** benutzt:
在实践中，基本上使用三种不同类型的插值：

- **Nächster-Nachbar-Interpolation**
最近邻插值

![Alt text](Figures\Folien_7_14.png)
![Alt text](Figures\Folien_7_15.png)

Der **interpolierte Grauwert G(x)** an der Stelle x = (x, y)T entspricht dem am nächsten gelegenen Grauwert G(pˆ) auf dem diskreten Bildpunktgitter pˆ , wobei gilt:
位置x =(x，y)T处的内插灰度值G(x)对应于离散像素网格p上的最近灰度值G(p)，其中：

p = (m∆x, n∆y)T

G(x) = G(pˆ) , wobei pˆ = argminp||p−x|| .

- **Bilineare Interpolation**
Bilineare插值

![Alt text](Figures\Folien_7_16.png)
![Alt text](Figures\Folien_7_17.png)

Den interpolierten Grauwert G(x) an der Stelle x = (x, y)T erhält man über die bilineare Form
通过双线性形式获得位置x =（x，y）T处的内插灰度值G（x）

- **Bikubische Interpolation**

![Alt text](Figures\Folien_7_18.png)

Den interpolierten Grauwert G(x) an der Stelle x = (x, y)T erhält man über die bikubische Form
通过双三次形式获得位置x =（x，y）T处的内插灰度值G（x）

Die 16 Koeffizienten aij werden über die Helligkeitswerte G(pi), wobei i = 1 - 4, und deren Ableitungen Gx(pi), Gy(pi) und Gxy(pi) bestimmt.
16个系数aij由亮度值G（pi）确定，其中i = 1-4，并且它们的导数Gx（pi），Gy（pi）和Gxy（pi）

#### 7.1.7.3 Beispiel

![Alt text](Figures\Folien_7_13.png)

- NN: Falsche hohe Wellenzahlen werden erzeugt, - viele Artefakte
NN: 生成错误的高波数， - 许多工件
- BL: Hohe Wellenzahlen werden gedämpft, - starke Glättung
BL: 高波纹阻尼， - 强力平滑
- BK: Leichte Glättung, wenig Artefakte.
BK: 轻微的平滑，很少的文物

---

## 7.2 Punktoperatoren

### 7.2.1 Anwendungen

**Punktoperatoren** beeinflussen das **„Was“** eines Bildpunktes und modifizieren die Grauwerte einzelner Bildpunkte *nur in Abhängigkeit vom Grauwert selbst* und eventuell *von der Position des Bildpunktes*
点运算符影响像素的“什么”，并且仅根据灰度值本身和可能在像素的位置上修改单个像素的灰度值

**Punktoperatoren** werden für folgende Anwendungen benötigt:
以下应用程序需要点运算符：
- Korrektur und Optimierung von Beleuchtung,
照明的校正和优化，
- Detektion von Unter- und Überlauf,
检测下溢和溢流，
- Kontrastverstärkung und -dehnung,
对比度增强和拉伸，
- Bildmittelung bei Mehrbildaufnahmen,
多图像记录中的图像平均，
- Korrektur inhomogener Beleuchtung,
纠正不均匀的照明，
- Radiometrische Kalibrierung.
辐射校准

### 7.2.2 Definition

Es gibt **sowohl** homogene (ortsinvariante) **als auch** inhomogene (ortsvariante) **Punktoperatoren**
有均匀（场所不变）和非均匀（场所变体）点运算符

Sie sind i.A **nicht umkehrbar** -- *Information geht verloren*
它们不可逆 - 信息丢失

- **Homogene Punktoperatoren** : Jeder Grauwert G(p) wird *über die Funktion F* auf sich selbst abgebildet:
均匀点运算符每个灰度值G（p）通过函数F映射到自身：

 G'(p) = F(G(p))

- **Inhomogene Punktoperatoren** : Jeder Grauwert G(p) wird *über eine vom Ort p abhängige Funktion F* auf sich selbst abgebildet:
非均匀点运算符每个灰度值G（p）通过函数F映射到自身，取决于位置p：

 G'(p) = F(G(p), p)

### 7.2.3 Homogene Operatoren

#### 7.2.3.1 Beispiele


- **Kontrastverstärkung** 对比度加强

  Verbesserung des visuellen Eindrucks eines Bildes **durch** das *Abbilden des Grauwertbereiches eines Bildes* auf den *vollen Kontrastbereich*
通过将图像的灰度范围映射到完整的对比度范围来改善图像的视觉印象

  Die Bildqualität erhöht sich dadurch nicht!
图像质量不会提高

  ![Alt text](Figures\Folien_7_19.png)

- **Kontrastspreizung/-stauchung**
对比度传播/  - 压缩

  Verbesserung des visuellen Eindrucks eines Bildes **durch** das *Abbilden eines begrenzten Grauwertbereiches eines Bildes* auf einen *größeren/kleineren Kontrastbereich*
通过将图像的有限灰度范围映射到更大/更小的对比度范围来改善图像的视觉印象

  Die Bildqualität erhöht sich dadurch nicht!
因此图像质量不会增加！

  ![Alt text](Figures\Folien_7_20.png)

- **Histogrammausgleich** 直方图均衡化

  Dient auch der **Kontrastverbesserung** in Grauwertbildern
还用于灰度值图像中的对比度增强

  Hierzu wird die *Grauwertskala in Bereichen mit häufigen Grauwerten gestreckt* und in Bereichen mit weniger häufigen Grauwerten gestaucht
为此目的，灰度等级在具有频繁灰度值的区域中被拉伸并且在具有较低频率灰度值的区域中被压缩

  Die **Transformation** entspricht einfach der *Verteilungsfunktion P(G) des Grauwertbildes*.
变换简单地对应于灰度值图像的分布函数P（G）

  ![Alt text](Figures\Folien_7_21.png)

### 7.2.4 Inhomogene Operatoren

Im Gegensatz zu homogenen Operatoren, wo die Transformation in einer Lookup-Tabelle abgespeichert werden kann, muss sie bei **inhomogenen Operatoren** meistens *für jedes Pixel berechnet werden*
与同构运算符相比，转换可以存储在查找表中，对于非均匀运算符，通常必须为每个像素计算
Beispiele für inhomogene Operatoren sind:
非均匀运算符的示例是：
- Subtraktion von Hintergrundbildern,
减去背景图像，
- zeitliche Bildmittelung,
时间图像平均，
- Adaptiver Histogrammausgleich
自适应直方图均值化

  ![Alt text](Figures\Folien_7_22.png)
