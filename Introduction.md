
# Introduction and Overview

## 1.1 物理信息学

信息：在物理系统中的一种编码.

### 信息的里程碑

**Landauer’s principle**:信息的擦除是一种耗散过程.信息的擦除一定会带来相空间的压缩,也是不可逆的.
举例：在活塞将气体分子都压向左侧时气体的熵减小.每移除1bit信息至少需要做$\Delta S = k \ln 2$的功.

**Reversible** **computation**:逻辑门一般认为是不可逆的.
**麦克斯韦妖**: 妖怪必须收集盒子里气体分子的信息,而妖怪的记忆存储是有限的,最终信息需要被抹除.于是最终我们还是需要付出能量.

## 1.2 量子信息

从根本上讲，宇宙是遵守量子力学法则的.对于信息的经典看法应该用量子的观点替代.

量子力学带来的一些改变:

- 存在真正的随机性
- 非对易性的物理量不能精确测量
- 对物理系统的测量不可避免地对系统的状态产生影响
- 量子信息不能被完美复制(Wootters and Zurek and by Dieks, 1982)

## 1.3 有效的量子算法

量子理论对我们对计算的理论有着深远的影响.(举例:大数的质因数分解,量子计算机对RSA加密算法的破解是多项式复杂度)

## 1.4 量子的复杂性

量子系统可以进行计算的结论在1982年被Paul Benioff和 Richard Feynman分别独立指出.
理解Feynman的观点需要从量子信息与计算的数学描述出发.

描述传统信息的最小单位是比特,而描述量子信息的最小单位是量子比特(quantum bit),又被叫做$qbit$.$qbit$是在二维复空间中的一个带内积的复向量,和经典比特不同,我们把在这个空间中的正交基分别称为$\left|0 \right>$和$\left|1 \right>$,则一个单位向量可以写为 
$$\left| \psi \right> =a\left| 0 \right> + b\left| 1 \right>,|a|^2 + |b|^2 = 1$$
其中$a,b \in \bf{C}$,在测量时我们无法测量到这个向量的具体状态,我们得到的是得到$\left|1 \right>$和$\left|0 \right>$的概率.N个量子比特可以使用一个$2^N$维空间描述.
$$\left| 01110010\cdots 1001\right>$$
它可以在基上被展开为
$$\sum_{x=0}^{2^N-1}a_x\left| x \right>$$
量子计算的过程可以这样描述:我们制作$N$个量子比特,使它们处于一个标准的初态,比如$\left|0 \right>\left|0 \right>\cdots\left|0 \right>$,或者$\left| x=0\right>$,然后我们在这些量子比特上施加一个酉变换$U$,再在基底$\{ \left| 0\right> ,\left| 1\right> \}$上测量这些量子比特,测量得到的结果就是计算的结果.
量子计算的算法是概率算法,也就是重复运行会产生不同的结果.量子计算有一个合理的概率得到正确结果.

经典计算机难以模拟得到量子计算机运行的结果.

## 1.5 量子并行计算(?)Quantum parallelism

我们假设有一个量子黑箱$f(x)$,我们想要在一段时间内同时进行两个计算,假设有这样一个变换矩阵
$$U_f:\left|x\right>\left|y\right> \rightarrow \left|x\right>\left|y \oplus f(x)\right>$$
我们可以选择一个输入为$\left|0\right>$和$\left|1\right>$的叠加.如果初态为$\frac{1}{\sqrt{2}}(\left|0\right>-\left|1\right>)$,那么
$$U_f : \frac{1}{\sqrt{2}}(\left|0\right>+\left|1\right>)\frac{1}{\sqrt{2}}(\left|0\right>-\left|1\right>) \rightarrow$$
$$\frac{1}{\sqrt{2}}\left[ (-1)^{f(0)}\left|0\right> + (-1)^{f(1)}\left|1\right>\right]\frac{1}{\sqrt{2}}(\left|0\right>-\left|1\right>)$$
最终,我们可以把第一个量子比特在如下基上展开
$$\left|\pm\right> = \frac{1}{\sqrt{2}}(\left|0\right>\pm\left|1\right>)$$
假设我们有一个作用在$N$个比特上的方程,它有可能有$2^N$种可能的参数.在传统计算机上我们需要计算$2^N$次,但是在量子计算机中,我们可以选择这样一个输入函数
$$\left[\frac{1}{\sqrt{2}}(\left|0\right>-\left|1\right>)\right]^N = \frac{1}{2^{N/2}}\sum_{x=0}^{2^N-1}\left|x\right>,$$
我们可以得到一个态
$$\frac{1}{2^{N/2}}\sum_{x=0}^{2^N-1}\left|x\right>\left|f(x)\right>,$$

## 1.6 对复杂度的新分类

时间复杂度、空间复杂度.传统的复杂度计算方法对量子计算机似乎并不适用.

## 1.7 计算错误

量子计算机的错误纠正.量子比特不可避免会与外界环境发生相互作用,将一个较大的量子系统与外界隔离是很难做到的.量子系统与外界的相互作用会导致量子系统的状态坍缩到一个值,也被称为退相干(decoherence).

退相干并不是唯一的问题,假设我们能完美地将量子系统与外界环境隔离,但我们仍然不能认为量子计算机能完美完成运算.在运算时微小错误的累积会导致计算的错误.

为了提升量子门的表现,我们在每次门后冷却量子比特.但是我们不能对量子计算机做这种冷却,与环境的相互作用会导致导致计算机的退相干.

