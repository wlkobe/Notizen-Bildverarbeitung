<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 8 Filter](#folien-8-filter)
	- [8.1 Lineare Filter](#81-lineare-filter)
		- [8.1.1 Mittelung](#811-mittelung)
			- [8.1.1.1 Gewünschte Eigenschaften](#8111-gewünschte-eigenschaften)
			- [8.1.1.2 Ideale Eigenschaften](#8112-ideale-eigenschaften)
		- [8.1.2 Rechteckfilter](#812-rechteckfilter)
			- [8.1.2.1 Eigenschaften](#8121-eigenschaften)
			- [8.1.2.2 Transferfunktion](#8122-transferfunktion)
		- [8.1.3 Binomialfilter](#813-binomialfilter)
			- [8.1.3.1 Eigenschaften](#8131-eigenschaften)
			- [8.1.3.2 Transferfunktion](#8132-transferfunktion)
			- [8.1.3.3 Vergleich](#8133-vergleich)
		- [8.1.4 Gaußfilter](#814-gaufilter)
			- [8.1.4.1 Ideale Glättung](#8141-ideale-glättung)
			- [8.1.4.2 Ableitungen](#8142-ableitungen)
				- [8.1.4.2.1 Finden lokaler Konturformen](#81421-finden-lokaler-konturformen)
		- [8.1.5 Differenzialoperatoren](#815-differenzialoperatoren)
			- [8.1.5.1 1. Ordnung](#8151-1-ordnung)
			- [8.1.5.2 2. Ordnung](#8152-2-ordnung)
		- [8.1.6 Kantendetektion](#816-kantendetektion)
			- [8.1.6.1 Möglichkeiten](#8161-möglichkeiten)
			- [8.1.6.2 Ableitungen](#8162-ableitungen)
				- [8.1.6.2.1 Ideale Eigenschaften](#81621-ideale-eigenschaften)
				- [8.1.6.2.2 Diskrete Differenzen erster Ordnung](#81622-diskrete-differenzen-erster-ordnung)
				- [8.1.6.2.3 Differenzenoperator zweiter Ordnung](#81623-differenzenoperator-zweiter-ordnung)
				- [8.1.6.2.4 Beispiele](#81624-beispiele)
				- [8.1.6.2.5 Regularisierte Kantendetektion](#81625-regularisierte-kantendetektion)
				- [8.1.6.2.6 Beispiele regularisierte 1. Ableitungen](#81626-beispiele-regularisierte-1-ableitungen)
				- [8.1.6.2.7 Beispiele regularisierter Laplaceoperator](#81627-beispiele-regularisierter-laplaceoperator)
			- [8.1.6.3 Nichtlinearitäten und Beispiel](#8163-nichtlinearitäten-und-beispiel)
	- [8.2 Nichtlineare Filter](#82-nichtlineare-filter)
		- [8.2.1 Rangordnungsfilter](#821-rangordnungsfilter)
			- [8.2.1.1 Prinzip](#8211-prinzip)
			- [8.2.1.2 Arten](#8212-arten)
		- [8.2.2 Medianfilter](#822-medianfilter)
			- [8.2.2.1 Eigenschaften](#8221-eigenschaften)
		- [8.2.3 Minimum-Filter](#823-minimum-filter)
			- [8.2.3.1 Eigenschaften](#8231-eigenschaften)
		- [8.2.4 Maximum-Filter](#824-maximum-filter)
			- [8.2.4.1 Eigenschaften](#8241-eigenschaften)
		- [8.2.5 Morphologiche Operatoren](#825-morphologiche-operatoren)
			- [8.2.5.1 Definition](#8251-definition)
			- [8.2.5.2 Beispiele](#8252-beispiele)
		- [8.2.6 Normalisierte Faltung](#826-normalisierte-faltung)
			- [8.2.6.1 Prinzip und Beispiel](#8261-prinzip-und-beispiel)
	- [8.3 Adaptive Filter](#83-adaptive-filter)
		- [8.3.1 Idee & Ziel](#831-idee-ziel)
			- [8.3.1.1 Beispiel : Anisotroper Gaußfilter](#8311-beispiel-anisotroper-gaufilter)
	- [8.4 Steuerbare Filter](#84-steuerbare-filter)
		- [8.4.1 Idee & Ziel](#841-idee-ziel)
		- [8.4.2 Entwurf](#842-entwurf)
		- [8.4.3 Beispiele](#843-beispiele)
			- [8.4.3.1 Adaptive Anisotrope Mittelung 各向异性平均](#8431-adaptive-anisotrope-mittelung-各向异性平均)
			- [8.4.3.2 Adaptive Richtungsableitung](#8432-adaptive-richtungsableitung)

<!-- /TOC -->

# Folien 8 Filter

---

## 8.1 Lineare Filter

### 8.1.1 Mittelung

#### 8.1.1.1 Gewünschte Eigenschaften

**Ziel der Mittelung** ist das *Abschwächen von feinen Strukturen* **im Ortsraum**
平均的目的是削弱物理空间中的精细结构

Das ist gleichbedeutend mit dem *Unterdrücken von hohen Wellenzahlen* **im Frequenzraum**
这与抑制频域中的高波数同义

Eine Mittelung soll also wie ein **2D Tiefpassfilter** wirken und kann damit zur Rauschunterdrückung bzw Bildglättung benutzt werden.
因此，平均值应该像2D低通滤波器一样，因此可以用于噪声抑制或图像平滑

#### 8.1.1.2 Ideale Eigenschaften

Für eine ideale Mittelung muss das Filter folgende **Eigenschaften** haben:
要获得理想的平均值，过滤器必须具有以下属性：(*Prinzip auch wichtig*)

- **Verschiebungsfreiheit**: Keine Veränderung von Objektpositionen -- symmetrische Filtermasken
运动自由：物体位置无变化 - 对称过滤面罩
- **Erhaltung des Mittelwerts**: Keine Veränderung der Helligkeit -- Summe aller Koeffizienten der Maske gleich eins
保存均值：亮度无变化 - 掩模的所有系数之和等于1
- **Glättungseigenschaft**: Feinere Strukturen werden stärker abgeschwächt als gröbere -- monotone Abnahme der Transferfunktion
平滑性：较细的结构比较粗糙的结构衰减更强 - 单调的传递函数减少
- **Isotropie**: Richtungsunabhängigkeit der Glättung -- isotrope Transferfunktion.
各向同性：平滑 - 各向同性传递函数的方向独立性

### 8.1.2 Rechteckfilter

#### 8.1.2.1 Eigenschaften

![Alt text](Figures\Folien_8_1.png)

**Vorteile**:
优点：
- separierbar
可分离
- rekursiv berechenbar: drei Rechenoperationen pro Bildpunkt unabhängig von der Filtergröße
递归可计算：每个像素三次算术运算，与滤波器大小无关

**Nachteile**:
缺点：
- keine isotrope Transferfunktion
没有各向同性传递函数
- keine monotone Abnahme der Transferfunktion
传递函数没有单调的减少

#### 8.1.2.2 Transferfunktion

![Alt text](Figures\Folien_8_2.png)

### 8.1.3 Binomialfilter

#### 8.1.3.1 Eigenschaften

![Alt text](Figures\Folien_8_4.png)

**Vorteile**:
优点：
- separierbar, beinahe isotrop
可分离的，几乎各向同性的
- streng monoton fallende Transferfunktion gegen Null
严格单调递减向零的传递函数

**Nachteile**:
缺点：
- leichte Anisotropie entlang der Diagonalen
沿对角线略微各向异性
- Varianz nicht beliebig wählbar
方差不是随意的

#### 8.1.3.2 Transferfunktion

![Alt text](Figures\Folien_8_3.png)

#### 8.1.3.3 Vergleich

![Alt text](Figures\Folien_8_5.png)

### 8.1.4 Gaußfilter

#### 8.1.4.1 Ideale Glättung

![Alt text](Figures\Folien_8_7.png)
![Alt text](Figures\Folien_8_8.png)
![Alt text](Figures\Folien_8_9.png)

![Alt text](Figures\Folien_8_6.png)

**Vorteile**:
优点：
- rein isotrop
控制各向同性
- streng monoton fallende Gaußsche Transferfunktion
严格单调递减高斯传递函数
- separierbar
可分离
- beliebige Standardabweichung wählbar
可以选择任何标准偏差

#### 8.1.4.2 Ableitungen

##### 8.1.4.2.1 Finden lokaler Konturformen

![Alt text](Figures\Folien_8_10.png)

Ziel von **Ableitungsfiltern** ist das Finden von *Kanten, Ecken und lokalen Extremwerten* im Ortsraum
导数滤波器的目标是在空间中找到边缘，角落和局部极值

Das geschieht über eine **Auswertung** des *Gradientenvektors und der Hesse-Matrix*
这是通过评估梯度向量和Hesse矩阵来完成的

Dabei interessiert **nicht nur** die *Konturform* **sondern auch** die *Stärke der lokalen Kontur*
不仅轮廓形状而且局部轮廓的强度也是令人感兴趣的

### 8.1.5 Differenzialoperatoren

#### 8.1.5.1 1. Ordnung

Die partiellen Ableitungen der Bildfunktion entlang beider Dimensionen an einem Bildort x ergeben den Gradientenvektor
沿着位置x处的两个维度的图像函数的偏导数给出梯度向量

![Alt text](Figures\Folien_8_12.png)

Die Richtungsableitung entlang der Richtung θ gibt die Stärke der Änderung entlang dieser Richtung an und entspricht dem Skalarprodukt zwischen Richtungsvektor n und Gradient
沿θ方向的方向导数表示沿该方向的变化幅度，对应于方向矢量n和梯度之间的标量乘积

![Alt text](Figures\Folien_8_13.png)
![Alt text](Figures\Folien_8_14.png)

#### 8.1.5.2 2. Ordnung

**Differenzialoperatoren zweiter Ordnung** beschreiben die *Krümmung eines mehrdimensionalen Signals*
二阶微分算子描述了多维信号的曲率

Alle möglichen Kombinationen der partiellen Ableitungen zweiter Ordnung bilden die sogenannte **Hesse-Matrix H**
二阶偏导数的所有可能组合形成所谓的Hesse矩阵H.

Für **2D-Signale** gilt:
对于2D信号：

![Alt text](Figures\Folien_8_15.png)

in einem um den Winkel θ' gedrehten Koordinatensystem x' mit diagonaler Hesse-Matrix H'
在坐标系x'中，对角线Hesse矩阵H'旋转角度θ'

![Alt text](Figures\Folien_8_16.png)

Die **Spur ∆** ist *invariant gegenüber Drehungen R(θ') des Koordinatensystems*.
迹线Δ相对于坐标系的旋转R（θ'）是不变的

### 8.1.6 Kantendetektion

#### 8.1.6.1 Möglichkeiten

**1. Mittels Richtungsableitung**
通过方向推导

**Kanten** entsprechen *Extremwerten in der ersten Ableitung*
边缘对应于一阶导数中的极值

Damit erhält man Kanten **durch** eine *Suche nach den größten Änderungen des Gradientenvektors*, also den *Maxima im Betrag von r(x)*
这通过搜索梯度向量中的最大变化（即r（x）的量的最大值）来产生边缘。

**2. Mittels Hesse-Matrix**
通过Hesse矩阵

**Kanten** sind *Nulldurchgänge in der zweiten Ableitung*
边是二阶导数中的过零点

Damit kann *mit dem Laplace-Operator ∆* nach **Kanten gesucht** werden
因此，可以搜索拉普拉斯算子Δ的边缘

Die **Signalspitzen** neben den Nulldurchgängen müssen *deutlich höher als der Rauschpegel* sein, damit der *Nulldurchgang einer Kante* entspricht
零交叉旁边的信号峰值必须明显高于噪声水平，以使零交叉对应于一个边缘

**Vergleich**: Der **Laplaceoperator** ist deutlich *rauschanfälliger* als der Betrag des Gradientenvektors.
比较：拉普拉斯算子比梯度向量的幅度更容易受到噪声的影响

#### 8.1.6.2 Ableitungen

##### 8.1.6.2.1 Ideale Eigenschaften

Für eine **ideale Ableitung** muss das Filter **folgende Eigenschaften** haben:
对于理想的派生，过滤器必须具有以下属性：

- **Verschiebungsfreiheit**: Keine Veränderung von Objektpositionen -- antisymmetrische Filtermasken für 1 Ableitungen, symmetrische Filtermasken für 2 Ableitungen
移动自由：物体位置无变化 -  1个引线的反对称滤波器掩模，2个引线的对称滤波器掩模

- **Unterdrückung des Mittelwerts**: Keine Antwort auf räumlich konstante Helligkeit -- Summe aller Koeffizienten der Maske gleich Null
抑制平均值：对空间恒定亮度无响应 - 掩模的所有系数之和等于零

- **Isotropie**: Richtungsunabhängigkeit des Gradienten -- isotrope Transferfunktion
各向同性：梯度的方向独立性 - 各向同性传递函数

**Ziel**: Entwurf diskreter Filter, die eine möglichst genaue Approximation der Ableitungen ergeben.
目标：设计离散滤波器，给出最精确的导数近似

##### 8.1.6.2.2 Diskrete Differenzen erster Ordnung

Die **erste partielle Ableitung** im Kontinuierlichen kann *im Diskreten durch Differenzen approximiert* werden
连续中的第一偏导数可以通过差异在离散中近似

Es gibt **drei verschiedene Realisierungsmöglichkeiten** für die Ableitung in x-Richtung @G(x, y)=@x (analog in y-Richtung @G(x, y)=@y), wobei *nur die symmetrische Differenz verschiebungsfrei* ist:
在x方向上推导有三种不同的可能性@G（x，y）= @ x（类似于y方向@G（x，y）= @ y），因此只有对称差是无位移的：

![Alt text](Figures\Folien_8_17.png)

##### 8.1.6.2.3 Differenzenoperator zweiter Ordnung

Die Approximation der zweiten Ableitung in x-Richtung @2G(x, y)=@x2 (analog in y-Richtung @2G(x, y)=@y2) ergibt sich aus *einer zweifachen Anwendung* der Differenzen erster Ordnung:
x方向上的二阶导数近似@ 2G（x，y）= @ x2（类似于y方向@ 2G（x，y）= @ y2）是由于一阶差分的两倍应用：

![Alt text](Figures\Folien_8_18.png)

Damit folgt für den diskreten Laplaceoperator für 2D Bilder die Filtermaske:
接下来是2D图像的离散拉普拉斯算子的滤镜掩码：

![Alt text](Figures\Folien_8_19.png)

**Nachteile**:
缺点：

- Schlechte Approximation bei großen Wellenzahlen
大波数的不良近似值
- Nicht vollkommen isotrop
不是完全各向同性的

Ein **optimierter Laplaceoperator L'** mit geringerer Anisotropie ergibt sich über eine lineare Kombination von Binomialfilter B und Impulsfilter P:
具有较低各向异性的优化拉普拉斯算子L'由二项式滤波器B和脉冲滤波器P的线性组合产生：

![Alt text](Figures\Folien_8_20.png)

##### 8.1.6.2.4 Beispiele

Vergleich der **Kantenstärken** über den *Betrag des Gradientenvektors* oder die *Nulldurchgänge des Laplaceoperators ∆*.
边缘强度与梯度向量的大小或拉普拉斯算子Δ的过零点的比较

![Alt text](Figures\Folien_8_21.png)

##### 8.1.6.2.5 Regularisierte Kantendetektion

Es gibt ein **grundsätzliches Problem**, das bei Ableitungsfiltern auftritt: *Ableitungen verrauschter Signale verstärken das Rauschen*!
导数滤波器存在一个基本问题：噪声信号的导数会放大噪声！

Die Lösung bzw Verringerung dieses Problems erreicht man **durch** eine *vorangeschaltete Glättung des Bildes*, also einem Unterdrücken von hohen Frequenzen bzw Rauschen
通过图像的上游平滑，即抑制高频或噪声来实现该问题的解决或减少

Da **Glättung und Differenzieren** *beide durch eine Faltung*, also lineare Operatoren, realisiert werden, können sie **vertauscht** werden
由于平滑和微分都是通过卷积实现的，即线性算子，它们可以互换

Das bedeutet, die **Ableitung eines Glättungsfilters** kann als **regularisierender Kantenfilter** benutzt werden
这意味着平滑滤波器的导数可以用作正则化边缘滤波器

![Alt text](Figures\Folien_8_22.png)

##### 8.1.6.2.6 Beispiele regularisierte 1. Ableitungen

Es gibt **mehrere Möglichkeiten** regularisierte Ableitungsfilter zu entwerfen
有几种方法可以设计正则化的推导滤波器

Sie unterscheiden sich in der **Güte der Approximationseigenschaften**, wie Isotropie und Transferfunktion.
它们的近似特性的质量不同，例如各向同性和传递函数

- **Sobel-Kantendetektoren**

  **Nachteil**: Zu *starke Glättung* senkrecht zur Ableitungsrichtung.

  ![Alt text](Figures\Folien_8_23.png)

- **Optimierte Sobel-Kantendetektoren**

  Verbesserung: Optimale Einstellung der Querglättung -- minimale Anisotropie
改进：横向平滑的最佳调整 - 最小的各向异性

  ![Alt text](Figures\Folien_8_24.png)

  ![Alt text](Figures\Folien_8_25.png)

##### 8.1.6.2.7 Beispiele regularisierter Laplaceoperator

Da die Transferfunktion des Laplace-Operators proportional zum Quadrat der Wellenzahl ist, ist die Rauschanfälligkeit sehr hoch
由于拉普拉斯算子的传递函数与波数的平方成比例，因此对噪声的敏感性非常高

Eine Regularisierung ist hier besonders zu empfehlen.
这里特别推荐正规化

- **Laplace of Gaussians**: LoG-Filter
高斯拉普拉斯：LoG-Filter

  ![Alt text](Figures\Folien_8_26.png)

Eine gute Näherung des LoG-Filters liefert der DoG-Filter
DoG滤波器提供了良好的LoG滤波器近似值

- **Difference of Gaussians**: DoG-Filter
高斯差异：DoG-Filter

  ![Alt text](Figures\Folien_8_27.png)

wobei p und q die Ordnung der Binomialfilter kennzeichnen und damit **Gaußglättungen** mit *unterschiedlichen Varianzen σ2* approximieren.
其中p和q表示二项式滤波器的阶数，因此近似具有不同方差σ2的高斯光滑

#### 8.1.6.3 Nichtlinearitäten und Beispiel

Der **letzte Schritt** ist das *Bewerten der Gradientenstärke bzw der Steigung in den Nulldurchgängen*
最后一步是评估梯度强度或过零点的斜率

Dazu werden zwei **zusätzliche nichtlineare Operationen** benötigt:
这需要两个额外的非线性操作：

- Schwellwertoperation und
阈值操作
- eventuell zusätzliche Hysterese (zwei Schwellwerte).
可能有额外的滞后（两个阈值）

  ![Alt text](Figures\Folien_8_28.png)

---

## 8.2 Nichtlineare Filter

### 8.2.1 Rangordnungsfilter

#### 8.2.1.1 Prinzip

Eine wichtige Klasse von nichtlinearen Filtern sind die **Rangordnungsfilter**
一类重要的非线性滤波器是排序滤波器

Anstatt ein Filterergebnis durch
而 **不是过滤结果**

- **Wichtung und Addition** der Grauwerte *in einer Nachbarschaft*, wie das bei linearen Filtern der Fall ist,
在邻域中加权和添加灰度值，如线性滤波器的情况，

zu erhalten, ergibt sich das **Filterergebnis hier durch**
在这里得到过滤器的结果

- **Vergleich und Selektion** der Grauwerte *in einer Nachbarschaft*
邻域中灰度值的比较和选择

Da Rangordnungsfilter **keine** arithmetischen Operationen durchführen, **sondern** *Grauwerte selektieren*, entstehen *keine Rundungsprobleme*, wie beim linearen Filterentwurf
由于排序过滤器不执行算术运算而是选择灰度值，因此没有舍入问题，如线性滤波器设计中那样

Es wird immer eine diskrete Menge von Grauwerten auf sich selbst abgebildet
一组离散的灰度值始终映射到自身

Alle **Rangordnungsfilter** *basieren auf* einer aufsteigend bzw absteigend sortierten Liste der Grauwerte *innerhalb* der betrachteten Nachbarschaft
所有排名过滤器都基于所考虑的邻域内的灰度值的升序或降序排序列表

Die **Nachbarschaft Np** muss nicht rechteckig sein, kann also *beliebige lokale Formen* annehmen und *ortsabhängig p* sein.
邻居Np不必是矩形的，因此它可以采用任何局部形式并且是位置相关的p

#### 8.2.1.2 Arten

Je nach **Filterart** wird entweder der Mittelwert, das Maximum oder das Minimum der sortierten Liste als Filterergebnis gewählt:
根据过滤器类型，选择排序列表的平均值，最大值或最小值作为过滤结果：

![Alt text](Figures\Folien_8_29.png)

Damit gibt es **drei verschiedene Arten von Rangordnungsfiltern**:
有三种不同类型的排名过滤器：
- Median-Filter ,
中位数过滤器，
- Minimum-Filter,
最小过滤器，
- Maximum-Filter.
最大过滤器

![Alt text](Figures\Folien_8_30.png)

### 8.2.2 Medianfilter

#### 8.2.2.1 Eigenschaften

![Alt text](Figures\Folien_8_31.png)

Der **Median-Filter** hat folgende besondere **Eigenschaft**. Er
中值滤波器具有以下特殊属性

- unterdrückt Salt & Pepper verteiltes Rauschen,
盐和胡椒抑制分布的噪音，
- ohne dabei markante Kanten zu stark zu glätten
没有过多地消除明显的边缘

**Je größer** die Nachbarschaft gewählt wird, **desto mehr** gehen feine Strukturen *verloren*, ohne dabei kontrastreiche Kanten zu verlieren.
选择的邻域越大，在不损失高对比度边缘的情况下丢失越精细的结构

### 8.2.3 Minimum-Filter

#### 8.2.3.1 Eigenschaften

**Lokaler Minimum-Operator**:

![Alt text](Figures\Folien_8_33.png)

Lokaler最小值算子：
![Alt text](Figures\Folien_8_32.png)

Auswirkungen der Größe und Form der Filtermaske Np auf
过滤面罩Np的大小和形状的影响
- **Grauwertbild**: Lokale Minima werden auf die Form der Filtermaske Np ausgedehnt, *Konturen werden glatter*
灰度值图像：局部最小值扩展到滤镜蒙版Np的形状，轮廓变得更平滑
- **Binärbild**: Die Größe der Objekte wird verkleinert. Objekte, die kleiner als die Größe der Filtermaske sind, verschwinden, *Objektberührungen werden getrennt*.
二值图像：减少了对象的大小.小于过滤器蒙版大小的对象消失，对象触摸被分开

### 8.2.4 Maximum-Filter

#### 8.2.4.1 Eigenschaften

![Alt text](Figures\Folien_8_35.png)

Lokaler Maximum Operator:
![Alt text](Figures\Folien_8_34.png)

Auswirkungen der Größe und Form der Filtermaske Np auf
过滤面罩Np的大小和形状的影响
- **Grauwertbild**: Lokale Maxima werden auf die Form der Filtermaske Np ausgedehnt, *Konturen werden glatter*
灰度值图像：局部最大值扩展到滤镜蒙版Np的形状，轮廓变得更平滑
- **Binärbild**: Die Größe der Objekte wird ausgedehnt, *kleine Löcher oder Sprünge werden gefüllt*.
二值图像：物体的大小扩大，小孔或裂缝被填充

### 8.2.5 Morphologiche Operatoren

#### 8.2.5.1 Definition


**Morphologische Operatoren** beeinflussen die *Form von Objekten über Referenzformen M*
形态算子通过参考形式M影响物体的形式

Der *Minimum- und Maximum-Operator* bilden die **beiden Grundoperationen**, aus denen sich *verschiedene zusammengesetzte Operatoren* erzeugen lassen
最小和最大运算符构成两个基础运算符，可以从中生成不同的复合运算符

Bei **Binärbildern** entsprechen der Minimum- und Maximum Operator den folgenden Mengenoperationen:
对于二进制图像，最小和最大运算符对应于以下设置操作：

- **Erosion**: G (-) M (Menge aller Pixel, für die M vollständig in G enthalten ist.)
侵蚀：G (-) M（M完全包含在G中的所有像素的集合）
- **Dilatation**: G ⊕ M (Menge aller Pixel, für die die Schnittmenge von M und G nicht die leere Menge ist.)
扩张：G⊕M（M和G的交点不是空集的所有像素的集合）

**Gängige Mengenoperationen** sind:
常用数量操作是：

![Alt text](Figures\Folien_8_36.png)

#### 8.2.5.2 Beispiele

![Alt text](Figures\Folien_8_37.png)

### 8.2.6 Normalisierte Faltung

#### 8.2.6.1 Prinzip und Beispiel

![Alt text](Figures\Folien_8_39.png)

Mit einer **normierten Faltung** kann der *Einfluss der Faltungsoperation lokal variiert* werden
利用归一化卷积，卷积运算的影响可以在本地变化

Im **speziellen Fall** bei einer Glättungsmaske entspricht das einer *lokal variierenden gewichteten Mittelung*
在平滑掩模的特殊情况下，这对应于局部变化的加权平均

Dazu benötigt man für jeden Grauwert G(m, n) einen entsprechenden **Gewichtungsfaktor W(m, n)**, der den Einfluss des Filters H auf den Grauwert variiert
为此，每个灰度值G（m，n）需要相应的加权因子W（m，n），这改变了滤波器H对灰度值的影响

Die **nichtlineare Berechnungsvorschrift** lautet:
非线性计算规则是：
![Alt text](Figures\Folien_8_38.png)

---

## 8.3 Adaptive Filter

### 8.3.1 Idee & Ziel

#### 8.3.1.1 Beispiel : Anisotroper Gaußfilter

![Alt text](Figures\Folien_8_40.png)

**Idee**: Die **Faltungsmaske Hp** soll sich in Abhängigkeit *von der lokalen Bildstruktur ändern*, um die **Filtereigenschaften** optimal an bestimmte Eigenschaften der *lokalen Bildstruktur anzupassen*
想法：卷积蒙版Hp应根据局部图像结构而改变，以使滤镜属性最佳地适应局部图像结构的某些属性

**Problem**: Die **Filtermasken Hα(p)** müssen alle berechnet und abgespeichert werden! Dabei ist es vorteilhaft die **Filterkoeffizienten** *über Funktionen mit frei justierbaren Parametern α(p) ortsabhängig zu adaptieren*.
问题：过滤掩模Hα（p）必须全部计算并保存！有利的是，通过具有可自由调节的参数α（P）的函数，以位置相关的方式调整滤波器系数。

---

## 8.4 Steuerbare Filter

### 8.4.1 Idee & Ziel


- **Idee**: Die **Faltungsmaske Hp** soll *abhängig von der lokalen Bildstruktur* in einer bestimmten Nachbarschaft Np um den Bildpunkt p sein, um die **Filtereigenschaften** *optimal* an bestimmte Eigenschaften der lokalen Bildstruktur anzupassen
想法：卷积掩模Hp将依赖于像素p周围的特定邻域Np中的局部图像结构，以便最优地使滤波器属性适应于局部图像结构的某些属性

- **Definition**: **Steuerbare Filter Hα(p)** haben einige *frei justierbare Parameter α(p)*, die die **Filterung** *ortsabhängig* steuern
定义：可控滤波器Hα（p）具有一些可自由调节的参数α（p），它们以位置相关的方式控制滤波

- **Ziel**: Einen Satz von wenigen **Basisfiltern Hi** zu konstruieren, mit denen man sich jede beliebige Antwort eines steuerbaren Filters **über** eine *α- abhängige Interpolation* der Filterantworten der Basisfilter **erzeugen** kann.
目标：构建一组少数基滤波器，可用于通过基本滤波器的滤波响应的α依赖插值从可控滤波器生成任何响应

  ![Alt text](Figures\Folien_8_41.png)

### 8.4.2 Entwurf

**Ziel** ist also der Entwurf eines Sets an **Basisfiltern Hi** und **Interpolationsfunktionen fi(α(p))**, so dass der **steuerbare Filter Hα(p)** möglichst gut approximiert wird:
因此，目的是设计一组基本滤波器Hi和插值函数fi（α（p）），以便可控滤波器Hα（p）尽可能近似：
![Alt text](Figures\Folien_8_42.png)

Damit läßt sich eine **adaptive Filterung** mit einem **steuerbaren Filter Hα(p)** sehr effizient implementieren:
这使得可以非常有效地使用可控滤波器Hα（p）实现自适应滤波：
![Alt text](Figures\Folien_8_43.png)

### 8.4.3 Beispiele

#### 8.4.3.1 Adaptive Anisotrope Mittelung 各向异性平均

Für jedes steuerbare Filter gilt wegen der Linearitätseigenschaft der Fouriertransformation:
对于每个可控滤波器，由于傅里叶变换的线性特性，

![Alt text](Figures\Folien_8_44.png)

Deswegen können die Basisfilter eines steuerbaren Filters über seine Transferfunktion entworfen werden
因此，可控滤波器的基础滤波器可以通过其传递函数来设计

Beispiel einer **Transferfunktion eines gerichteten Glättungsfilters** in Polarkoordinaten (k, θ) im Fourierraum:
傅立叶空间中极坐标（k，θ）中方向平滑滤波器的传递函数示例：
![Alt text](Figures\Folien_8_45.png)

Der **frei wählbare Parameter θ0** bestimmt die Richtung in die nicht geglättet werden soll
可自由选择的参数θ0决定了您不想平滑的方向

Die Radialfunktion f(k) bestimmt die Grenzfrequenz.
径向函数f（k）确定截止频率

Es ergibt sich folgende Zerlegung in Basisfilter Hˆ i und Interpolationsfunktionen fi(θ0):
结果是以下分解为基本滤波器H i和插值函数fi（θ0）：

![Alt text](Figures\Folien_8_46.png)

Durch Optimierung kann ein Basisset an 3×3 großen separierbaren Filtern im Ortsraum gefunden werden:
通过优化，可以在空间中的3×3可分离滤波器上找到基本集：

![Alt text](Figures\Folien_8_47.png)

Bei diesem Filterset nimmt die Direktionalität bei höheren Frequenzen ab.
使用此滤波器设置，方向性在较高频率下降低

Im einfachsten Fall kann der Winkel θ0 über die Maximierung der Richtungsableitung nach der Richtung berechnet werden:
在最简单的情况下，角度θ0可以通过根据方向最大化方向导数来计算：

![Alt text](Figures\Folien_8_48.png)

#### 8.4.3.2 Adaptive Richtungsableitung

Die Richtungsableitung entlang der Richtung θ0 ist an sich schon steuerbar!.
沿θ0方向的方向导数本身是可控的

![Alt text](Figures\Folien_8_49.png)

Filterbank für sieben verschiedene Richtungsableitungen berechnet aus nur zwei Ableitungen G ∗ H0◦ und G ∗ H90◦.
从仅有两个导数G * H0◦和G * H90 计算的七个不同方向导数的滤波器组

![Alt text](Figures\Folien_8_50.png)
