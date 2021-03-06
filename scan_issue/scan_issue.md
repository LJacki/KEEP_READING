## 扫描顺序对显示产生分界的影响
### 现象阐述

1. 当前SRS5020的基板设计是上下驱动电路镜像的方式；
2. 若上，下屏幕均从左上角开始扫描，中间屏幕分界线在低灰度显示明显；
3. 若上屏幕从左上角开始，下屏幕从左下角开始，会有分界线处较黑的现象；
4. 若上屏幕从左下角开始，下屏幕从左上角开始，会有分界线出较亮的现象；

### 猜测

- [ ] 3、4两种现象是否也是在低灰度的时候产生？
- [ ] 是不是低灰度的闪烁增加了这种分界的感觉？
- [ ] 是否可以调整为全屏幕扫描的方式，减弱这种分界效果？

## 低灰度显示不均匀与灰度反转

## 现象阐述

1. 低灰度0\~15\~32灰度显示不均匀，过度亮度明显，不符合gamma 2.2的关系；
2. 3灰度比4灰度亮度亮；从数字扫描的逻辑上看是1/2 + 1/4 的的亮度大于 1 的亮度；

## 猜测

因为之前都是假设LED的显示亮度与显示时间从PWM方式控制方式上是成正比，但实际情况并非如此。

很显然，对于两个子帧都进行清行显示的亮度在实际效果累加起来，就是比LED平稳的显示对应的亮度要亮。

这里可以猜测，LED瞬间开关的亮度是可能先达到峰值，随后平稳下来的亮度比刚打开的时候亮度低。

所以说，通过清行的方式，将两个子帧叠加，不仅要考虑时间的影响，也要考虑次数的影响；

## 低灰度闪烁

## 现象阐述

举例为1灰度的时候，因1帧中，只有第1子帧的1/16是进行发光的，这样相当于刷新频率降低了19倍，相对于之前的19 * 120 频率，容易观察出闪烁。

## 猜测

将1灰度拆分，进行多次闪烁，但可能回引起上述，打开次数多，灰度变亮的现象。

## 实验步骤

上述问题，进行讨论，再确定进行试验或验证时间。

详细实验步骤可分为：

### 实验准备

- [ ] 确定7040驱动地板和显示芯片的数量，以及可以参与实验的显示状态完好的屏幕。
- [ ] 确定实验条件，按照优先级及实验时间长短进行划分。
- [ ] 确定实验条件，比如需要使用亮度计还是需要观察，使用亮度计的方式等。

