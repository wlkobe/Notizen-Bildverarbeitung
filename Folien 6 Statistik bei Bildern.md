<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 6 Statistik bei Bildern](#folien-6-statistik-bei-bildern)
	- [6.1 Motivation](#61-motivation)
		- [6.1.1 Statistik in natürlichen Bildern](#611-statistik-in-natürlichen-bildern)
	- [6.2 Zufallsvariablen](#62-zufallsvariablen)
		- [6.2.1 Wahrscheinlichkeitsdichtefunktion](#621-wahrscheinlichkeitsdichtefunktion)
		- [6.2.2 Histogramm](#622-histogramm)
			- [6.2.2.1 Beispiel](#6221-beispiel)
		- [6.2.3 Verteilungsfunktion](#623-verteilungsfunktion)
		- [6.2.4 Kenngrößen](#624-kenngröen)
			- [6.2.4.1 Erwartungswert](#6241-erwartungswert)
			- [6.2.4.2 Varianz](#6242-varianz)
			- [6.2.4.3 Zentrale Momente](#6243-zentrale-momente)
	- [6.3 Funktionen von Zufallsvariablen](#63-funktionen-von-zufallsvariablen)
		- [6.3.1 Herleitung](#631-herleitung)
		- [6.3.2 Beispiel](#632-beispiel)
	- [6.4 Multiple Zufallsvariablen](#64-multiple-zufallsvariablen)
		- [6.4.1 Eigenschaften](#641-eigenschaften)
		- [6.4.2 Kovarianzmatrix](#642-kovarianzmatrix)
		- [6.4.3 Kovarianz](#643-kovarianz)
	- [6.5 RGB Barbbild](#65-rgb-barbbild)
		- [6.5.1 Korrelationen](#651-korrelationen)
		- [6.5.2 Korrelationskoeffizienten](#652-korrelationskoeffizienten)
		- [6.5.3 Vertauschen der Kanäle](#653-vertauschen-der-kanäle)
	- [6.6 Verteilungsfunktionen](#66-verteilungsfunktionen)
		- [6.6.1 Poissonverteilung](#661-poissonverteilung)
		- [6.6.2 Gaußvertielung](#662-gauvertielung)
		- [6.6.3 Zentraler Grenzwertsatz](#663-zentraler-grenzwertsatz)
		- [6.6.4 Multivariate Gaußverteilung](#664-multivariate-gauverteilung)
		- [6.6.5 Hauptachsentransformation](#665-hauptachsentransformation)
			- [6.6.5.1 Beispiel](#6651-beispiel)
				- [6.6.5.1.1 Whitening von Bildern](#66511-whitening-von-bildern)
		- [6.6.6 Binomialverteilung](#666-binomialverteilung)
		- [6.6.7 Studentische t-Verteilung](#667-studentische-t-verteilung)
		- [6.6.8 Gaußsche Mischverteilung](#668-gausche-mischverteilung)
	- [6.7 Stochastische Prozesse und Felder](#67-stochastische-prozesse-und-felder)
		- [6.7.1 Definition](#671-definition)
		- [6.7.2 Problem](#672-problem)
		- [6.7.3 Annahmen](#673-annahmen)
	- [6.8 Korrelationsanalyse](#68-korrelationsanalyse)
		- [6.8.1 Autokorrelationsfunktion](#681-autokorrelationsfunktion)
		- [6.8.2 Normierte Autokovarianzfunktion](#682-normierte-autokovarianzfunktion)
		- [6.8.3 Beispiel Autokorrelationsfunktion](#683-beispiel-autokorrelationsfunktion)
		- [6.8.4 Kreuzkorrelationsfunktion](#684-kreuzkorrelationsfunktion)
		- [6.8.5 Normierte Kreuzkovarianzfunktion](#685-normierte-kreuzkovarianzfunktion)
		- [6.8.6 Lokale Kreuzkorrelationsfunktion](#686-lokale-kreuzkorrelationsfunktion)
		- [6.8.7 Vergleich](#687-vergleich)

<!-- /TOC -->

# Folien 6 Statistik bei Bildern

---

## 6.1 Motivation

Es gibt im wesentlichen **zwei Gründe**, warum die Statistik interessant für die Bildverarbeitung ist:
统计数据对于图像处理有趣的原因主要有两个：
- Die Bildaufnahme ist **Störungen** unterworfen
图像采集受到干扰
- „Natürliche Bilder“ weisen **charakteristische raumzeitliche Abhängigkeiten** zwischen visuellen Merkmalen auf
“自然图像”具有视觉特征之间的特征时空依赖性
  - ausgeprägte Strukturen
明显的结构
  - gemeinsame statistische Eigenschaften.
常见的统计特性

### 6.1.1 Statistik in natürlichen Bildern

- **Grauwertstatistik**: Huang & Mumford 1999 (Statistics of Natural Images and Models)
- **2 × 2 Musterstatistik**: Lee, Mumford & Huang 2001 (Occlusion Models for Natural Images)
- **Bewegungsstatistik**: Liu, Freeman, Adelson, Weiss 2008 (Human-Assisted Motion Annotation)

---

## 6.2 Zufallsvariablen

### 6.2.1 Wahrscheinlichkeitsdichtefunktion

Der **Grauwert** G eines Bildes an einem bestimmten Pixel ist *ein Maß für die gemessene Bestrahlungsstärke E*
特定像素处的图像的灰度值G是测量的辐照度E的量度

Da der **Messprozess** *statistischen Schwankungen* unterworfen ist, muss die Bestrahlungsstärke bzw der Grauwert eines jeden Pixel als **Zufallsvariable mit** einer bestimmten kontinuierlichen p(x = E) bzw diskreten p(X = G) **Wahrscheinlichkeitsdichtefunktion (pdf)** angenommen werden
由于测量过程受统计波动的影响，每个像素的辐照度或灰度值必须假定为具有一定连续p（x = E）或离散p（X = G）概率密度函数（pdf）的随机变量

Jede pdf erfüllt *zwei Bedingungen*:
每个pdf都符合两个条件：

![Alt text](Figures\Folien_6_1.png)

### 6.2.2 Histogramm

Wenn man annimmt, dass die *Zufallsvariable X unabhängig vom Bildort* ist, dann kann die *pdf durch* ein **Histogramm** angenähert werden
假设随机变量X独立于图像位置，则可以通过直方图来近似pdf

Ein **Histogramm** entspricht der *Häufigkeitsverteilung der Variablen* z.B der Grauwerte in einem Bild:
直方图对应于变量的频率分布，例如图像中的灰度值：

p(X) ≈ hN(X) = Nx/N

![Alt text](Figures\Folien_6_2.png)

wobei **Nx** der *Anzahl der jeweiligen Variable X* z.B des jeweiligen Grauwertes G im Bild entspricht. Es gilt:
其中NX对应于相应变量X的数量，例如图像中的相应灰度值G.

lim N-inf hN(X) = p(X)

#### 6.2.2.1 Beispiel

![Alt text](Figures\Folien_6_3.png)
![Alt text](Figures\Folien_6_4.png)

### 6.2.3 Verteilungsfunktion

![Alt text](Figures\Folien_6_5.png)

Die **Wahrscheinlichkeit P(x)**, dass z.B die Beleuchtungsstärke E im Intervall von ]−inf; E] liegt wird **Verteilungsfunktion** genannt und entspricht der **Stammfunktion der pdf**
概率P（x），例如，间隔中的照度E，-inf; E]称为分布函数，对应于pdf的父函数

Die **Verteilungsfunktion** wächst monoton von 0 nach 1 an und es gilt:
分布函数从0单调增加到1，以下情况适用：

P'(x) = dP(x)/dx = p(x)

### 6.2.4 Kenngrößen

#### 6.2.4.1 Erwartungswert

Der **Mittelwert µx** bzw. der **Erwartungswert E{x}** ist definiert als:

![Alt text](Figures\Folien_6_6.png)

Der **Erwartungswert** kann durch *N-malige Messung und Mittelung* gemessener Werte *Xi* ohne Wissen der pdf approximiert werden (empirischer Mittelwert µ):
期望值可以通过测量N次并且在不知道pdf（经验平均μ）的情况下平均测量值Xi来近似：

![Alt text](Figures\Folien_6_7.png)

Z.B kann der **Erwartungswert des Grauwertes** eines Bildes durch die Summe aller Grauwerte geteilt durch die Grauwertanzahl approximiert werden.
例如，图像的灰度值的期望值可以通过所有灰度值之和除以灰度值数来近似

#### 6.2.4.2 Varianz

Die **Varianz** beschreibt die *Abweichung vom Mittelwert µx*:

![Alt text](Figures\Folien_6_8.png)

Auch die Varianz kann **durch** *N-malige Messung* ohne Wissen der pdf approximiert werden. Es ergibt sich die sogenannte **Stichprobenvarianz**:

![Alt text](Figures\Folien_6_9.png)

#### 6.2.4.3 Zentrale Momente

Weitere Eigenschaften der pdf von Zufallsvariablen werden durch **zentrale Momente n-ter Ordnung** ermittelt:

![Alt text](Figures\Folien_6_10.png)

Das dritte Moment, auch **Schiefheit** genannt, ist z.B ein Maß für die *Asymmetrie der pdf*
第三个时刻，也称为歪曲，例如衡量pdf的不对称性

Die **Kurtosis κ** bzw **Wölbung einer pdf** ist durch das *normierte vierte zentrale Moment* gegeben, wobei der **Normierungsfaktor σ4** der vierten Potenz der Standardabweichung entspricht:
pdf的峰度κ或跳跃由归一化的第四中心力矩给出，其中归一化因子σ4对应于标准偏差的四次幂：

![Alt text](Figures\Folien_6_11.png)

---

## 6.3 Funktionen von Zufallsvariablen

![Alt text](Figures\Folien_6_12.png)

Sogenannte **Punktoperatoren** dienen unter anderem dazu die Grauwerte in einem Bild nach *bestimmten Kriterien zu verändern*, so dass z.B der Bildkontrast verbessert wird
除此之外，所谓的点运算符用于根据特定标准改变图像中的灰度值，从而例如改善图像对比度

Das hat **nicht nur** *Auswirkungen auf die Grauwerte* an sich, **sondern auch** auf die *Bildstatistik*
这不仅影响灰度值本身，还影响图像统计

Wenn die **Grauwerte G** nach einem bestimmten funktionalen Zusammenhang G' = g(G) zu anderen Grauwerten G' verändert werden, dann *ändert sich auch die Grauwertverteilung* P(G) -- P(G0) bzw das *Histogramm*.
如果根据某个函数关系G'= g（G）将灰度值G改变为其他灰度值G'，则灰度值分布P（G）-P（G0）或直方图也改变

### 6.3.1 Herleitung

Wird eine **pdf p(x)** in eine **pdf p(y)** über eine *Kennlinie y = g(x)* überführt, dann gilt für alle i = 1, ... n:
如果pdf p（x）在特征y = g（x）上转换为pdf p（y），那么对于所有i = 1，...n:

![Alt text](Figures\Folien_6_13.png)

Für kleine δy kann man näherungsweise annehmen, dass gilt:
对于小的δy，可以大致假设以下适用：

![Alt text](Figures\Folien_6_14.png)

Ist y = g(x) differenzierbar, dann ergibt sich:

![Alt text](Figures\Folien_6_15.png)

### 6.3.2 Beispiel

Beispiel einer **gaußverteilten Zufallsvariable**, die über eine *nichtlineare monoton steigende Funktion abgebildet wird*
高斯分布随机变量的示例，其映射在非线性单调递增函数上

- bleibt unimodal
仍然是单峰的
- aber nicht mehr gaußverteilt
但不再是高​​斯分布式的

**Vorkommen in der Bildverarbeitung** z.B beim Messen der Entfernung über Disparitäten von Bildpunktkoordinaten unterschiedlicher Kameras aus unterschiedlichen Blickwinkeln.
图像处理中的出现，例如，测量不同相机的像素坐标从不同角度的差异的距离 ???

![Alt text](Figures\Folien_6_16.png)

Positionierung im Raum über den räumlichen Rückwärtsschnitt
通过空间向后切割在空间中定位

---

## 6.4 Multiple Zufallsvariablen

### 6.4.1 Eigenschaften

**Multiple Zufallsvariablen** x = (x1, x2, , xN)T besitzen eine *gemeinsame pdf p(x) mit den Eigenschaften p(x) ≥ 0 und Px p(x) = 1*, wobei die einzelnen Zufallsvariablen ZV im Allgemeinen *korreliert und statistisch voneinander abhängig* sind.
多个随机变量x =（x1，x2，xN）T具有共同的pdf p（x），其属性为p（x）≥0且Px p（x）= 1，其中各个随机变量ZV通常是相关的且在统计上不同依赖

![Alt text](Figures\Folien_6_17.png)

**Statistische Unabhängigkeit** schließt immer *Unkorreliertheit* mit ein
统计独立性总是包括不相关
Der Umkehrschluss gilt jedoch nicht.
反之则不然

### 6.4.2 Kovarianzmatrix

Gemeinsame **zentrale Momente höherer Ordnung** bieten die **Möglichkeit** *statistische Abhängigkeiten zwischen den Zufallsvariablen Xn eines Vektors X* zu bewerten
高阶的共同中心矩提供了评估向量X的随机变量Xn之间的统计依赖性的可能性

Hierbei ist das wichtigste Instrument die **Kovarianzmatrix Σ**.
这里，最重要的工具是协方差矩阵Σ

![Alt text](Figures\Folien_6_18.png)

Diese **Matrix** ist *symmetrisch und positiv semidefinit (alle Eigenwerte ≥ Null)*
该矩阵是对称的和半正的（所有特征值≥零）

Die **Varianzen σ2i** sind stets positiv, die **Kovarianzen σij** können positiv oder negativ sein (korreliert bzw antikorreliert)
方差σ2i总是正的，协方差σij可以是正的或负的（相关的或反相关的）

Falls die **Kovarianzen Null** sind, dann sind die Variablen *statistisch unabhängig* und die *Kovarianzmatrix diagonal*.
如果协方差为零，则变量在统计上是独立的，并且协方差矩阵是对角线的

### 6.4.3 Kovarianz

Da die **Kovarianzmatrix** *symmetrisch* ist, kann *immer ein Koordinatensystem, also eine Linearkombination der Zufallsvariablen, gefunden werden*, in dem die **Kovarianzmatrix** diagonal und damit die **Zufallsvariablen** unkorreliert sind
由于协方差矩阵是对称的，因此总是可以找到坐标系，即随机变量的线性组合，其中协方差矩阵是对角线的，因此随机变量是不相关的

Die **Kovarianz von zwei Zufallsvariablen** gibt an in welchem Maß die Fluktuationen zueinander in Beziehung stehen.
两个随机变量的协方差表明波动彼此相关的程度

![Alt text](Figures\Folien_6_19.png)

Der **Korrelationskoeffizient** ist die *mit den Varianzen normierte Kovarianz*:
相关系数是用方差归一化的协方差：

![Alt text](Figures\Folien_6_20.png)

**Unkorrelierte Zufallsvariablen** erfüllen folgende Beziehungen:
不相关的随机变量满足以下关系：

![Alt text](Figures\Folien_6_21.png)

---

## 6.5 RGB Barbbild

### 6.5.1 Korrelationen

![Alt text](Figures\Folien_6_22.png)

### 6.5.2 Korrelationskoeffizienten

![Alt text](Figures\Folien_6_23.png)

### 6.5.3 Vertauschen der Kanäle

![Alt text](Figures\Folien_6_24.png)

---

## 6.6 Verteilungsfunktionen

### 6.6.1 Poissonverteilung

**Rauschmodell für Bildsensoren**:
图像传感器的噪声模型：

Der von einem *einzelnen Sensorelement aufgenommene mittlere Strom von Ladungsträgern λ* ist **proportional** zur *Bestrahlungsstärke E*
由单个传感器元件吸收的电荷载流子λ的平均电流与照射强度E成比例

Da der **Photonenstrom statistischen Schwankungen** unterworfen ist, werden bei *jeder Aufnahme mit einer festen Belichtungszeit ∆t unterschiedliche Anzahlen N von Elektronen gesammelt*
由于光子电流经历统计波动，因此在每次发射时以固定的曝光时间Δt收集不同数量的N个电子

Die **diskrete Verteilung** der Elektronenanzahl N ist **poissonverteilt**:
电子数N的离散分布是泊松分布的：

![Alt text](Figures\Folien_6_25.png)

Der **Mittelwert und die Varianz** sind abhängig von λ, also auch von der Bestrahlungsstärke, und identisch:
平均值和方差取决于λ，因此也取决于照射强度，并且相同：a

![Alt text](Figures\Folien_6_26.png)

![Alt text](Figures\Folien_6_27.png)

Schon für **moderate Bestrahlungsstärken** approximiert folgende *Gaußverteilung N (N|λ∆t, λ∆t)* die *Poissonverteilung* fast *perfekt*
即使对于中等辐照度，以下高斯分布N（NjλΔt，λΔt）几乎完全近似泊松分布

Selbst ein **idealer Bildsensor** ohne elektronisches Rauschen weist **aufgrund** des Photonenrauschens bei 10000 Elektronen (durch Absorbtion von Photonen) eine **Standardabweichung** von etwa 100 Elektronen also 1% auf.
即使没有电子噪声的理想图像传感器也具有约100个电子的标准偏差，这是由于10000个电子（通过光子的吸收）的光子噪声，即1％

### 6.6.2 Gaußvertielung

![Alt text](Figures\Folien_6_29.png)

Bei der **Modellierung von Rauschen und Nachbarschaftsbeziehungen**, sowie beim Filtern spielt **sowohl** die eindimensionale **als auch** die multivariate *Gaußverteilung die wichtigste Rolle*
在噪声和邻域关系以及滤波的建模中，一维和多元高斯分布都起着最重要的作用

Die eindimensionale Normalverteilung bzw Gaußverteilung N (x|µ, σ2) über der Zufallsvariablen x mit dem Mittelwert µ und der Varianz σ2 (bzw der Präzision β = 1/σ2) hat die Form:
随机变量x上的一维正态分布或高斯分布N（x |μ，σ2）具有均值μ和方差σ2（或精度β= 1 /σ2）具有以下形式：

![Alt text](Figures\Folien_6_28.png)

### 6.6.3 Zentraler Grenzwertsatz

![Alt text](Figures\Folien_6_30.png)
![Alt text](Figures\Folien_6_31.png)
![Alt text](Figures\Folien_6_32.png)

Der **zentrale Grenzwertsatz** besagt im Wesentlichen, dass die *Summe einer großen Zahl von unabhängigen, identisch verteilten Zufallsvariablen annähernd normalverteilt ist*
本质上，中心极限定理表示大量独立的，相同分布的随机变量的总和大致正态分布

Betrachtet man beispielsweise **N gleichverteilte Zufallsvariablen (X1, , XN)**, dann tendiert die Verteilung der Summe dieser Zufallsvariablen Y = 1/N Sigma (i=1 Xi) mit steigendem N *immer mehr zu einer Gaußverteilung*
考虑到，例如，N个均匀分布的随机变量（X1，XN），这些随机变量之和的分布Y = 1/N Sigma (i=1 Xi)随着N的增加趋于越来越高的高斯分布

Aus dem **zentralen Grenzwertsatz** folgt auch, dass *kaskadierte Faltungen* besonders bei *glatten Faltungskernen* schon bei einer geringen Anzahl an Faltungen (N > 5) durch eine einzige Faltung *mit einem Gaußkern* approximiert werden kann.
从中心极限定理得出，级联卷积可以通过单个卷积与高斯核近似，即使在平滑卷积核的情况下，即使具有少量卷积（N> 5）

### 6.6.4 Multivariate Gaußverteilung

![Alt text](Figures\Folien_6_34.png)

Die **multivariate Gaußverteilung N (x|µ,Σ)** über einer *multiplen D-dimensionalen Zufallsvariablen x* mit den Mittelwerten µ und der Kovarianzmatrix Σ bzw der Präzisionsmatrix Λ = Σ−1 hat die Form:
具有平均值μ和协方差矩阵Σ或精度矩阵Λ=Σ-1的多D维随机变量x上的多元高斯分布N（x |μ，Σ）具有以下形式：

![Alt text](Figures\Folien_6_33.png)

wobei *|Σ| die Determinante der Kovarianzmatrix* bezeichnet
其中|Σ|表示协方差矩阵的行列式

Der Exponent beinhaltet die sogenannte **Mahalanobis Distanz** ∆2 = (x−µ)TΛ(x−µ) die der Euklidischen Distanz entspricht, wenn die Kovarianzmatrix der Einheitsmatrix entspricht Λ = I.
如果协方差矩阵对应于单位矩阵Λ= I，则指数包含所谓的马哈拉诺比斯距离Δ2=（x-μ）TΛ（x-μ），其对应于欧几里德距离

![Alt text](Figures\Folien_6_35.png)

Die **Kovarianzmatrix** läßt sich immer in eine *gewichtete Summe von folgenden separablen Matrizen zerlegen*:
协方差矩阵总是可以分解为以下可分离矩阵的加权和

![Alt text](Figures\Folien_6_36.png)

Die **Vektoren ui** entsprechen den *Eigenvektoren von Σ* und bilden eine *Orthonormalbasis*
矢量ui对应于Σ的特征向量并形成标准正交基

Die **Gewichte λi** entsprechen den *Eigenwerten von Σ*.
权重λi对应于Σ的特征值

**Vorherige Zerlegung kann auch folgendermaßen geschrieben werden:**
以前的分解也可以写成如下：

![Alt text](Figures\Folien_6_37.png)

wobei S = diag(λi) , i = 1,  , D
其中S = diag（λi），i = 1，D

Die **Zeilenvektoren u> i** erzeugen die *Rotationsmatix U* und die **Eigenwerte λi** die *Diagonalmatrix S*
线矢量u> i生成旋转矩阵U，特征值λi生成对角矩阵S.

Damit kann die **Mahalanobis Distanz** auch in einem um den Vektor µ verschobenen und um U rotierten Koordinatensystem y = U(x − µ) dargestellt werden:
因此，马哈拉诺比斯距离也可以用坐标系y = U（x-μ）表示，该坐标系偏移了矢量μ并绕U旋转：
∆2 = yTS−1y

Damit entspricht jede **multivariate Gaußverteilung** im Koordinatensystem x einer *mittelwertfreien multivariaten Normalverteilung* im transformierten Koordinatensystem y mit den Hauptachsen der Verteilung entlang der Koordinatenachsen
因此，坐标系x中的每个多元高斯分布对应于变换坐标系y中的无平均多元正态分布，其中沿着坐标轴的分布的主轴

![Alt text](Figures\Folien_6_38.png)

wobei die **multivariate Normalverteilung** *im transformierten Koordinatensystem* einem Produkt von D eindimensionalen Normalverteilungen entspricht.
其中变换坐标系中的多元正态分布对应于D个一维正态分布的乘积


**Produkt univariater Normalverteilungen**:
单变量正态分布的乘积：

![Alt text](Figures\Folien_6_39.png)

Damit gibt es **drei Kategorien** von multivariaten Gaußverteilungen:
有三类多元高斯分布：
- a) allgemeine anisotrope Σ,
a）一般各向异性Σ，
- b) separierbare anisotrope Σ = diag(σi2),
b）各向异性separiqueryΣ= diag（σi2），
- c) separierbare isotrope Σ = σ2I
c）separierbare各向同性Σ=σ2I

![Alt text](Figures\Folien_6_40.png)

### 6.6.5 Hauptachsentransformation

![Alt text](Figures\Folien_6_41.png)

**Hauptachsentransformation** bezeichnet die Transformation einer *multivariaten Normalverteilung N (x|µ,Σ)*, so dass die Kovarianzmatrix zu einer Diagonalmatrix wird
主轴变换是指多元正态分布N（x |μ，Σ）的变换，因此协方差矩阵成为对角矩阵

Diese Transformation wird **Whitening** genannt, **wenn** die *diagonale Kovarianzmatrix zusätzlich so skaliert* wird, dass sie der *Einheitsmatrix entspricht Σ = I* und damit das **Spektrum der Eigenvektoren** (Menge der unterschiedlichen Eigenvektoren) **uniform** (λi = 1 , i) ist:
如果对角协方差矩阵被另外缩放以对应于单位矩阵Σ= I并且因此特征向量的光谱（不同特征向量的集合）是均匀的（λi= 1,i），则该变换被称为白化：

![Alt text](Figures\Folien_6_42.png)

**Nach der Transformation** sind die **Zufallsvariablen** *unkorreliert* und weil sie normalverteilt sind damit auch *unabhängig*
转换后，事故变量是不相关的，因为它们是正态分布的，所以它们也是独立的

Durch die **Projektion von x auf einen beliebigen Vektor a** erhält man die *Verteilung N (y|a>µ, aTΣa) entlang des eindimensionalen Unterraumes y*
通过将x投影到任意向量a上，我们得到沿着一维子空间y的分布N（y | a>μ，aTΣa）

Der Name **Whitening** kommt daher, weil *N (0, I)-verteilte Fehler als Gaußsches Weißes Rauschen bzw Gaussian White Noise* bezeichnet werden.
名称白化来自于N（0，I）分布的误差被称为高斯白噪声或高斯白噪声的事实

#### 6.6.5.1 Beispiel

##### 6.6.5.1.1 Whitening von Bildern

**Whitening** als *Vorverarbeitung* von Bildern über Hauptkomponentenanalyse (PCA)
通过主成分分析（PCA）将白化作为图像的预处理

![Alt text](Figures\Folien_6_43.png)
![Alt text](Figures\Folien_6_44.png)

### 6.6.6 Binomialverteilung

![Alt text](Figures\Folien_6_47.png)
![Alt text](Figures\Folien_6_48.png)

Das *diskrete Analogon zur Normalverteilung N (x|µ, σ2)* ist die **Binomialverteilung**
与正态分布N（x |μ，σ2）的离散模拟是二项分布

![Alt text](Figures\Folien_6_45.png)

Sie beschreibt die Wahrscheinlichkeit der Auftrittsanzahl m eines Zustandswertes X = 1 einer binären Zustandsvariablen X = [0, 1] bei N Wiederholungen des Zufallsexperiments
它描述了随机性实验的N次重复的二元状态变量X = [0,1]的状态值X = 1的出现次数m的概率

Der **Mittelwert** und die **Varianz** ergeben sich zu:
均值和方差是：

![Alt text](Figures\Folien_6_46.png)

### 6.6.7 Studentische t-Verteilung

![Alt text](Figures\Folien_6_50.png)
![Alt text](Figures\Folien_6_51.png)

Die **Studentsche t-Verteilung S(x|µ, λ, ν)** ist besonders dazu geeignet die *Statistik von Datensätzen robust gegenüber Ausreißern zu beschreiben* und liefert in vielen Fällen ein besseres Modell für typische Bildstatistiken als die Gaußverteilung.
学生的t分布S（x |μ，λ，ν）特别适用于描述对异常值具有鲁棒性的数据集的统计量，并且在许多情况下提供了比高斯分布更好的典型图像统计模型

![Alt text](Figures\Folien_6_49.png)

Die **Studentsche t-Verteilung** entspricht einer Gaußschen Mischverteilung bestehend aus unendlich vielen Gaußverteilungen mit identischen Mittelwerten und allen möglichen Varianzen
学生的t分布对应于高斯混合分布，由无数个高斯分布组成，具有相同的平均值和所有可能的方差

![Alt text](Figures\Folien_6_52.png)

wobei die Gewichte der Gammaverteilung G(τ|λ, ν) = 1/Γ(λ)νλτ(λ−1)e−ντ entsprechen
其中伽马分布的权重对应于G（τ|λ，ν）= 1 /Γ（λ）νλτ（λ-1）e-τ
Für ν-inf ergibt sich wieder eine Gaußverteilung
对于ν-inf，还有高斯分布

![Alt text](Figures\Folien_6_53.png)

### 6.6.8 Gaußsche Mischverteilung

![Alt text](Figures\Folien_6_55.png)
![Alt text](Figures\Folien_6_56.png)

Es gibt **einige Fälle** in der Bildverarbeitung (z.B Korrespondenzverteilungen), wo eine *unimodale Verteilung nicht ausreicht, um den statistischen Zusammenhang ausreichend zu modellieren*
在图像处理（例如，对应分布）中存在一些情况，其中单峰分布不足以充分地模拟统计关系

Eine Möglichkeit **multimodale Verteilungen** zu modellieren bieten **Gaußsche Mischverteilungen**
高斯混合分布提供了建模多模态分布的一种可能性

![Alt text](Figures\Folien_6_54.png)

wobei die **Mischkoeffizienten πk** der einzelnen Gaußkomponenten selbst wieder eine *diskrete Verteilung* bilden
其中各个高斯分量本身的混合系数πk再次形成离散分布

---

## 6.7 Stochastische Prozesse und Felder

### 6.7.1 Definition

**Stochastische Prozesse bzw stochastische Felder** werden dazu benutzt, um die *zeitlichen (Prozess) und räumlichen (Feld) Beziehungen* zwischen den *visuellen Zuständen der einzelnen Bildpunkte* zu berücksichtigen
随机过程或随机场用于解释各个像素的视觉状态之间的时间（过程）和空间（场）关系

Hierbei wird ein *komplettes Bild* bzw eine *Bildsequenz* oder eine *zeitliche Folge eines Bildmerkmals* als eine **statistische Größe** betrachtet
在这种情况下，完整图像或图像序列或图像特征的时间序列被视为统计变量

Die *Grauwerte eines Bildes mit M ×N Pixel* können z.B mit einem *stochastischen Feld*, also einer **Matrix aus M ×N Zufallsvariablen** beschrieben werden.
具有M×N像素的图像的灰度值可以例如用随机场，即M×N个随机变量的矩阵来描述

### 6.7.2 Problem

Selbst wenn nur der Zusammenhang der Grauwerte G im Bild mit einem stochastischen Feld modelliert werden soll, dann ergeben sich bei **Q Quantisierungsstufen QMN verschiedene Zustände**, die die Zufallsvariable G annehmen kann
即使仅用随机场对图像中的灰度值G的关系进行建模，在Q量化级QMN处出现不同的状态，随机变量G可以假设

Das bedeutet, man muss die pdf p(G) = p(G1,1, G1,2,  , GM,N) dieses **hochdimensionalen Zustandes** modellieren, um **statistische Kenngrößen** wie beispielsweise den Erwartungswert auszurechnen
这意味着必须对这个高维状态的pdf p（G）= p（G1,1，G1,2 ,, GM，N）进行建模，以便计算统计参数，例如期望值

![Alt text](Figures\Folien_6_57.png)

Das ist **aufgrund** der *hohen Dimension* praktisch nicht mehr möglich
由于高尺寸，这几乎是不可能的

**Deswegen** müssen *geeignete Approximationen* eingeführt werden, um das Auswerten der *hochdimensionalen Zufallsvariablen rechenbar* zu machen.
因此，必须引入适当的近似值以使高维随机变量的计算可计算

### 6.7.3 Annahmen

Anstatt **statistische Kenngrößen**, wie den Mittelwert oder die Varianz, exakt zu berechnen, können sie durch sogenannte **Schar- oder Ensemblekenngrößen** ersetzt werden
它们不是精确地计算诸如均值或方差的统计参数，而是可以用所谓的族或集合参数代替

Damit bleiben die **Kenngrößen** aber immer noch *zeit- und ortsabhängig*
但是，参数仍然取决于时间和位置

Folgende **zusätzliche Annahmen** werden normalerweise in der Praxis eingeführt:
在实践中通常会引入以下附加假设：

- **Ergodizität**: **Scharmittelwerte** entsprechen den Zeit- bzw Ortsmittelwerten (eine Realisierung/Signal ist ausreichend)
锐利的平均值对应于时间或平均值（一个实现/信号就足够了）
- **Stationarität**: **Statistische Eigenschaften** eines stochastischen Prozesses sind *invariant gegenüber Verschiebungen in der Zeit*
平稳：随机过程的统计特性对于时间变化是不变的
- **Homogenität**: **Statistische Eigenschaften** eines stochastischen Feldes sind *invariant gegenüber Verschiebungen im Bildort*
同质性：随机场的统计特性对于图像位置的变化是不变的

Unter diesen Annahmen werden **Mittelwerte und Varianzen** *orts- und zeitunabhängig* und **Korrelationsfunktionen** hängen **nur** noch *von Abständen in Ort und Zeit ab*.
在这些假设下，平均值和方差变得与时间和地点无关，相关函数仅取决于地点和时间的距离

---

## 6.8 Korrelationsanalyse

### 6.8.1 Autokorrelationsfunktion

Um *Grauwerte an unterschiedlichen Positionen im Bild oder der Zeit in Beziehung zu setzen* werden unter anderem **Korrelationsfunktionen** benutzt
相关函数尤其用于将图像中或时间中的不同位置处的灰度值相关联

**Autokorrelationsfunktion**: Messung der Selbstähnlichkeit eines Signals.
测量信号的自相似性

![Alt text](Figures\Folien_6_58.png)

Mittelwertfreie Messung der Selbstähnlichkeit eines Signals
对信号的自相似性的平均无值测量

Ortsdiskret, ergodisch & homogen, mit Mittelwert
空间离散，遍历和均匀，具有均值
![Alt text](Figures\Folien_6_59.png)

![Alt text](Figures\Folien_6_60.png)

### 6.8.2 Normierte Autokovarianzfunktion

Mittelwertfreie und varianznormierte Messung der Selbstähnlichkeit eines Signals
信号自相似性的均值正态和方差归一化测量

Ortsdiskret, ergodisch & homogen:
局部离散，遍历和同质：

![Alt text](Figures\Folien_6_61.png)

### 6.8.3 Beispiel Autokorrelationsfunktion

![Alt text](Figures\Folien_6_62.png)

### 6.8.4 Kreuzkorrelationsfunktion

Das Vergleichen von zwei unterschiedlichen Bildern an unterschiedlichen Positionen in den Bildern oder entlang der Zeit wird auch Matching oder Korrespondenzanalyse genannt
比较图像中不同位置或沿时间的两个不同图像也称为匹配或对应分析

Kreuzkorrelationsfunktion: Messung der Ähnlichkeit zweier Signale.
互相关函数：测量两个信号的相似性

![Alt text](Figures\Folien_6_63.png)

**Mittelwertfreie Messung** der **Ähnlichkeit** zwischen zwei Signalen.

Ortsdiskret, ergodisch & homogen:

![Alt text](Figures\Folien_6_64.png)

### 6.8.5 Normierte Kreuzkovarianzfunktion

**Mittelwertfreie und varianznormierte Messung** der **Ähnlichkeit** zweier Signale.

Ortsdiskret, ergodisch & homogen:

![Alt text](Figures\Folien_6_65.png)

![Alt text](Figures\Folien_6_66.png)

### 6.8.6 Lokale Kreuzkorrelationsfunktion

Bei Kenntnis eines Prototypen eines Musters bzw Templates T, liefert das Maximum der **lokalen Kreuzkorrelationsfunktion** zwischen dem **Muster T** der Größe K × L und einem **Bild G** der Größe M × N den Ort des *wahrscheinlichsten Auftretens des Musters im Bild*, wobei gewöhnlich gilt:
在知道模板T的原型的情况下，尺寸为K×L的图案T与尺寸为M×N的图像G之间的局部互相关函数的最大值给出了图像中可能出现的图案的位置，其中通常

 K × L << M × N

- **Anwendung**: Erkennung von Mustern wie z.B Druckbuchstaben durch Schwellwertoperation auf der Kreuzkorrelation
应用：通过对互相关的阈值操作识别诸如块字母之类的模式
- **Vorteil**: Theoretisch optimale Lösung
优点：理论上最优的解决方案
- **Nachteil**: Rotations- und Skalierungsvariant, hoher Rechenaufwand (eine Faltung pro Prototyp).
缺点：旋转和缩放变量，高计算量（每个原型一个卷积）

**Lokale Korrelationen** sind *orts- bzw zeitabhängig*, da örtlich begrenzte Korrelationsfunktionen berechnet werden
由于计算了局部相关函数，因此局部相关性是位置或时间相关的

- Lokale Kreuzkorrelationsfunktion
局部互相关函数

![Alt text](Figures\Folien_6_67.png)

- Lokale Kreuzkovarianzfunktion
局部交叉协方差函数

![Alt text](Figures\Folien_6_68.png)

- Lokale varianznormierte Kreuzkovarianzfunktion
局部varianznormierte交叉协方差函数

![Alt text](Figures\Folien_6_69.png)

**Alternative Korrelationsmaße**, die vorwiegend z.B in der *Photogrammetrie* und der *visuellen Navigation* angewendet werden
替代相关性测量，主要用于例如摄影测量和视觉导航

- **SSD Matching** (Sum of Squared Differences)
SSD匹配（平方差的和）

![Alt text](Figures\Folien_6_70.png)

- **SAD Matching** (Sum of Absolute Differences)
SAD匹配（绝对差异的总和）

![Alt text](Figures\Folien_6_71.png)

### 6.8.7 Vergleich

![Alt text](Figures\Folien_6_72.png)

![Alt text](Figures\Folien_6_73.png)
