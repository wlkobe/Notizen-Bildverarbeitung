<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Folien 4 Beleuchtung und Digitalisierung](#folien-4-beleuchtung-und-digitalisierung)
	- [4.1 Beleuchtung](#41-beleuchtung)
		- [4.1.1 Lichtquellen & Objekteigenschaften](#411-lichtquellen-objekteigenschaften)
		- [4.1.2 Anwendungsbeispiel](#412-anwendungsbeispiel)
			- [4.1.2.1 Aktive Beleuchtung](#4121-aktive-beleuchtung)
			- [4.1.2.2 Gestalt aus Schattierung](#4122-gestalt-aus-schattierung)
		- [4.1.3 Anforderungen und Auslegung](#413-anforderungen-und-auslegung)
		- [4.1.4 Strahlungsphysik](#414-strahlungsphysik)
			- [4.1.4.1 Lichttechnik](#4141-lichttechnik)
		- [4.1.5 Hellempfindlichkeitskurve](#415-hellempfindlichkeitskurve)
		- [4.1.6 Radiometrische Größen 辐射量](#416-radiometrische-gröen-辐射量)
		- [4.1.7 Punktlichtquelle](#417-punktlichtquelle)
			- [4.1.7.1 Modell](#4171-modell)
		- [4.1.8 Strahlengang](#418-strahlengang)
			- [4.1.8.1 Helligkeit](#4181-helligkeit)
		- [4.1.9 Oberflächen](#419-oberflächen)
			- [4.1.9.1 Reflexionen](#4191-reflexionen)
				- [4.1.9.1.1 Gerichtete Reflexion](#41911-gerichtete-reflexion)
				- [4.1.9.1.2 Diffuse Reflexion](#41912-diffuse-reflexion)
		- [4.1.10 Arten (6)](#4110-arten-6)
			- [4.1.10.1 Auflicht & Durchlicht](#41101-auflicht-durchlicht)
	- [4.2 Digitales Bild](#42-digitales-bild)
		- [4.2.1 Bildaufnahmesysteme](#421-bildaufnahmesysteme)
		- [4.2.2 Bildaufzeichnung](#422-bildaufzeichnung)
			- [4.2.2.1 Prinzip](#4221-prinzip)
		- [4.2.3 Farbaufnahmen](#423-farbaufnahmen)
			- [4.2.3.1 Bayer-Filter](#4231-bayer-filter)
			- [4.2.3.2 Foveon X3 Direkt-Bildsensor](#4232-foveon-x3-direkt-bildsensor)
			- [4.2.3.3 Vergleich](#4233-vergleich)
		- [4.2.4 Digitalisierungsfehler](#424-digitalisierungsfehler)
			- [4.2.4.1 Überblick](#4241-überblick)
			- [4.2.4.2 Bildrauschen](#4242-bildrauschen)
		- [4.2.5 Funktionsprinzipien unterschiedlicher Typen](#425-funktionsprinzipien-unterschiedlicher-typen)
			- [4.2.5.1 Zeilenkamera](#4251-zeilenkamera)
			- [4.2.5.2 Aktive Kamera](#4252-aktive-kamera)
				- [4.2.5.2.1 Laufzeitkamera](#42521-laufzeitkamera)
					- [4.2.5.2.1.1 PMD (Photonic Mixer Device)](#425211-pmd-photonic-mixer-device)
				- [4.2.5.2.2 Strukturiertes Licht](#42522-strukturiertes-licht)
					- [4.2.5.2.2.1 Prinzip](#425221-prinzip)
					- [4.2.5.2.2.2 Beispiel Microsoft KINECT](#425222-beispiel-microsoft-kinect)

<!-- /TOC -->

# Folien 4 Beleuchtung und Digitalisierung
---
## 4.1 Beleuchtung

### 4.1.1 Lichtquellen & Objekteigenschaften

**Um Bilder zu interpretieren und 3D-Szenen zu rekonstruieren**, ist es notwendig *alle Faktoren der Bildaufnahme zu verstehen*
为了解释图像并重建3D场景，有必要了解图像采集的所有因素

Dazu gehört neben der Abbildung auch die **Sichtbarmachung** einer Szene
这不仅包括图片，还包括场景的可视化

Dies geschieht durch *Reflexion, Brechung und Streuung von Licht*
这是通过光的反射，折射和散射来完成的

- Sowohl die Objekteigenschaften,
- als auch die Art und Lage(n) der Lichtquelle(n) spielen dabei eine **wichtige Rolle**
物体属性以及光源的类型和位置都起着重要作用

Die **Lösung eines Bildverarbeitungsproblems** hängt maßgeblich davon ab, **ob** die Lichtverhältnisse unveränderbar vorgegeben sind, **oder** optimal gestaltet werden können
图像处理问题的解决在很大程度上取决于照明条件是否不可改变，或者是否可以最佳地设计

Falls die Beleuchtungsverhältnisse beeinflussbar sind, hilft eine **gute Abstimmung von Beleuchtung und Auswertetechnik** die **Qualität der Auswertung** entscheidend zu **verbessern**.
如果照明条件受到影响，照明和评估技术的良好协调有助于显着提高评估质量

### 4.1.2 Anwendungsbeispiel

#### 4.1.2.1 Aktive Beleuchtung

#### 4.1.2.2 Gestalt aus Schattierung

- Lage der Lichtquelle bekannt 已知光源的位置
- Annahme einer Lambertschen Oberfläche (gleichmäßige diffuse Reflexion) 朗伯表面的假设（均匀漫反射）
- Profil aus Bestrahlungsstärke 辐照度分布

### 4.1.3 Anforderungen und Auslegung

**Ziel der Beleuchtung** 照明目标：

Herstellen von homogenen Beleuchtungsbedingungen und Erzeugen eines optimalen Hell/ Dunkel-Kontrasts
创造均匀的照明条件并创造最佳的明暗对比度

**Anforderungen**
要求

- Konstanz der Beleuchtung in Wellenlänge und Intensität
照度在波长和强度上的恒定性

- bestimmte Farbzusammensetzungen (Wellenlängenbereiche)
某些颜色成分（波长范围）

- bestimmte Formgebung (Ringfeld, Langfeld)
某种形状（环场，长场）

- kein Flimmern, geringe Erwärmung
没有闪烁，轻微的变暖

**Auslegung**
解释

- Anpassung von **Wellenlängenbereichen der Lichterzeugung** an die **Empfindlichkeit des Sensors**
适应波长范围的光产生对传感器的灵敏度

- Anpassung von **Wellenlängenbereichen** und der **Beleuchtungsart an die Reflexions- und Absorbtionseigenschaften der Objekte**.
使波长范围和照明类型适应物体的反射和吸收特性

### 4.1.4 Strahlungsphysik

#### 4.1.4.1 Lichttechnik

![Alt text](Figures\Folien_4_1.png)

- **Strahlungsphysik (Radiometrie):** Beschreibt die *objektiv ausgesandte Strahlung*
辐射物理学（辐射测量学）：描述客观发射的辐射

- **Lichttechnik (Photometrie):** Beschreibt die *subjektiv vom Menschen wahrgenommene Strahlung* (berücksichtigt die Wellenlängenabhängigkeit der Empfindlichkeit des menschlichen Auges).
光技术（光度测定）：描述人体辐射主观感知（考虑到人眼灵敏度的波长依赖性）

### 4.1.5 Hellempfindlichkeitskurve

![Alt text](Figures\Folien_4_2.png)

Beschreibt den spektralen HellEmpfindlichkeitsgrad von Testpersonen bei Tageslicht (rot) und bei Nacht (blau).
描述测试对象在白天（红色）和夜晚（蓝色）的光谱亮度级别

### 4.1.6 Radiometrische Größen 辐射量

- **Strahlungsenergie**: *Summe* der Energien aller beteiligter Photonen 辐射能量：所有相关光子的能量之和
![Alt text](Figures\Folien_4_3.png)

- **Strahlungsfluss**: Energie die eine Lichtquelle *pro Zeit* emittiert 辐射流量：每次发射一个光源的能量
![Alt text](Figures\Folien_4_4.png)

- **Strahlstärke**:  Strahlungsfluss der *in einem bestimmten Raumwinkel* von einer Lichtquelle abgestrahlt wird 辐射强度：光源以给定立体角发射的辐射通量
![Alt text](Figures\Folien_4_5.png)

- **Bestrahlungsstärke**: Leistung, die *an einem Punkt x* aus *allen Richtungen* empfangen wird 辐照度：从各个方向x点接收的功率
![Alt text](Figures\Folien_4_6.png)

- **Raumwinkel**: Ist die Fläche S eines *Ausschnittes einer Kugeloberfläche* pro quadratischem Kugelradius r2 立体角：每平方球面半径r2的球面截面的面积S.
![Alt text](Figures\Folien_4_7.png)
wobei θ der Einfallswinkel der Strahlung auf die Fläche A ist. 其中θ是表面A上辐射的入射角。

### 4.1.7 Punktlichtquelle

#### 4.1.7.1 Modell

Das einfachste Modell einer Lichtquelle, ist die **Punktlichtquelle**
最简单的光源模型是点光源

Jede *beliebig geformte Lichtquelle* läßt sich durch **räumlich zusammengesetzte Punktlichtquellen modellieren**
任何任意形状的光源可以通过空间组合的点光源建模

Das *Abstrahlverhalten einer Lichtquelle* ergibt sich durch **Integration der Abstrahlungen der einzelnen Punktlichtquellen**
光源的辐射行为是由各个点光源的发射的积分产生的

Eine *isotrop ausstrahlende Punktlichtquelle* strahlt **gleichmäßig in alle Richtungen** mit einem gesamten Strahlungsfluss von
各向同性发射点光源在所有方向上均匀地辐射，总辐射通量为
![Alt text](Figures\Folien_4_8.png)

Damit ergibt sich die **Bestrahlungsstärke** durch eine Punktquelle zu
这导致通过点源的辐照度
![Alt text](Figures\Folien_4_9.png)

![Alt text](Figures\Folien_4_10.png)

Für eine Punktlichtquelle liegt eine *mit dem Abstand quadratische Abnahme* der **Bestrahlungsstärke (E)** vor
对于点光源，存在一个具有辐照度的距离二次减小的光源

Jedes *Objekt das kleiner als die Auflösung der Kamera* ist, kann als **Punktlichtquelle** aufgefasst werden
任何小于相机分辨率的物体都可以被捕获为点光源

Aber die Objekte sind normalerweise größer als die Auflösung der Kamera, **kompensiert** die *quadratisch ansteigende Größe der Fläche* den *quadratischen Abfall der Intensität*, und die **Helligkeit** kann als **entfernungsunabhängig** angenommen werden.
由于物体通常大于相机的分辨率，因此表面的二次增大尺寸补偿了强度的二次下降，并且可以假设亮度与距离无关

### 4.1.8 Strahlengang

#### 4.1.8.1 Helligkeit

**Licht** wird von *einer oder mehreren Lichtquellen ausgestrahlt*
光从一个或多个光源发射

Es trifft mit einer **gewissen Beleuchtungsstärke** auf die Objekte
它以一定程度的照度击中物体

In **Abhängigkeit** von der *Oberflächenbeschaffenheit und der Lichtdurchlässigkeit von Objekten* wird das **Licht** *unterschiedlich* **absorbiert, gebrochen und reflektiert**
根据物体的表面纹理和透光率，光被不同地吸收，破坏和反射

Ein **Bruchteil des gestreuten Lichtes** *trifft auf das Objektiv* und *beeinflusst die Helligkeit des abgebildeten Objektes*
一部分散射光照射到镜头上并影响成像物体的亮度

Ein **Oberflächenelement** erhält **nicht nur** direktes Licht von den Lichtquellen, **sondern auch** indirektes Licht von allen reflektierenden Oberflächen in der Szene.
表面元件不仅接收来自光源的直射光，还接收来自场景中所有反射表面的间接光
>Deswegen ist die **Helligkeit eines projizierten Bildpunktes** von der *Lage* und dem *Reflexionsverhalten aller Objekte* einer Szene abhängig
因此，投影像素的亮度取决于场景的所有对象的位置和反射行为

### 4.1.9 Oberflächen

#### 4.1.9.1 Reflexionen

##### 4.1.9.1.1 Gerichtete Reflexion

- **Einfallendes Licht** wird von der Oberfläche **nur** in einer Richtung reflektiert
入射光仅在一个方向上被表面反射

- Tritt bei *spiegelnden Oberflächen* auf und erzeugt **Glanzlichter**, die sich bei *geringer Lageänderung von Objekt oder Kamera verschieben* und das *Aussehen des Abbildes verändern*.
在反射表面上发生并产生高光，这些高光在物体或相机位置变化很小的情况下移动，并改变图像的外观

##### 4.1.9.1.2 Diffuse Reflexion

- Das Licht wird von der Oberfläche **in alle Richtungen gleichmäßig gestreut**
光从各个方向均匀地散射到表面

- Eine *komplett diffuse Oberfläche* nennt man auch **Lambert-Strahler**
完全漫射的表面也称为Lambert辐射器

Die *meisten Oberflächen* weisen ein **gemischtes Streuverhalten** auf, z.B lackierte Metalloberflächen.
大多数表面具有混合散射行为，例如涂漆的金属表面

### 4.1.10 Arten (6)

Durch eine **geeinete Wahl der Beleuchtung**, können *störende Reflexionen vermieden* werden
通过精心挑选的照明选择，可以避免干扰反射
- **Diffuse Beleuchtung** Beleuchtung die *aus allen Richtungen* erfolgt
散射照明来自各个方向的照明
- **Dombeleuchtung** Homogene Beleuchtung (örtlich konstantes Beleuchtungsfeld) die *aus allen Richtungen* erfolgt
圆顶照明来自所有方向的均匀照明（局部恒定照明场）
- **Koaxiale Beleuchtung** Gerichtete Beleuchtung bei der die Beleuchtungsrichtung mit der *Beobachtungsrichtung übereinstimmt*
同轴照明定向照明，其中照明方向与观察方向一致
- **Telezentrische Beleuchtung** Beleuchtung eines Objektes *durch parallel verlaufende Lichtstrahlen*
远心照明平行光束照射物体
- **Dunkelfeldbeleuchtung** Nur an aufgabenrelevante Strukturen eines Objektes erfolgt eine Lichtablenkung in das Abbildungssystem. *Alles andere bleibt dunkel*
暗场照明仅在物体的任务相关结构处是对成像系统的光偏转. 其他一切都保持黑暗
- **Hellfeldbeleuchtung** Der *überwiegende Teil einer Objektoberfläche* bewirkt eine *Lichtablenkung in das Abbildungssystem* und erscheint *hell*.
明场照明绝大多数物体表面会导致光线偏转进入成像系统并显得明亮

#### 4.1.10.1 Auflicht & Durchlicht

![Alt text](Figures\Folien_4_11.png)

Alle Arten der Beleuchtung können im Durchlicht oder Auflicht erfolgen
所有类型的照明都可以在透射或反射光下完成

![Alt text](Figures\Folien_4_12.png)

- **Durchlicht 逆光** Beleuchtung die sich in dem Halbraum befindet, der der Abbildungsoptik bezüglich des Objekts **gegenüberliegt** (“hinter dem Objekt”)
位于与成像光学器件相对的物体的半球中的透射光照射（“物体后面”）

![Alt text](Figures\Folien_4_13.png)

- **Auflicht 顺光** Beleuchtung bei der sich die Lichtquelle bezüglich des Objekts im **gleichen Halbraum** wie die Abbildungsoptik befindet (“vor dem Objekt”).
入射光照明，其中光源相对于物体处于与成像光学器件相同的半空间中（“在物体前面”）

---
## 4.2 Digitales Bild

### 4.2.1 Bildaufnahmesysteme

**Unterscheidung** zwischen
- passiven und aktiven Kamerasystemen
- unterschiedliche Frequenzbereiche

![Alt text](Figures\Folien_4_14.png)

**Beispiele**
- Digitale Kamera
 - Flächen- & Zeilenkamera
 - S/W- & Farbkamera
- Wärmebildkamera (Infrarotkamera)
- Time-of-Flight Kamera
- Dynamic Vision Sensor “Silicon Retina”

### 4.2.2 Bildaufzeichnung

#### 4.2.2.1 Prinzip

![Alt text](Figures\Folien_4_15.png)

Zur digitalen Bildaufzeichnung werden Festkörperbildsensoren (vorwiegend auf Silicium-Basis), also als flächenhafte Matrix angeordnete integrierte Halbleiterbauelemente meist auf Grundlage der CCD (Charge Coupled Devices, ladungsgekoppelte Bauelemente) eingesetzt
对于数字图像记录，固态图像传感器（主要是基于硅的），即布置为平面矩阵的集成半导体器件，主要用于CCD（电荷耦合器件，电荷耦合器件）的基础上。

Ein **CCD-Bildsensor** arbeitet in drei Stufen: CCD图像传感器分三个阶段运行：

- Die **Photonen** des einfallenden Lichtes werden **in** eine zur Beleuchtungsstärke proportionale **Ladungsmenge umgewandelt** (photoelektrischer Effekt). Integrationsdauer ≈ 20ms
入射光的光子转换成与照度成比例的量（光电效应）

- Während der **Auslesephase (< 1ms)** erfolgt der *sequentielle Transfer* der angesammelten Ladungspakete längs einer Kette von MOS-Kondensatoren (Transferregister, vertikales Schieberegister) zu einer **Auslesestufe**
在读出阶段（<1 ms）期间，累积电荷包沿着一系列MOS电容（传输寄存器，垂直移位寄存器）顺序传输到读出阶段

- In der **Auslesestufe** wird *jedes ankommende Ladungspaket* in ein zur Ladungsmenge proportionales **Spannungssignal** umgewandelt (A/D-Wandler).
在读出阶段，每个输入电荷包被转换成与电荷量成比例的电压信号（A / D转换器）

### 4.2.3 Farbaufnahmen

#### 4.2.3.1 Bayer-Filter

![Alt text](Figures\Folien_4_16.png)

Der **Bayer-Filter** ist ein Farbfilter für einen Fotosensor, angeordnet ähnlich wie ein *Schachbrett*, das zu 50% aus Grün, und je zu 25% aus Rot und Blau besteht
拜耳滤光片是一种用于光电传感器的滤色片，类似于棋盘，由50％绿色和25％红色和蓝色组成

Die **fehlenden Farbwerte** der nicht belegten Pixel in den einzelnen Farbkanälen müssen über *Interpolation künstlich erzeugt werden*
必须通过插值人工生成各个颜色通道中未占用像素的缺失颜色值

Das führt zu **Farbfehlern an Farbdiskontinuitäten**.
这导致颜色不连续性的颜色错误

#### 4.2.3.2 Foveon X3 Direkt-Bildsensor

![Alt text](Figures\Folien_4_17.png)

Der **Foveon X3** ist ein CMOS-Bildsensor bestehend aus *drei übereinander liegenden Schichten* von **Photodioden**
Foveon X3是一个CMOS图像传感器，由三层光电二极管组成

Die **unterschiedlichen Wellenlängen der Farben** Rot, Grün und Blau werden in *unterschiedlichen Schichten absorbiert*, weil **langwelliges (rotes) Licht** in Silizium eine *größere Eindringtiefe* hat, als kurzwelliges (blaues)
红色，绿色和蓝色的不同波长被不同层吸收，因为硅中的长波（红色）光比短波（蓝色）具有更大的穿透深度

**Jede der Schichten** hat eine eigene *Farbempfindlichkeit*
每个层都有自己的颜色灵敏度

Damit läßt sich die **Farbempfindlichkeit** des menschlichen Auges *relativ gut nachbilden*.
这允许人眼的颜色灵敏度相对较好地模拟

#### 4.2.3.3 Vergleich

![Alt text](Figures\Folien_4_18.png)

### 4.2.4 Digitalisierungsfehler

#### 4.2.4.1 Überblick
![Alt text](Figures\Folien_4_19.png)
- **Bildrauschen**
噪音
- **Smear & Blooming**: Überschreiten der Ladungsmenge durch Überbelichtung
涂抹和绽放：超过曝光过度导致的电荷量
- **Moiré-Muster**: Periodische Muster auf einem Objekt werden durch eine unzureichend aufgelöste Bildrasterung unterabgetastet. Dadurch entstehen “Scheinmuster” (Aliasing-Effekt)
莫尔条纹图案：对象上的周期性图案由未充分分辨的帧进行二次采样. 这会产生“虚拟图案”（锯齿效果）
- **Kompressionsartefakte** z.B. jpeg 压缩

#### 4.2.4.2 Bildrauschen

Gründe für das **Bildrauschen bei CCD Sensoren**
CCD传感器产生图像噪声的原因
- **Pixelvariabler Dunkelstrom** (z.B. wegen Temperaturerhöhung) und Rauschen des **Ausleseverstärkers**
像素可变暗电流（例如， 由于温度升高）和读出放大器的噪声
- **Photonenrauschen**, **Schwankungen der Lichtempfindlichkeit** eines Pixels
光子噪声，像素光敏度的变化
- **Pixelgröße und Pixelabstand**: Je kleiner desto mehr Rauschen
像素大小和像素间距：噪点越小
- **Quantisierungsrauschen**
量化
- **Belichtungszeit**: Je länger desto mehr Rauschen
快门速度：噪音越大

### 4.2.5 Funktionsprinzipien unterschiedlicher Typen

#### 4.2.5.1 Zeilenkamera

![Alt text](Figures\Folien_4_20.png)

**Eigenschaften/Besonderheiten** 属性/特殊功能
- Auflösungen bis 12288 Pixel in X-Richtung, in **Transport-Richtung** ist die *Auflösung (fast) beliebig*
在X方向上分辨率高达12288像素，在传输方向上，分辨率（几乎）是任意的
- Kamera oder Objekt **muss bewegt** werden
需要移动相机或物体
- einfachere **Beleuchtung** (linienförmig)
更简单的照明（线性）
- höhere **Beleuchtungsstärken** realisierbar
可以实现更高的照度水平
- Einsatz vor allem bei **Scannern und Inspektion**
尤其适用于扫描仪和检查

#### 4.2.5.2 Aktive Kamera

##### 4.2.5.2.1 Laufzeitkamera

###### 4.2.5.2.1.1 PMD (Photonic Mixer Device)

![Alt text](Figures\Folien_4_21.png)

Funktionsweise eines **PMD-Sensors** (Photonic Mixer Device)
PMD传感器的工作原理（光子混合器装置）
- Gepulstes oder moduliertes Infrarotlicht
脉冲或调制红外光
- Zeit- oder Phasenverschiebung zwischen emittierten und empfangenen Lichtwellen kodiert Entfernung
发射和接收光波之间的时间或相移编码距离

**Gepulstes Infrarotlicht**
脉冲红外线

![Alt text](Figures\Folien_4_23.png)
(n -- 折射率)

Licht durchläuft 1cm in 33ps. D.h., **sehr genaue Zeitmessungen nötig**. 光线以33ps的速度穿过1cm。 也就是说，需要非常精确的时间测量。

**Moduliertes Infrarotlicht** 调制红外光

![Alt text](Figures\Folien_4_24.png)
![Alt text](Figures\Folien_4_22.png)

**Fehlerquellen**
错误的来源
- **Mehrdeutigkeiten** bei periodischem Trägersignal
具有周期性载波信号的模糊度
- **Intensitätsabhängigkeit** der Tiefenmessung
深度测量的强度依赖性
- **Umgebungslicht** beeinflusst Messqualität
环境光会影响测量质量
- **Bewegungsartefakte**
运动伪影
- **Temperaturdrift**
- **Rauschen**

##### 4.2.5.2.2 Strukturiertes Licht

###### 4.2.5.2.2.1 Prinzip

Funktionsweise bei **strukturiertem Licht**
使用结构光
- Projektor **projiziert ein Lichtmuster** einer bestimmten Struktur und Wellenlänge auf eine Szene
投影仪将特定结构和波长的光投射到场景上
- Aus dem **Abbild der Verzerrung des Lichtmusters** wird das 3D Profil rekonstruiert (Verschiebung der Punkte)
从光图案的扭曲图像中，重建3D轮廓（点的位移）
- **Voraussetzung** für fehlerfreie Rekonstruktionen ist ein *vollständig kalibriertes Projektor-Kamera-System*.
无差错重建的先决条件是完全校准的投影仪 - 相机系统

###### 4.2.5.2.2.2 Beispiel Microsoft KINECT

**Funktionsprinzip** des KINECT-Sensors
KINECT传感器的功能原理
- Infrarot Laser Projektor **projiziert ein Punktmuster** auf die Szene
红外激光投影仪将点图案投射到场景上
- **Infrarotkamera (CMOS)** mit einer Auflösung 1600x1200 Pixel nimmt das Abbild der **Verzerrung des Punktemusters** auf
分辨率为1600x1200像素的红外相机（CMOS）拾取点图案失真的图像
- **Farbkamera (CMOS)** mit einer Auflösung von 640x480 Pixel nimmt die **Bestrahlungsstärke** des sichtbaren Lichts auf
分辨率为640x480像素的彩色相机（CMOS）吸收可见光的辐照度
- **Verzerrtes Punktemuster und Bestrahlungsstärken** werden zu einem farbgetreuen 3D Profil mit einer Bildwiederholrate von 30 Hz in Echtzeit umgerechnet
扭曲的点图案和辐照度被实时转换为帧频为30 Hz的真彩色3D轮廓

![Alt text](Figures\Folien_4_25.png)
![Alt text](Figures\Folien_4_26.png)

**Fehlerquellen**
错误的来源
- **Infrarotes Umgebungslicht** beeinflusst Messqualität
红外环境光影响测量质量
- Es kann **nur ein Sensor** gleichzeitig betrieben werden (ansonsten Mehrdeutigkeiten durch mehrere Muster).
只能同时操作一个传感器（否则会出现多种模式的模糊）
