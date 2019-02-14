<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 9 Deskriptoren](#folien-9-deskriptoren)
	- [9.1 Idee](#91-idee)
	- [9.2 Aufgabe](#92-aufgabe)
	- [9.3 Definition](#93-definition)
		- [9.3.1 Ziel und Nutzen](#931-ziel-und-nutzen)
	- [9.4 Güte der Merkmale](#94-güte-der-merkmale)
		- [9.4.1 Diskriminativität](#941-diskriminativität)
		- [9.4.2 Invarianz](#942-invarianz)
	- [9.5 Variationen](#95-variationen)
		- [9.5.1 Ansicht und Beleuchtung eines Objektes](#951-ansicht-und-beleuchtung-eines-objektes)
		- [9.5.2 Innerhalb von Objektklassen](#952-innerhalb-von-objektklassen)
	- [9.6 Merkmale zur Beschreibung](#96-merkmale-zur-beschreibung)
	- [9.7 Skalenraum](#97-skalenraum)
		- [9.7.1 Nutzen und Definition](#971-nutzen-und-definition)
		- [9.7.2 Ortsraum und Wellenzahlraum](#972-ortsraum-und-wellenzahlraum)
		- [9.7.3 Lokale Fouriertransformation](#973-lokale-fouriertransformation)
			- [9.7.3.1 Unschärferelation](#9731-unschärferelation)
		- [9.7.4 Mehrgitterstrukturen 更多的光栅结构](#974-mehrgitterstrukturen-更多的光栅结构)
			- [9.7.4.1 Vorteil](#9741-vorteil)
			- [9.7.4.2 Gaußpyramide](#9742-gaupyramide)
			- [9.7.4.3 Laplacepyramide](#9743-laplacepyramide)
	- [9.8 Lokale Strukturen](#98-lokale-strukturen)
		- [9.8.1 Strukturtensor](#981-strukturtensor)
			- [9.8.1.1 Motivation](#9811-motivation)
			- [9.8.1.2 Definition](#9812-definition)
			- [9.8.1.3 Orientierung](#9813-orientierung)
			- [9.8.1.4 Kohärenz](#9814-kohärenz)
			- [9.8.1.5 Eckpunkt (corner feature)](#9815-eckpunkt-corner-feature)
		- [9.8.2 Histogramme](#982-histogramme)
			- [9.8.2.1 HoG](#9821-hog)

<!-- /TOC -->

# Folien 9 Deskriptoren
---

## 9.1 Idee

Frage: Wie wird ein Bildausschnitt bzw ein Objekt im Bild beschrieben und wie wird diese Beschreibung repräsentiert?
问题：图片中描述的图片部分或对象如何以及如何表示此描述？

## 9.2 Aufgabe

![Alt text](Figures\Folien_9_1.png)

---

## 9.3 Definition

### 9.3.1 Ziel und Nutzen

- **Definition**: Ein **Deskriptor** *repräsentiert bestimmte Eigenschaften* eines Bildausschnittes bzw Objektes **in Form eines Merkmalsvektors**
定义：描述符以特征向量的形式表示图片细节或对象的某些属性

- **Ziel**: Je nach Aufgabe sollen diese **Merkmale** *möglichst diskriminativ (unterscheidbar)* für ein bestimmtes Objekt bzw eine bestimmte Objektklasse sein und *möglichst invariant (unbeeinflussar)* gegenüber Schwankungen in den Ausprägungen eines Objektes
目标：根据任务的不同，这些特征对于特定对象或特定对象类应尽可能具有辨别力（无法区分），并且应尽可能不受影响（不受影响）以防止对象表达式的波动

- **Nutzen**: Je **diskriminativer** und **invarianter** ein Deskriptor ist, desto einfacher kann eine Segmentierungs-, Detektions- oder Klassifikationsaufgabe gelöst werden
好处：描述符越具有判别性和不变性，就越容易解决分割，检测或分类任务

- **Optimierung**: Die **Wahl des Verhältnisses** zwischen der *Komplexität eines Deskriptors* und der *Nichtlinearität eines Detektors (2-Klassen-Problem) bzw Klassifikators (Mehrklassen-Problem)* ist **abhängig von** der *Diskriminativität und den Invarianzeigenschaften* eines Objektes bzw einer Objektklasse.
优化：解密器的复杂性与检测器的非线性（2类问题）或分类器（多类问题）之间的关系的选择取决于对象或对象类的判别性和不变性

---

## 9.4 Güte der Merkmale

Es gibt **zwei Kriterien**, die zur *Bewertung eines Deskriptors* entscheidend sind:
评估描述符有两个至关重要的标准：

**Diskriminativität**: **Je weniger** Merkmalsvektoren sich in einer Nachbarschaft des Merkmalsvektors eines bestimmten Deskriptors befinden und **je größer** der Bereich ohne angrenzenden Merkmalsvektor im Merkmalsraum ist, **desto diskriminativer (unterscheidbarer)** ist ein Deskriptor
判别性：特征描述符的特征向量附近的特征向量越少，特征空间中没有相邻特征向量的区域越大，描述符越具有判别性

**Invarianz**: **Je weniger** Variationen von Objekteigenschaften die Variablen des Merkmalsvektors des Deskriptors beeinflussen, **desto invarianter** ist er gegebenüber solchen Variationen
不变性：对象属性的变化越小，影响描述符特征向量的变量，对这些变化给出的变量就越不变

**Datensätze**: Die Wahl eines geeigneten Datensatzes zur Beurteilung der Güte eines Deskriptors ist *nicht trivial* und sollte alle auftretenden Varianzen eines Objektes mit einer genügend großen Anzahl an Kombinationen (z.B Farbe und Skalierung) beinhalten.
数据集：选择合适的数据集来评估描述符的质量并非易事，应包括具有足够大量组合（例如颜色和比例）的对象的所有方差

### 9.4.1 Diskriminativität

![Alt text](Figures\Folien_9_2.png)

### 9.4.2 Invarianz

![Alt text](Figures\Folien_9_3.png)

---

## 9.5 Variationen

Es gibt eine **Reihe an Variationen**, von denen ein *Deskriptor möglichst unabhängig* sein sollte:
有许多变体，其描述符应尽可能独立：
- Beleuchtungsvariationen (Helligkeit, Kontrast, Lichtquellenbewegung)
照明变化（亮度，对比度，光源移动）
- Objektvariationen (siehe Eigenschaften)
对象变体（参见属性）
- Hintergrundvariationen (siehe Eigenschaften)
背景变化（见属性）
- Größenvariationen (Entfernung oder Objekt?)
尺寸变化（距离或物体？）
- Ansichtsvariationen (Rotation, perspektivische Verzerrung)
查看变化（旋转，透视变形）

### 9.5.1 Ansicht und Beleuchtung eines Objektes

![Alt text](Figures\Folien_9_4.png)

### 9.5.2 Innerhalb von Objektklassen

![Alt text](Figures\Folien_9_5.png)

---

## 9.6 Merkmale zur Beschreibung

Es gibt eine **Menge an Merkmalen** und deren **Eigenschaften**, die ein *Deskriptor zur Beschreibung* von Objekten bzw *Bildausschnitten* benutzen kann:
用于描述对象或图像部分的描述符可以使用许多功能及其属性：

- Farbeigenschaften
颜色属性
- Kontureigenschaften (2D)
轮廓属性（2D）
- Formeigenschaften (3D)
形状属性（3D）
- Struktureigenschaften
结构特性
- Textureigenschaften
- Bewegungseigenschaften
运动特性

Die **Eigenschaften** unterteilen sich im Wesentlichen in Eigenschaften die den *Verlauf im Bildort* beschreiben und *in statistische Eigenschaften*, wie z.B der Häufigkeit eines bestimmten Merkmals.
这些属性基本上细分为描述图像位置中的路线的属性和统计属性，例如特定特征的频率

---

## 9.7 Skalenraum

### 9.7.1 Nutzen und Definition

**Nutzen**: Die  **Detektion von Merkmalen eines Objektes** in einem Bild hängt von der *Größe des Objektes* und der *vorhandenen Bildauflösung* ab
用途：检测图像中对象的特征取决于对象的大小和现有的图像分辨率

Für jedes Merkmal gibt es **nicht nur** einen *geeigneten Detektor* (z.B der Laplaceoperator für die Kantendetektion), **sondern auch** eine *geeignete Bildauflösung*
对于每个特征，不仅有合适的检测器（例如，用于边缘检测的拉普拉斯算子），而且还有合适的图像 **分辨率**

**Definition**: Eine Datenstruktur, die aus einer Folge von *Bildern mit unterschiedlichen Auflösungen* besteht, wird als **Skalenraum** bezeichnet
定义：由具有不同分辨率的图像序列组成的数据结构称为标度空间

**Je kleiner** die Bildauflösung ist, **desto kleiner** ist der Wellenzahlbereich der dargestellt werden kann
图像分辨率越小，可显示的波数范围越小

**Eine Skala** entspricht einem *bestimmten Wellenzahlbereich*.
标度对应于特定的波数范围

### 9.7.2 Ortsraum und Wellenzahlraum

Die **Darstellungen eines Bildes** im *Ortsraum* oder im *Wellenzahlraum* stellen **zwei Extreme** dar:
空间或波数空间中图像的表示代表两个极端：

**Ortsraum**: Die **Positionsgenauigkeit** entspricht der *Bildauflösung*, aber es ist **keine** Wellenzahlinformation vorhanden
空间：位置精度与图像分辨率相同，但没有波数信息

**Wellenzahlraum**: Die **Wellenzahlauflösung** entspricht der *Bildauflösung*, aber es ist **keine** Ortsinformation mehr enthalten.
波长空间：波数分辨率对应于图像分辨率，但不包括位置信息

![Alt text](Figures\Folien_9_6.png)

### 9.7.3 Lokale Fouriertransformation

Die **lokale Fouriertransformation** liefert eine *kombinierte Orts- /Wellenzahldarstellung* über eine zusätzliche Faltung mit einer *örtlich begrenzten Fensterfunktion W(x0 − x)*:
局部傅里叶变换在具有局部窗口函数W（x0-x）的附加卷积上提供组合的空间/波数表示：

![Alt text](Figures\Folien_9_7.png)

Die **Transferfunktion des Faltungskerns** entspricht einem *Bandpassfilter* mit einem Maximum bei der Wellenzahl k0:.
卷积核的传递函数对应于带宽波长为k0的带通滤波器
![Alt text](Figures\Folien_9_8.png)

#### 9.7.3.1 Unschärferelation

Die **Optimale Fensterfunktion** für die **lokale Fouriertransformation** ist die *Gaußfunktion*, da sie die beste Wellenzahlauflösung bei vorgegebener örtlicher Auflösung erreicht
局部傅立叶变换的最佳窗函数是高斯函数，因为它对于给定的空间分辨率实现了最佳波数分辨率

![Alt text](Figures\Folien_9_9.png)

Die *Breite dieses Bandpasses W(kx)* ist **umgekehrt proportional** zur *Breite der Fensterfunktion W(x)*.
该带通W（kx）的宽度与窗函数W（x）的宽度成反比
![Alt text](Figures\Folien_9_10.png)

### 9.7.4 Mehrgitterstrukturen 更多的光栅结构

#### 9.7.4.1 Vorteil

**Feine Strukturen**, also hohe Wellenzahlbereiche, können **nur** mit einer *hohen örtlichen Bildauflösung* dargestellt werden
精细结构，即高波数范围，只能以高局部图像分辨率显示

**Grobe Strukturen**, also niedrige Wellenzahlbereiche, benötigen **nur** eine *niedrige örtliche Bildauflösung* zur Darstellung
粗糙结构，即低波数范围，仅需要低的局部图像分辨率用于显示

**Idee**: Deswegen bietet es sich an, *unterschiedliche Wellenzahlbereiche auch nur mit der Auflösung abzutasten*, die zur vollständigen Darstellung **benötigt** werden
想法：这就是为什么仅使用完整演示所需的分辨率对不同的波数范围进行采样是有意义的

( **Vorsicht**: Abtasttheorem beachten! )
（注意：注意采样定理！）

![Alt text](Figures\Folien_9_11.png)

#### 9.7.4.2 Gaußpyramide

Die **Gaußpyramide** ist eine *Serie von rekursiv tiefpassgefilterten Bildern*, bei denen die Grenzwellenlänge durch Halbieren der Bildauflösung bei jedem Rekursionsschritt auf die Hälfte abnimmt
高斯金字塔是一系列递归低通滤波图像，其中通过在每个递归步骤中将图像分辨率减半，将截止波长减半

Der gesamte Speicherplatz der Pyramide nimmt wegen dem rekursiven Halbieren nur um 1/3 gegnüber dem Originalbild zu
由于递归减半，金字塔的整个存储空间仅比原始图像增加了1/3

Damit erhöht sich der Rechenaufwand auch nur um 1/3.
这使计算工作量仅增加了1/3

![Alt text](Figures\Folien_9_12.png)

#### 9.7.4.3 Laplacepyramide

Die Laplacepyramide ist eine Serie von bandpassgefilterten Bildern, bei denen die zentrale Wellenzahl k0 von Ebene zu Ebene halbiert wird
拉普拉斯金字塔是一系列带通滤波图像，将中心波数k0从平面到平面减半

Durch die Begrenzung der Wellenzahlauflösung bleibt eine gute räumliche Auflösung erhalten
通过限制波数分辨率，仍然保持良好的空间分辨率

Im Vergleich zur lokalen Fouriertransformation ist die Wellenzahlauflösung viel gröber und es gibt keine Richtungszerlegung (Alle Wellenzahlen innerhalb des Bandes sind enthalten)
与局部傅立叶变换相比，波数分辨率更粗糙，并且没有方向分解（包括频带内的所有波数）

Die Laplacepyramide läßt sich direkt aus der Gaußpyramide konstruieren:
拉普拉斯金字塔可以直接从高斯金字塔构建：

![Alt text](Figures\Folien_9_13.png)

Das Originalbild kann komplett aus der Laplacepyramide rekonstruiert werden:
原始图像可以从拉普拉斯金字塔中完全重建：

![Alt text](Figures\Folien_9_14.png)


![Alt text](Figures\Folien_9_15.png)

---

## 9.8 Lokale Strukturen

### 9.8.1 Strukturtensor

#### 9.8.1.1 Motivation

Ein **wesentliches Merkmal** zum Beschreiben von kleinen Bildregionen ist die sogenannte *Struktur*
描述小图像区域的基本特征是所谓的结构

Sie wird durch Größen, wie
它的特点是尺寸，如
- die **Orientierung** und
方向和
- die **Kohärenz**
连贯性

Im **Unterschied zur Richtung**, die im Bereich von Null bis 360◦ definiert ist, beschreibt die Orientierung eine **Vorzugsrichtung** ohne zwischen positiven und negativen Ableitungen zu unterscheiden
与在0到360°范围内定义的方向相反，方向​​描述了一个优选的方向，而没有区分正负导数

Man möchte wissen, ob eine **lokale Struktur** eine gewisse Vorzugsrichtung bei den einzelnen Gradienten aufweist und wie stark diese Vorzugsrichtung ausgeprägt ist.
人们想知道一个地方结构是否具有某个优先方向的个人灰色，以及这个优先方向有多强烈

#### 9.8.1.2 Definition

#### 9.8.1.3 Orientierung

#### 9.8.1.4 Kohärenz

#### 9.8.1.5 Eckpunkt (corner feature)

### 9.8.2 Histogramme

Eine **weitere Möglichkeit** die Struktur einer Bildregion zu beschreiben bieten **Histogramme von Strukturmerkmalen**
描述图片区域结构的另一种方式是通过结构特征的直方图

Der einfachste Deskriptor dieser Art ist das sogenannte *Histogramm of Gradients (HoG)*
这种最简单的描述符是所谓的梯度直方图（HoG）

Dazu wird der zu beschreibende Bildausschnitt in zusammenhängende Zellen aufgeteilt und für jede Zelle ein mit der Gradientenstärke gewichtetes Histogramm über eine bestimmte Anzahl an Bins unterschiedlicher Kantenorientierung erzeugt
为此目的，将要描述的图像部分划分为连续的单元格，并且在具有不同边缘方向的特定数量的区间上为每个单元格生成用梯度强度加权的直方图。

Jedes dieser Histogramme kann zusätzlich über eine Vektornorm normiert werden
这些直方图中的每一个还可以通过矢量标准进行标准化

Alle Histogramme in einem Vektor zusammengehängt ergeben dann den **HoG-Deskriptor**.
矢量中的所有直方图都是HoG描述符的结果

#### 9.8.2.1 HoG

**Vorteil**: HoGs sind zu einem gewissen Grad **invariant** gegenüber *Größenskalierungen und Helligkeitsschwankungen*
优点：HoG在某种程度上对尺寸缩放和亮度变化不变

**Nachteil**: Die *örtliche Verteilung* geht nicht komplett verloren, **reduziert** sich aber auf die *Auflösung der Zellen*.
缺点：局部分布不会完全丢失，但会降低到细胞的分辨率

![Alt text](Figures\Folien_9_16.png)