一个较为复杂的方法是使用纠错码.量子纠错码的困难:
- 态错误,错误的种类更多: $\left|0\right> \rightarrow \left|1\right>, \left|0\right> \rightarrow -\left|0\right>$.
- 错误更小.$a\left|0\right>+b\left|1\right>$中的$a$与$b$可能会被改变,传统的纠错码被设计为寻找比特错误这样的明显错误.
- 测量会导致扰动.
- 量子系统无法精确复制.

## 1.8 量子纠错码

Peter Shor首次提出了第一种量子纠错码的样例.

## 1.9 量子硬件

量子硬件必须满足一些严格的条件:
- **存储**:将量子比特存储足够长的时间.
- **隔离**:量子比特必须与环境很好地隔离.
- **读取**:我们需要方便快捷地读取量子比特的状态.
- **门**:我们需要操纵单个量子比特的状态,并向量子比特施加受控的作用.
- **精确度**:量子门需要有足够的精度.

### 1.9.1 离子阱

一种可能的达到以上目标的方式由Ignacio Cirac和Peter Zoller提出并由Dave Wineland的研究组加以发展.在这个方法中，每个量子比特由一个离子携带.每个离子的量子态是粒子基态$\left|g\right>$(视为$\left|0\right>$)和一个特殊的长寿命的激发态$\left|e\right>$(视为$\left|1\right>$),这两个能级的相干叠加
$$a\left|g\right>+be^{i\omega t}\left|e\right>$$
在$\{\left|g\right>,\left|e\right>\}$的基底上测量离子的状态是很简单的.一束短激光可以把离子从状态$\left|g\right>$转变到一个短时的激发态$\left|e^{'}\right>$,当激光照明离子时,在状态$\left|0\right>$的离子持续吸收释放光子,而在状态$\left|1\right>$的离子保持不变.

由于离子之间的库伦斥力，这些离子之间是分开的，可以使用激光脉冲来分别定位.如果精确控制激光脉冲的强度和相位,就可以控制量子态.

### 1.9.2 Cavity QED

Jeff Kimble’s的实验组利用光腔控制了一些中性原子.

另外一种可能是在质子的极化中存储量子比特.

### 1.9.3 NMR

nuclear magnetic resonance technology.量子比特由核自旋携带.量子比特可以存在较长的时间.

## 1.10 总结
- 量子计算机可以解决复杂的问题
- 量子计算的错可以被纠正
- 量子计算的硬件可以实现

# Foundations I: States and Ensembles

## 2.1 Axioms of quantum mechanics 量子力学的公理

 在本章以及下一章中我们主要讨论开放量子系统的理论.我们说一个系统是开放系统,主要是因为它并没有与外界完美隔离,与外界环境交换物质与能量.研究这一类系统的动机是在现实中的系统都是开放系统.

 为了理解一个开放系统$S$的行为,我们把$S$和他所处的外界环境$E$结合在一起视为一个系统.

 ### 公理一: 态

态是一个物理系统状态的完整描述.在量子力学中,一个态是希尔伯特空间中的一个矢量.

**希尔伯特空间**:
- 一个在复数域上的矢量空间,向量被写作$\left|\psi\right>$(狄拉克符号)
- 有一个*内积*$\left<\varphi|\psi\right>$将按顺序的一对矢量映射到$\mathbb{C}$中,它有如下性质:
   1. 模为正:$\left<\psi|\psi\right> >0$
    2. 线性性:$\left<\varphi |(a|\psi_1\right> + b|\psi_2) = a\left<\varphi|\psi_1\right>+b\left<\varphi|\psi_2\right>$.
   3. 斜对称性: $\left<\varphi|\psi\right> = \left<\psi|\varphi\right>^{*}$.
- 在范数为$||\psi|| = \left<\varphi|\psi\right> = \left<\psi|\varphi\right>^{\frac{1}{2}}$是*complete*的.(不太会翻译这个词)

### 公理二: 可观测量

可观测量是一个可以被观测的物理量.在量子物理中,一个可观测量是一个自伴算子.
在希尔伯特空间$\mathcal{H}$中的自伴算子有谱表示方法,它的本征矢量在希尔伯特空间中形成一组正交的基.我们可以把算符$\bf{A}$表示为
$$\bf{A} = \sum_{n} a_n\bf{E}_n.$$
其中$a_n$为$\bf{A}$的一个本征值,$\bf{E}_n$是在相互正交的本征向量组成的空间中对应本征值的矢量.它们满足
$$\bf{E}_n\bf{E}_m = \delta_{n,m}\bf{E}_n.$$
$$\bf{E}_n^{\dagger} = \bf{E}_n$$
由$\left| \psi \right>$在一维空间展开的正交算符可以被写作$\left| \psi \right>\left< \psi \right|$,算符$\bf{A}$的谱表示为
$$ \bf{A} = \sum_{n} \left| \psi \right>a_n\left< \psi \right|, $$
其中 $\{\left| n \right>\}$是$\bf{A}$的一组正交基,有$\bf{A}\left|n\right> = a_n\left|n\right>$.

### 公理三: 测量

测量是物理系统的状态被某个探测器获得的过程.在量子物理中,对一个可观测的量$\bf{A$的测量会获得$\bf{A$的一个本征状态,测量得到这个态对应的本征值.假设这个态是$\left| \psi \right>$