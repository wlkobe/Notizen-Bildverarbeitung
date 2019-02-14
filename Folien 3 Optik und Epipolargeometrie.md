<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 3. Optik & Epipolargeometrie](#folien-3-optik-epipolargeometrie)
	- [3.1 Das Opjektiv](#31-das-opjektiv)
		- [3.1.2 Motivation](#312-motivation)
		- [3.1.3 Linsensystem mit Blende](#313-linsensystem-mit-blende)
		- [3.1.4 Bildentstehung bei Linsenabbildungen](#314-bildentstehung-bei-linsenabbildungen)
		- [3.1.5 Kennwerte](#315-kennwerte)
			- [3.1.5.1 Brennweite 焦距](#3151-brennweite-焦距)
			- [3.1.5.2 Brechzahl 折射率](#3152-brechzahl-折射率)
			- [3.1.5.3 Brechzahl, Brennweite & Farbe des Lichtes](#3153-brechzahl-brennweite-farbe-des-lichtes)
			- [3.1.5.4 Abbildungsmaßstab 图像比例](#3154-abbildungsmastab-图像比例)
			- [3.1.5.5 Sichtfeld 视野](#3155-sichtfeld-视野)
				- [3.1.5.5.1 Beispiel](#31551-beispiel)
			- [3.1.5.6 Blendenzahl & Belichtungszeit 光圈 & 曝光](#3156-blendenzahl-belichtungszeit-光圈-曝光)
			- [3.1.5.7 Schärfentiefe 景深](#3157-schärfentiefe-景深)
				- [3.1.5.7.1 Blendenöffung & Brennweite 光圈 & 焦距](#31571-blendenöffung-brennweite-光圈-焦距)
				- [3.1.5.7.2 Beispiele](#31572-beispiele)
		- [3.1.6 Sammellinse](#316-sammellinse)
			- [3.1.6.1 Dünne Linse](#3161-dünne-linse)
				- [3.1.6.1.1 Strahlenoptisches Grundgesetz](#31611-strahlenoptisches-grundgesetz)
				- [3.1.6.1.2 Abbildungsmaßstab 图像比例](#31612-abbildungsmastab-图像比例)
				- [3.1.6.1.3 Tiefenschärfe (e) & Schärfentiefe (∆g = gh−gv) 焦点和景深](#31613-tiefenschärfe-e-schärfentiefe-g-ghgv-焦点和景深)
					- [3.1.6.1.3.1 Anwendung -- 3D Profil mittels Schärfemessung](#316131-anwendung-3d-profil-mittels-schärfemessung)
		- [3.1.7 Abbildungsfehler](#317-abbildungsfehler)
			- [3.1.7.1 Überblick](#3171-überblick)
			- [3.1.7.2 Beugungsunschärfe 衍射模糊](#3172-beugungsunschärfe-衍射模糊)
			- [3.1.7.3 Sphärische Aberration (Abschweifung) 球面像差](#3173-sphärische-aberration-abschweifung-球面像差)
			- [3.1.7.4 Astigmatismus (Punktlosigkeit) 散光](#3174-astigmatismus-punktlosigkeit-散光)
			- [3.1.7.5 Chromatische Aberration 色差](#3175-chromatische-aberration-色差)
			- [3.1.7.6 Verzeichnungen 扭曲](#3176-verzeichnungen-扭曲)
		- [3.1.8 Kamerakalibrierung II](#318-kamerakalibrierung-ii)
			- [3.1.8.1 Radiale Verzeichnungen](#3181-radiale-verzeichnungen)
			- [3.1.8.2 Normierte Koordinaten](#3182-normierte-koordinaten)
	- [3.2 Epipolargeometrie](#32-epipolargeometrie)
		- [3.2.1 Eigeninduzierter Optischer Fluss](#321-eigeninduzierter-optischer-fluss)

<!-- /TOC -->

# Folien 3. Optik & Epipolargeometrie
---
## 3.1 Das Opjektiv

### 3.1.2 Motivation

### 3.1.3 Linsensystem mit Blende

Jede **reale Kamera** besitzt ein Objektiv mit einem **sammelnden Linsensystem** und einer **Blende**
每个真正的相机都有一个带有聚光透镜系统和快门的镜头

Das **Linsensystem** *beeinflusst* die Richtung der Ausbreitung von Lichtstrahlen *über* Beugung, Brechung und Reflexion
透镜系统通过衍射，折射和反射影响光线的传播方向

Mit Hilfe der **Blende** wird die *Lichtmenge durch das Objektiv vorgegeben*
在光圈的帮助下，光量由镜头提供

Die **drei wichtigsten Größen** sind die *Brennweite f, die Blendenöffnung D und die Bildweite b*
三个最重要的变量是焦距f，光圈D和图像宽度b

Diese Größen **beeinflussen** z.B. die *Schärfe der Bildaufnahme*, oder bestimmen z.B. den *Abbildungsmaßstab*
例如，这些数量会影响图像的清晰度捕获,或确定图片比例

Im folgenden werden verschiedene Kennwerte eines Objektivs und deren Abhängigkeiten genauer besprochen
在下文中，更详细地讨论透镜的各种特性及其依赖性

### 3.1.4 Bildentstehung bei Linsenabbildungen
![Alt text](Figures\Folien_3_1.png)
---
### 3.1.5 Kennwerte

#### 3.1.5.1 Brennweite 焦距
![Alt text](Figures\Folien_3_2.png)

Das **Linsensystem eines Objektivs** besteht meist aus mehreren *konvexen (Sammel-) und konkaven (Zerstreuungs-) Linsen*.
镜片的镜片系统通常由几个凸（收集）和凹（发散）镜片组成

Die **optischen Eigenschaften** einer Linse werden durch die *Brennweite f* beschrieben
透镜的光学特性由焦距f描述

Die **Brennweite** entspricht dem *Abstand des Brennpunkts F* von der Hauptebene einer Linse und ist bei *Sammellinsen positiv f > 0*
焦距对应于焦点F距镜头主平面的距离，并且在会聚透镜处正f> 0

Die **Brennweite** läßt sich aus der Brechzahl des Linsenmaterials n, der Brechzahl des umgebenden Mediums n0 (für Luft gilt n0 = 1), sowie den Krümmungsradien R1 und R2, und der Dicke d der Linse **berechnen**.
可以根据透镜材料的折射率n，周围介质的折射率n0（对于空气n0 = 1），以及曲率半径R1和R2以及透镜的厚度d来计算焦距。

#### 3.1.5.2 Brechzahl 折射率

Die **Brechzahl n der Linse** kennzeichnet die *Brechung und das Reflexionsverhalten* von Lichtwellen beim Treffen auf die Linsenoberfläche
透镜的折射率n表征光波撞击透镜表面时的折射和反射行为

Sie ist durch das Verhältnis der Ausbreitungsgeschwindigkeiten einer Lichtwelle im Vakuum c0 und im Material der Linse c definiert
它由真空c0中的光波和透镜c的材料中的光传播速度的比率来定义 -- **n = c0/c > 1**

Wenn Lichtwellen eine Linse durchqueren, dann reduziert sich die Ausbreitungsgeschwindigkeit c
当光波穿过透镜时，传播速度c减小

Die Ausbreitungsgeschwindigkeit einer Welle hängt von ihrer Wellenlänge λ und der Frequenz ν ab:
波的传播速度取决于其波长λ和频率ν： **c = λν = c0/n**

#### 3.1.5.3 Brechzahl, Brennweite & Farbe des Lichtes

Da sich die **Frequenz** beim Übergang in einen anderen Stoff *nie ändert*, ändert sich die Wellenlänge in gleicher Weise wie die Ausbreitungsgeschwindigkeit
由于频率在换成另一种物质时不会改变，因此波长的变化方式与传播速度相同 -- **λ=λ0/n**

Die Wellenlänge und die Lichtgeschwindigkeiten in zwei verschiedenen Stoffen verhalten sich umgekehrt wie die Brechzahlen
两种不同材料中的光的波长和速度与折射率相反 -- **λ1/λ2 = c1/c2 = n2/n1**

Die Brechzahl n hängt also von der Wellenlänge λ ab und deswegen ist auch die Brennweite f von der Wellenlänge und damit der Farbe des Lichtes abhängig.
因此，折射率n取决于波长λ，因此焦距f取决于波长并因此取决于光的颜色。-- **f ~ λ/(λ0 - λ)**

#### 3.1.5.4 Abbildungsmaßstab 图像比例

![Alt text](Figures\Folien_3_6.png)

#### 3.1.5.5 Sichtfeld 视野

![Alt text](Figures\Folien_3_9.png)
![Alt text](Figures\Folien_3_10.png)

Wie bereits im Abschnitt über geometrische Projektionen für das Lochkameramodell gezeigt, ist in der Praxis die Bildebene auf eine maximale Bildgröße Bmax räumlich begrenzt
如针孔相机模型的几何投影部分所示，实际上图像平面在空间上受限于最大图像尺寸Bmax

Es ergibt sich ein eingeschränktes Sichtfeld field of view (FOV)
结果是受限制的视野（FOV）视野

Falls die Entfernung zum Motiv größer als die Brennweite ist g > f, erhält man für das Sichtfeld bzw. den Bildwinkel
如果到主体的距离大于焦距g> f，则可以获得视野或视角

![Alt text](Figures\Folien_3_8.png)

- Bei einer flachen Bildebene ist dieser Winkel immer kleiner als θ ≤ 180◦
对于平面图像平面，此角度始终小于θ≤180°

- Je kleiner die Brennweite f, desto größer ist das Sichtfeld θ.
焦距f越小，视场θ越大。

##### 3.1.5.5.1 Beispiel

Wenn man eine *konstante Bildgröße B* eines Gegestandes für unterschiedliche Gegenstandsweiten g scharf abgebildet erhalten möchte, dann muss die *Brennweite f und die Bildweite b entsprechend angepasst werden*, womit sich auch der **Bildwinkel θ** ändert.
如果希望针对不同的物体宽度g获得给定物品的恒定图像尺寸B，则必须相应地调整焦距f和图像距离b，这也改变了图像角度θ

#### 3.1.5.6 Blendenzahl & Belichtungszeit 光圈 & 曝光

Die **Blendenzahl κ** bezeichnet das Verhältnis der Brennweite f zum Durchmesser D der Eintrittspupille des Objektivs
κ表示焦距f与物镜的入射光瞳的直径D的比率 -- **k = f/D**

Die **Eintrittspupille** ist die Öffnung des Objektivs, das die einfallenden Strahlenbündel begrenzt
入射光瞳是限制入射光束的透镜的开口

Je kleiner κ
k越小

- desto mehr Lichteinfall vorhanden
存在的光越多

- desto kürzere Belichtungszeit notwendig
需要更短的曝光时间

- desto größere Bildwiederholrate möglich
更高的刷新率可能

- desto weniger Bewegungsunschärfe tritt auf
运动模糊越少

- desto kleiner die Schärfentiefe (siehe Abschnitt Schärfentiefe)
景深越小（参见景深部分）

#### 3.1.5.7 Schärfentiefe 景深

##### 3.1.5.7.1 Blendenöffung & Brennweite 光圈 & 焦距

##### 3.1.5.7.2 Beispiele
---
### 3.1.6 Sammellinse

#### 3.1.6.1 Dünne Linse

Die **einfachste Möglichkeit Lichtstrahlen zu bündeln** geschieht über eine *Blende* und eine *konvexe Sammellinse*
聚焦光线最简单的方法是通过光圈和凸聚光透镜

*Vernachlässigt man die Dicke d der Linse* erhält man das **Modell der dünnen Linse**
忽略透镜的厚度d给出了薄透镜的模型

Es wird **angenommen**, dass die Bildebene parallel zur Linsenebene liegt und beide senkrecht auf der optischen Achse stehen, wobei die optische Achse durch das Projektionszentrum der Linse verläuft
假设图像平面与透镜平面平行并且两者都垂直于光轴，光轴穿过透镜的投影中心

Wird **nur die Brechung von Licht berücksichtigt** und Linsenfehler sowie Beugungserscheinungen werden vernachlässigt, dann *treffen sich alle Strahlen eines parallelen Lichtbündels in der Brennebene* und man erhält das **strahlenoptische Grundgesetz**.
如果仅考虑光的折射并且忽略透镜像差和衍射现象，那么平行光束的所有光线在焦平面中相遇并且获得辐射光学基本定律。

##### 3.1.6.1.1 Strahlenoptisches Grundgesetz
![Alt text](Figures\Folien_3_3.png)

Diese Abbildungsgleichung für dünne Linsen (d ! 0) ergibt sich über den **Abbildungsmaßstab** aus dem Strahlensatz und den Beziehungen zwischen Gegenstandsgröße G, Bildgröße B, Gegenstandsweite g und der Bildweite b
薄透镜的成像方程（d！0）由光束组的放大率和物体尺寸G，图像尺寸B，物体宽度g和图像尺寸b之间的关系给出 ![Alt text](Figures\Folien_3_4.png)

Unter den gemachten Annahmen entspricht die Bildweite der rein geometrisch definierten Kamerakonstanten b = c.
在所做的假设下，图像宽度对应于纯几何定义的相机常数b = c
![Alt text](Figures\Folien_3_5.png)

##### 3.1.6.1.2 Abbildungsmaßstab 图像比例

![Alt text](Figures\Folien_3_6.png)

Der **Abbildungsmaßstab β** ist definiert als Verhältnis zwischen Bildgröße B eines abgebildeten Gegenstandes und der realen Gegenstandsgröße G
放大率β被定义为成像对象的图像尺寸B与真实对象尺寸G之间的比率
![Alt text](Figures\Folien_3_7.png)

Jedes Objektiv besitzt eine **Naheinstellgrenze**
每个镜头都有一个近距离聚焦限制

*Unterhalb diesem Mindestabstand gmin* zum Objekt ist es **nicht mehr möglich** auf das **Objekt zu fokussieren**
在距离物体的最小距离gmin之下，不再可能聚焦在物体上

Ein Objektiv besitzt also einen **maximalen Abbildungsmaßstab**.
因此，透镜具有最大放大率

##### 3.1.6.1.3 Tiefenschärfe (e) & Schärfentiefe (∆g = gh−gv) 焦点和景深

Vernachlässigt man Auswirkungen wie Linsenfehler und Beugungserscheinungen, dann gibt es *für jede Gegenstandsweite g eine bestimmte Bildweite b* in der es zu einer **punktförmigen Wiedervereinigung aller Lichtstrahlen** kommt
如果忽略诸如透镜像差和衍射现象之类的影响，那么对于每个物体宽g，存在一定的图像宽度b，其中发生所有光线的点状重新统一。
![Alt text](Figures\Folien_3_13.png)

![Alt text](Figures\Folien_3_11.png)
![Alt text](Figures\Folien_3_12.png)

In dieser **optimal eingestellten Bildebene** entsteht ein **optimal scharfes Bild** des Gegenstandes in der Gegenstandsebene
在该最佳调整的图像平面中，产生对象平面中的对象的最佳清晰图像

Wird der Abstand des Gegenstandes verringert, muss die Bildweite vergrößert werden.
如果物体的距离减小，则必须增加图像尺寸。

![Alt text](Figures\Folien_3_14.png)

Alle *Gegenstände vor gv oder hinter gh der eingestellten Gegenstandsweite g* werden *auf der Bildebene mit Abstand b* **unscharf** mit einem Zerstreuungskreis vom Durchmesser e abgebildet
gv前面或设定对象g后面的所有物体在图像平面上变得模糊，距离b与直径混淆的圆圈e显示

Das bedeutet, dass *alle Gegenstände im Bereich der Schärfentiefe ∆g = gh−gv auf der Bildebene* mit einem Zerstreuungskreis kleiner als e abgebildet werden
这意味着在图像平面上景深范围Δg= gh-gv的所有物体的色散圆小于e成像

Man nennt **e die Tiefenschärfe**, wobei für eine Digitalkamera eine Tiefenschärfe von *unter einem Pixel* angestrebt werden muss, um eine scharfe Abbildung in Abhängigkeit von der Pixelgröße zu erreichen.
一个电话e对于数字相机，必须寻找小于一个像素的景深，以便根据像素尺寸获得清晰的图像。

Die **Blendenöffnung D und die Tiefenschärfe e** hängen über die Bildweiten b, bv und bh folgendermaßen zusammen
光圈D和景深？将图像宽度b，bv和bh挂在一起，如下所示
![Alt text](Figures\Folien_3_15.png)

??? Durch Einsetzen der Beziehung (1) für b, bv und bh ergibt sich mit der Blendenzahl κ und einer gewünschten Tiefenschärfe e der Schärfentiefebereich um einen Abstand g bei dem ein Gegenstand optimal scharf e -- 0 abgebildet wird.
通过将关系式（1）代入b，bv和bh，它给出了f数κ和所需的焦深e景深是物体最佳锐利的距离g
![Alt text](Figures\Folien_3_16.png)

- Wenn *gv und gh des Arbeitsbereiches vorgegeben sind*, dann erhält man die **Gegenstandsweite g**, bei der die Tiefenschärfe e optimal klein ist
如果给出工作区域的gv和gh，那么你得到的物体宽度为g，景深最小
![Alt text](Figures\Folien_3_17.png)

- Wenn der **Schärfentiefenbereich** für ein vorgegebenes e zwischen gv(g) und gh = inf liegen soll, dann ergibt sich g zu
如果给定的景深e在gv（g）和gh = 1之间，然后加入g
![Alt text](Figures\Folien_3_18.png)

- Wenn die eingestellte Gegenstandsweite g und die tatsächliche Gegenstandsweite gi bekannt sind, dann kann für gi ≥ g die resultierende Tiefenschärfe berechnet werden
如果设定物距g和实际物距gi是已知的，则对于gi≥g，可以计算得到的焦深。
![Alt text](Figures\Folien_3_19.png)

- Und für Fernaufnahmen g >> f, b ≈ f, ergibt sich näherungsweise.
而对于远程录音 g >> f ，b≈f ，是近似值。
![Alt text](Figures\Folien_3_20.png)

![Alt text](Figures\Folien_3_21.png)

Daraus folgt für die **Schärfentiefe**:
它遵循景深

- Die **Schärfentiefe** ist *umgekehrt proportional* zum **Quadrat der Brennweite**
景深与焦距的平方成反比

- Damit ergeben kleinere Brennweiten trotz einer zu f proportionalen Bildgröße eine größere Schärfentiefe
尽管与f图像尺寸成比例且景深更大，但这导致更小的焦距

- Eine **kleinere Blendenöffnung** und damit eine **größere Blendenzahl**, vergrößert den Bereich der Schärfentiefe
较小的光圈因此较大的f数增加了景深

- Eine **kleine Blendenöffnung** jedoch verringert die Lichtmenge, deswegen muss die Belichtungszeit erhöht werden.
但是，小光圈会减少光量，因此必须增加曝光时间。

###### 3.1.6.1.3.1 Anwendung -- 3D Profil mittels Schärfemessung
---
### 3.1.7 Abbildungsfehler

**Abbildungsfehler oder Aberrationen** sind Abweichungen von der idealen optischen Abbildung, die ein unscharfes oder verzerrtes Bild bewirken
图像像差或像差是理想光学图像的偏差，导致图像模糊或失真

Es gibt eine Reihe von **Gründen für solche Abweichungen**, die unter anderem das optische Auflösungsvermögen und die Kontrastübertragung (siehe Kraus S 66-73) beeinflussen:
造成这种偏差的原因有很多，其中包括光学分辨率和对比度传输（见Kraus S 66-73）：

#### 3.1.7.1 Überblick

- Beugungsunschärfe 衍射模糊
- Sphärische Aberration 球面像差
- Astigmatismus 散光
- Chromatische Aberration 色差
- Verzeichnungen 扭曲
- Bildfeldwölbung 场曲
- Helligkeitsverteilung (natürlicher Randlichtabfall, Vignettierung) 亮度分布（自然边缘光线下降，渐晕）
- Umwelteinflüsse (Temperatur, Verschmutzung, Alterung)  环境影响（温度，污染，老化）

#### 3.1.7.2 Beugungsunschärfe 衍射模糊

Aufgrund des **Wellencharakters des Lichtes** und dessen Beugung an der kreisförmigen Blende des Objektives gibt es in der Bildebene der Kamera keinen idealen Bildpunkt, sondern ein sogenanntes Beugungsscheibchen mit theoretischem Gesamtdurchmesser
由于光的波动特性及其在物镜圆孔处的衍射，在相机的像平面中没有理想的像素，而是具有理论总直径的所谓衍射盘 -- **uth = 2.44κλ**

Praktisch entspricht die **Beugungsunschärfe** näherungsweise der **Blendenzahl**
实际上，衍射大致对应于f数 -- **u ≈ κ = f / D**

**Je kleiner die Blendenöffnung D**, **desto größer wird die Beugungsunschärfe** und desto weniger Licht kommt durch die Blende hindurch.
孔径D越小，衍射衍射变得越大并且光通过孔径越少

#### 3.1.7.3 Sphärische Aberration (Abschweifung) 球面像差

Bei der **sphärischen Abberation** bilden sphärisch geschliffene Linsen *parallele Lichtstrahlen nicht mehr exakt im Brennpunkt* ab
对于球面像差，球面透镜不再精确地在焦点处形成平行光线

![Alt text](Figures\Folien_3_22.png)
![Alt text](Figures\Folien_3_23.png)

**Effekt**: Verschwommenes Bild, scharfes Kernbild wird von einem unscharfen überlagert
效果：图像模糊，锐利的核心图像被模糊覆盖

**Abhilfe**: Vorschalten von Blenden
补救措施：孔径上游

#### 3.1.7.4 Astigmatismus (Punktlosigkeit) 散光

![Alt text](Figures\Folien_3_24.png)

Trifft ein divergierender *Lichtstrahl nicht senkrecht sondern schräg auf die Linsenoberfläche* und verläuft dadurch unsymmetrisch zur optischen Achse, tritt an sphärischen Linsenoberflächen **Astigmatismus** auf
如果发散光束不垂直但倾斜地照射到透镜表面并因此相对于光轴不对称地行进，则在球面透镜表面上发生像散

**Ursache** dafür sind *unterschiedliche lokale Krümmungsradien der Linse*
这是由于镜片的局部曲率半径不同

Es *entstehen unterschiedliche Brennpunkte und Brennweiten* **für** *unterschiedliche Teilstrahlengänge*
不同的部分光束路径有不同的焦点和焦距

**Effekt**: Das Kamerabild wirkt für den Betrachter *nicht mehr scharf fokussiert*, da ein Szenenpunkt nicht mehr als Bildpunkt sondern unscharf abgebildet wird (punktlos).
效果：相机图像不再具有用于观察者的清晰焦点，因为场景点不再显示为像素而是模糊（没有点）

#### 3.1.7.5 Chromatische Aberration 色差

![Alt text](Figures\Folien_3_25.png)
![Alt text](Figures\Folien_3_26.png)
![Alt text](Figures\Folien_3_27.png)

Wie bereits im Abschnitt Kennwerte besprochen, hängt die **Brechzahl n** hängt von der **Wellenlänge λ** ab und deswegen ist auch die **Brennweite f** von der Wellenlänge und damit der **Farbe des Lichtes** abhängig
正如在特性部分中已经讨论的那样，折射率n取决于波长λ，因此焦距f取决于波长，因此取决于光的颜色

Das hat zur Folge, dass auch das **optische Auflösungsvermögen** von der **Wellenlänge** abhängt
结果，光学分辨率也取决于波长 -- **c = λν = c0/n -- n = c0/λν**

**Kurzwelliges Licht wird stärker als langwelliges Licht gebrochen**, deswegen werden die Spektralanteile des weißen Lichtes unterschiedlich fokussiert und damit an unterschiedlichen Orten auf der Bildebene abgebildet
短波光比长波光更强烈地破碎，因此白光的光谱分量被不同地聚焦，因此在图像平面上的不同位置成像

Das nennt man auch **chromatische Abberation**.
这也称为色差

#### 3.1.7.6 Verzeichnungen 扭曲

![Alt text](Figures\Folien_3_28.png)
![Alt text](Figures\Folien_3_29.png)
![Alt text](Figures\Folien_3_30.png)

Eine **Verzeichnung** ist eine nichtlineare optische Verzerrung, die *lokal den Abbildungsmaßstab verändert*
失真是局部改变放大率的非线性光学失真

Sie wird z.B **durch**
- die Abweichung des Ein- und Austrittswinkels eines Strahles bei einem realen optischen System, 真实光学系统中光束的入射角和出射角的偏差
- der Abweichung von der mechanisch realisierten Bildweite zur optischen Bildweite 机械实现的图像距离与光学图像距离的偏差
- Zentrierfehlern der Linsen im Objektiv hervorgerufen 物镜中的透镜的定心误差引起的

Es gibt **sowohl** radiale **als auch** tangentiale Verzeichnungen
有径向和切向扭曲

Da die **tangentiale** meistens um eine Größenordung kleiner als die radiale ist, kann sie *vernachlässigt werden*
由于切向通常比径向小一个数量级，因此可以忽略不计

---
### 3.1.8 Kamerakalibrierung II

#### 3.1.8.1 Radiale Verzeichnungen

Besonders bei **Weitwinkelobjektiven** kann eine *starke radiale Verzeichnung* auftreten
特别是对于广角镜头，会发生强烈的径向畸变

Sie äußern sich in einer tonnen- oder kissenförmigen Verzerrung gerader Linien im Bild
它们表现为画面中的桶状或枕形扭曲的直线

Die Parameter, welche die **optische Verzeichnung charakterisieren**, zählen auch zu der *inneren Orientierung, den intrinsischen Kameraparametern*.
表征光学畸变的参数也属于内部方向，即固有的相机参数

![Alt text](Figures\Folien_3_31.png)

Je nachdem, welches Modell zur Beschreibung der radialen Verzeichnungen gewählt wird, ergibt sich eine unterschiedliche Anzahl von Verzeichnungsparametern {L'(rd), c}
根据选择哪种模型来描述径向畸变，会产生不同数量的失真参数{L'(rd)，c}

Durch Bestimmung der Parameter kann man mit diesen Modellen die tatsächliche Verzerrung xd' = (xd' , yd' )T eines Bildes korrigieren und ein entzerrtes Bild xu' = (xu', yu')T berechnen.
通过确定参数，可以用这些模型校正图像的实际失真xd'=（xd'，yd'）T，并计算均衡图像xu'=（xu'，yu'）T

Das Zentrum der Verzerrung c und die Verzerrungs Korrekturfaktoren a1, a2, a3, a4, ... sind zu bestimmen. 将确定失真c的中心和失真校正因子a1，a2，a3，a4 ......

#### 3.1.8.2 Normierte Koordinaten

![Alt text](Figures\Folien_3_32.png)

Ideale normierte Bildkoordinaten entstehen bei einer rein kanonischen Projektion
理想的标准化图像坐标出现在纯粹的规范投影中

Je besser die Kamerakalibrierung durchgeführt wird, desto näher kommt man an dieses Ideal heran.
相机校准越好，您就越接近理想状态

---
## 3.2 Epipolargeometrie

### 3.2.1 Eigeninduzierter Optischer Fluss

![Alt text](Figures\Folien_3_33.png)

**Eigeninduzierten optischen Fluss** u = [u, v]T , der sich additiv aus einem rotatorischen u! und translatorischen uν Geschwindigkeitsanteil zusammensetzt, wobei nur der translatorische Anteil von der Entfernung ZK abhängig ist
自感光流u = [u，v] T，它是从旋转的u！和平移速度分量，其中只有平移分量取决于距离ZK
