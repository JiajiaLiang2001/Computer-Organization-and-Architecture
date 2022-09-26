- [第 2 章 计算机系统中的数据表示](#第-2-章-计算机系统中的数据表示)
  - [2.1 数值数据的编码](#21-数值数据的编码)
    - [原码](#原码)
      - [举例](#举例)
    - [补码](#补码)
      - [举例](#举例-1)
    - [反码](#反码)
      - [举例](#举例-2)
    - [移码](#移码)
    - [习题](#习题)
    - [数据的浮点表示](#数据的浮点表示)
  - [2.2 非数值数据编码](#22-非数值数据编码)
  - [2.3 检错与纠错码](#23-检错与纠错码)

# 第 2 章 计算机系统中的数据表示

**进位计数制**：二进制，十进制，八进制和十六进制。

| 进位计数制 | 基数 | 位权   | 标记符号 | 意义       | 数码                                                         |
| ---------- | ---- | ------ | -------- | ---------- | ------------------------------------------------------------ |
| 二进制     | $2$  | $2^i$  | $B$      | 逢二进一   | $0 \text { 和 } 1$                                           |
| 十进制     | $10$ | $10^i$ | $D$      | 逢十进一   | $0 \sim 9$                                                   |
| 八进制     | $8$  | $8^i$  | $O$      | 逢八进一   | $0 \sim 7$                                                   |
| 十六进制   | $16$ | $16^i$ | $H$      | 逢十六进一 | $0 \sim 9 、 \mathrm{~A}、 \mathrm{~B} 、 \mathrm{C} 、 \mathrm{D}、 \mathrm{E} 、 \mathrm{~F}$ |

任何一种进位计数制表示的数都可以写成按权展开的多项式之和。
$$
N_r=\sum_{i=m-1}^{-k} D_i \times r^i
$$
**数值数据**：数量多少和数值大小的数据，即在数轴上能找到其对应点的数据。

**机器数**：各种数值数据在计算机中表示的形式。

**真值**：机器数对应的实际数值。

**无符号数**：没有符号的数，数的每一位均用来表示数值。

**有符号数**：机器无法直接识别正负号，而正负恰好是两种截然不同的状态，用 0 表示 正，用 1 表示负，符号也被数字化，再将符号放在有效数字前面。

**定点数**：在机器数表示中，约定小数点的位置固定不变。

- **定点整数（纯整数，小数点定在最低有效数值位之后）**
- **定点小数（纯小数，小数点定在最低有效数值位之前）**

<div align=center>
  <img src="images\定点数.png" title="定点数" height="50%" width="50%">
</div>


**浮点数**：在机器数表示中，约定小数点的位置浮动。

基数为 $2$ 的数 $F$ 的浮点表示：$F=M \times 2^E$ （$M$：尾数，带符号的纯小数，$E$：阶码，带符号的纯整数）

> 浮点数 $\longrightarrow$ 尾数（定点小数） $+$ 阶码（定点整数），浮点数用定点数表示。

<div align=center>
  <img src="images\浮点数.png" title="浮点数" height="50%" width="50%">
</div>

## 2.1 数值数据的编码

<div align=center>
  <img src="images\定点小数与定点整数.png" title="定点小数与定点整数" height="50%" width="50%">
</div>


$\color{red}{注：X为真值。}$



### 原码

**原码**：符号位为 $0$ 表示正数，符号位为 $1$ 表示负数，数值为即真值绝对值。

$\color{green}{整数原码}$：



$$
[X]_{\text {原 }}=
\begin{cases}
X &0 \leq X < 2^{n-1}\\
2^{n-1}-X &-2^{n-1} < X \leq 0
\end{cases}
$$

$\color{green}{纯小数原码}$：



$$
[X]_{\text {原 }}=
\begin{cases}
X &0 \leq X < 1\\
1-X &-1 < X \leq 0
\end{cases}
$$



表示范围：原码 $n$ 位（包括一位符号位）

- 整数：$-\left(2^{n-1}-1\right) \sim+\left(2^{n-1}-1\right)$
- 纯小数：$-\left(1-2^{-(n-1)}\right) \sim+\left(1-2^{-(n-1)}\right)$



#### 举例

举例：采用 $8$ 位二进制编码

$X=+35$ $\longrightarrow$ $[X]_{\text {原 }}=00100011$

$X=-35$ $\longrightarrow$ $[X]_{\text {原 }}=10100011$

$X=+0.46875$ $\longrightarrow$ $[X]_{\text {原 }}=0.0111100$

$X=-0.46875$ $\longrightarrow$ $[X]_{\text {原 }}=1.0111100$



### 补码

**无模运算**

假定 $M$ 为**模**，若数 $a$、$b$ 满足 $a＋b＝M$，则称 $a$ 、$b$ 互为**补数**。

**有模运算**：在有模运算中，减去一个数等于加上这个数对模的补数。

<div align=center>
  <img src="images\有模运算.png" title="有模运算" height="50%" width="50%">
</div>



**补码**：

$$
[X]_{{ }^补}=M+X=
\begin{cases}
X &X \geq 0\\
M-|X| &X<0 
\end{cases}
$$

$\color{green}{整数补码}$：



$$
[X]_{{ }^补}=
\begin{cases}
X &0 \leq X < 2^{n-1}(\leq 2^{n-1}-1)\\
2^n+X &-2^{n-1} \leq X < 0 
\end{cases}\quad(\bmod 2^n)
$$

$\color{green}{纯小数补码}$：



$$
[X]_{{ }^补}=
\begin{cases}
X &0 \leq X < 1(\leq 1-2^{-(n-1)}) \\
2+X &-1 \leq X < 0 
\end{cases}\quad(\bmod 2)
$$



表示范围：补码 $n$ 位

- 整数：$-2^{n-1} \sim+\left(2^{n-1}-1\right)$
- 纯小数：$-1 \sim+\left(1-2^{-n+1}\right)$



$\color{green}{补码的符号位}$：“0”表示负，“1”表示正。 

证明：

小数：


$$
0 \leq X<1,[X] \text { 补 }=X \longrightarrow 0 \leq[X] \text { 补 }<1
$$

$$
-1 \leq X<0,[X] \text { 补 }=2+X \longrightarrow 1 \leq[X] \text { 补 }<2
$$



整数：


$$
0 \leq X<2^{n-1},[X] \text { 补 }=X \longrightarrow 0 \leq[X] \text { 补 }<2^{n-1}
$$

$$
-2^{n-1} \leq X<0,[X] \text { 补 }=2^n+X \longrightarrow 2^{n-1} \leq[X] \text { 补 }<2^n
$$



$\color{green}{补码中0唯一}$


$$
\begin{aligned}
&{[+0] \text { 补 }=0.0000000} \\
&{[-0] \text { 补 }=2+(-0.0000000)=10.0000000-0.0000000=0.0000000}
\end{aligned}
$$


$\color{green}{负数的补码值大于正数的补码值}$



**$\color{green}{补码，真值，原码相互转换}$**

小数部分证明：

当 $X \geq 0$：$X=[X]{\text {原 }}=[X]{\text {补 }}$

当 $\begin{equation}
X<0
\end{equation}$ ：

- 真值绝对值 $\longrightarrow$ 补码


$$
\begin{aligned}
&[X] \text { 补 }=2+X\\
&=\overbrace{1.11 \cdots \cdots 1}^{n \text { 个 } 1}+X+\overbrace{0.00 \cdots \cdots 01}^{n-1 \text { 个 } 0} 1\\
&=\underbrace{\overbrace{1.11 \cdots \cdots 1}^{n \text { 个 } 1}-|X|}|X| \text { 按位取反 }+\overbrace{0.00 \cdots \cdots 01}^{n-1 \text { 个 } 0} 1
\end{aligned}
$$


- 补码 $\longrightarrow$ 真值绝对值


$$
[X] \text { 补 }=2+X \longrightarrow-X=2-[X] \text { 补 }
$$


又 $-X=|X|$


$$
\begin{aligned}
&|X|==-X=2-[X]_{\text {补 }}\\
&=\underbrace{\overbrace{1.11 \cdots \cdots 1}^{n \text { 个 } 1}-[X]_{\text {补 }}}_{|X| \text { 按位取反 }}+\underbrace{\overbrace{0.00 \cdots \cdots 0}^{n-1 \text { 个 } 0}}_{\text {末位加一 }} 1
\end{aligned}
$$


$\color{red}{“按位取反，末尾加一”}$快捷操作： $X \cdots X X \quad 10 \cdots 00$ $\longrightarrow$  $\overline{\mathrm{X}} \cdots \overline{\mathrm{X}} \overline{\mathrm{X}} \quad 10 \cdots 00$



<div align=center>
    <img src="images\补码-真值-原码1.png" title="补码-真值-原码1" height="50%" width="50%">
  <img src="images\补码-真值-原码2.png" title="补码-真值-原码2" height="50%" width="50%">
</div>




$\color{green}{补码的符号位扩展}$

- 定点小数：在其低位填充适当位数的 $0$ 
- 定点整数：直接左侧填充 “符号位”

证明：

- 小数，直接联想补码与真值绝对值互相转换的逻辑即可

- 整数

  要将 $n$ 位定点整数补码用 $2n$ 位表示，如何处理？

  - $M O D ~2^n[X]_{\text {补 }}$：表示 $X$ 以 $2^n$ 为模的补码
  - $M O D ~2^{2n}[X]_{\text {补 }}$：表示 $X$ 以 $2^{2n}$ 为模的补码


$$
\operatorname{MOD} 2^n[X]_{\text {补 }}=\{\begin{array}{ll}
X & 0 \leq X<2^{n-1} \\
2^n+X & -2^{n-1} \leq X<0
\end{array} \quad \text { MOD } 2^n
$$

$$
\operatorname{MOD~}^{2 n}[X]_{\text {补 }}=\{\begin{array}{cc}
X & 0 \leq X<2^{2 n-1} \\
2^{2 n}+X & -2^{2 n-1} \leq X<0
\end{array} \quad \text { MOD } 2^{2 n}
$$


当 $X \geq 0$ ，


$$
\begin{aligned}
\operatorname{MOD} 2^{2 n} & {[X]_{\text {补 }}=X=\operatorname{MOD}2^n[X]_{\text {补 }} } \\
&=\underbrace{00 \cdots}_{2n \text {个 } 0}+\operatorname{MOD} 2^n[X]_{\text {补 }} \\
&=\underbrace{00 \cdots \cdots 0}_{n \text {个 } 0} \text { MOD } 2^n[X]_{\text {补 }}
\end{aligned}
$$


当 $X < 0$，


$$
\begin{aligned}
\operatorname{MOD} 2^{2 n}[X]_{\text {补 }} &=2^{2 n}+X=2^{2 n}+\left(-2^n+\operatorname{MOD}2^n[X]_{\text {补 }}\right) \\
&=\underbrace{100 \cdots \cdots 0}_{2 n \text {个 } 0}-\underbrace{100 \cdots \cdots 0}_{n \text {个 } 0}+\operatorname{MOD} 2^n[X]_{\text {补 }} \\
&=\underbrace{111 \cdots \cdots 1}_{\mathrm{n} \text {个 } 1} \underbrace{00 \cdots \cdots 0}_{\mathrm{n} \text {个 } 0}+\operatorname{MOD} 2^n[X]_{\text {补 }} \\
&=\underbrace{111 \cdots \cdots 1}_{\mathrm{n} \text {个 }1} \operatorname{MOD} 2^n[X]_{\text {补 }}
\end{aligned}
$$


$\color{green}{补码的算术右移（除2运算）}$：符号位不变，按位右移一位。

这里只讨论小数

当 $X \geq 0$ ，


$$
\begin{aligned}
&{[X]_{\text {补 }}=X} \\
&{\left[\frac{1}{2} X\right]_{\text {补 }}=\frac{1}{2} X=\frac{1}{2}[X]_{\text {补 }}=0 \cdot 2^0+\frac{1}{2}[X]_{\text {补 }}}
\end{aligned}
$$


当 $X < 0$，


$$
\begin{aligned}
&{[X]_{\text {补 }}=2+X} \\
&{\left[\frac{1}{2} X\right]_{\text {补 }}=2+\frac{1}{2} X=2+\frac{1}{2}\left(-2+[X]_{\text {补 }}\right)=1 \cdot 2^0+\frac{1}{2}[X]_{\text {补 }}}
\end{aligned}
$$


两式合并：


$$
\left[\frac{1}{2} X\right]_{\text {补 }}=X_S \cdot 2^0+\frac{1}{2}[X]_{\text {补 }}
$$


$\color{green}{补码的算术左移（乘2运算）}$：按位左移一位，末位补0。

证明：


$$
\begin{aligned}
&{[X]_{\text {补 }}=2+X \quad \text { MOD } 2} \\
&{[2 X]_{\text {补 }}=4+2 X \quad \text { MOD } 4} \\
&{[2 X]_{\text {补 }}=4+2 X=4+2\left(-2+[X]_{\text {补 }}\right)=2[X]_{\text {补 }}}
\end{aligned}
$$


$\color{red}{可能存在溢出，解决方法}$：

**变形补码**：采用双符号位。左符是真正的符号位，右符用来判别“溢出”。

当使用变形补码（双符号位）进行运算时，

- 若运算结果的两个符号位相同，则不发生溢出；
- 若运算结果的两个符号位相异，则结果溢出。
  - 最高位为符号；
  - 次高位为溢出的数值而非符号。

**溢出处理**：将 CPU 中状态寄存器的溢出标志位置位，转入溢出处理程序进行相应的处理。



#### 举例

采用 $8$ 位二进制编码

特殊的：

$X=0$ $\longrightarrow$ $[X]_{\text {补 }}=X=00000000$

$X=-1$ $\longrightarrow$ $[X]_{\text {补 }}=M-|X|=100000000-00000001=11111111$

$X=-128$ $\longrightarrow$ $[X]_{\text {补 }}=M-|X|=100000000-10000000=10000000$

普遍的：

$X=+35$ $\longrightarrow$ $[X]_{\text {补 }}==00100011$

$X=-35$ $\longrightarrow$ $[X]_{\text {补 }}=M-|X|=100000000-00100011=11011101$

$X=+0.46875$ $\longrightarrow$ $[X]_{\text {补 }}=0.0111100$

$X=-0.46875$ $\longrightarrow$ $[X]_{\text {补 }}=M-|X|=10.000000-0.0111100=1.1000100$

整数：

| 真值             | 原码                                    | 补码                            |
| :--------------- | :-------------------------------------- | :------------------------------ |
| $X_1=+0.1011001$ | $[X_1]_{\text {原 }}=0.1011001$         | $[X_1]_{\text {补 }}=0.1011001$ |
| $X_2=0$          | $[X_2]_{\text {原 }}=00000000=10000000$ | $[X_2]_{\text {补 }}=00000000$  |
| $X_3=-0.1101100$ | $[X_3]_{\text {原 }}=1.1101100$         | $[X_3]_{\text {补 }}=1.0010100$ |

小数：

| 补码                                       | 真值             | 原码                            |
| ------------------------------------------ | :--------------- | :------------------------------ |
| $\left[X_1\right]_{\text {补 }}=0.1010110$ | $X_1=+0.1010110$ | $[X_1]_{\text {原 }}=0.1010110$ |
| $\left[X_2\right]_{\text {补 }}=1.1100101$ | $X_2=-0.0011011$ | $[X_2]_{\text {原 }}=1.0011011$ |
| $\left[X_3\right]_{\text {补 }}=1.0000000$ | $X_3=-1.0000000$ | 超出范围                        |



### 反码

**反码**：

$\color{green}{整数反码}$：


$$
[X]_{{ }^反}=
\begin{cases}
X &0 \leq X < 2^{n-1}(\leq 2^{n-1}-1)\\
(2^n-1)+X &-2^{n-1} \leq X < 0 
\end{cases}\quad(\bmod 2^n-1)
$$


$\color{green}{纯小数反码}$：


$$
[X]_{{ }^反}=
\begin{cases}
X &0 \leq X < 1(\leq 1-2^{-(n-1)}) \\
(2-2^{-n+1})+X &-1 < X \leq 0 
\end{cases}\quad(\bmod (2-2^{-n+1}))
$$


表示范围：反码 $n$ 位

- 整数：$-2^{n-1} \sim+\left(2^{n-1}-1\right)$
- 纯小数：$-1 \sim+\left(1-2^{-n+1}\right)$



**$\color{green}{反码，真值，原码相互转换}$**

<div align=center>
  <img src="images\反码-原码-真值.png" title="反码-原码-真值" height="50%" width="50%">
</div>




#### 举例

采用 $8$ 位二进制编码

$X=+35$ $\longrightarrow$ $[X]_{\text {反 }}==00100011$

$X=-35$ $\longrightarrow$ $[X]_{\text {反 }}=(2^8-1)+(-35)=11111111-00100011=11011100$

$X=+0.46875$ $\longrightarrow$ $[X]_{\text {反 }}=0.0111100$

$X=-0.46875$ $\longrightarrow$ $[X]_{\text {反 }}=(2-2^{-8+1})+(-0.46875)=1.1111111-0.0111100=1.1000011$



### 移码

**移码**：移码多用于浮点数中表示阶码，均为整数。

$\color{green}{整数移码}$：


$$
[X]_{\text {栘 }}=2^{n-1}+X \quad\left(-2^{n-1} \leq X<2^{n-1}\right) \quad\left(\bmod 2^n\right)
$$



<div align=center>
  <img src="images\移码在数轴上的表示.png" title="移码在数轴上的表示" height="50%" width="50%">
</div>



$\color{green}{移码的符号位}$：“0”表示负，“1”表示正。 

证明：

- 当 $-2^{n-1} \leq X < 0$ ，$0 \leq [X]_{\text {移 }} < 2^{n-1}$ ， 符号位为 $0$
- 当 $0 \leq X < 2^{n-1}$ ，$2^{n-1} \leq [X]_{\text {移 }} < 2^n$ ，符号位为 $1$



$\color{green}{移码与补码的相互转换}$


$$
[X]_{\text {移 }}=2^{n-1}+X \quad-2^{n-1} \leq X<2^{n-1}
$$

$$
[X]_{\text {补 }}=\left\{\begin{array}{ll}
X & 0 \leq X<2^{n-1} \\
2^n+X & -2^{n-1} \leq X<0
\end{array} \quad \operatorname{MOD~}^n\right.
$$


<div align=center>
  <img src="images\补码-移码.png" title="补码-移码" height="50%" width="50%">
</div>



### 习题

- Example1

<div align=center>
  <img src="images\2_1.png" title="2_1" height="50%" width="50%">
</div>



> 在计算机中，有符号整数用补码表示。

| 真值  | 原码        | 补码        |
| :---- | ----------- | ----------- |
| $127$ | $0000007FH$ | $0000007FH$ |
| $-9$  | $8009H$     | $FFF7H$     |
| $118$ | $0000076H$  | $0000076H$  |

- Example2

<div align=center>
  <img src="images\2_2.png" title="2_2" height="50%" width="50%">
</div>



$|var1|=32767D=7FFFH$

$[var1]_{\text {补 }}=8001H$

$var2=8001H=32769D$

- Example3

| 补码（8位）                     | 拓展后的补码（16位）                    |
| ------------------------------- | --------------------------------------- |
| $[X_1]_{\text {补 }}=0.1010110$ | $[X_1]_{\text {补 }}=0.101011000000000$ |
| $[X_2]_{\text {补 }}=1.1100101$ | $[X_2]_{\text {补 }}=0.101011000000000$ |
| $[X_3]_{\text {补 }}=01010110$  | $[X_3]_{\text {补 }}=0000000001010110$  |
| $[X_4]_{\text {补 }}=111100101$ | $[X_4]_{\text {补 }}=11111111111100101$ |

- Example4

| 补码                            | 除2后的补码                                |
| ------------------------------- | ------------------------------------------ |
| $[X_1]_{\text {补 }}=0.1101010$ | $[\frac{1}{2}X_1]_{\text {补 }}=0.0110101$ |
| $[X_2]_{\text {补 }}=1.0100110$ | $[\frac{1}{2}X_2]_{\text {补 }}=1.1010011$ |
| $[X_3]_{\text {补 }}=1.0000000$ | $[\frac{1}{2}X_3]_{\text {补 }}=1.1000000$ |

- Example5

| 补码                            | 乘2后的补码                      | 状态   |
| ------------------------------- | -------------------------------- | ------ |
| $[X_1]_{\text {补 }}=0.0110100$ | $[2X_1]_{\text {补 }}=0.1101000$ | 未溢出 |
| $[X_2]_{\text {补 }}=1.0010110$ | $[2X_2]_{\text {补 }}=0.0101100$ | 溢出   |

- Example6

假设机器字长8位，$[X]_{\text {补 }}=11101100$

$[\frac{1}{2}X]_{\text {补 }}=11110110$

$[4X]_{\text {补 }}=10110000$ ，未溢出

- Example7

| 真值          | 原码                           | 补码                           | 移码                           |
| ------------- | ------------------------------ | ------------------------------ | ------------------------------ |
| $X_1=+101011$ | $[X_1]_{\text {原 }}=00101011$ | $[X_1]_{\text {补 }}=00101011$ | $[X_1]_{\text {移 }}=10101011$ |
| $X_2=-110010$ | $[X_2]_{\text {原 }}=10110010$ | $[X_2]_{\text {补 }}=11001110$ | $[X_2]_{\text {移 }}=00110001$ |

- Example8

涉及知识点

- 补码部分：
  - 补码与真值、原码之间的相互转换
  - 补码的算术右移（除2运算）
  - 补码的算术左移（乘2运算）
- 反码部分
  - 反码与原码及真值之间的转换
- 移码部分
  - 移码与补码之间的相互转换

| $[X]_{\text {补 }}=3AH=00111010$        | $[Y]_{\text {补 }}=C5H=11000101$        |
| --------------------------------------- | --------------------------------------- |
| $[2 X]_{\text {补 }}=01110100$          | $[2 Y]_{\text {补 }}=10001010$          |
| $[\frac{1}{2}X]_{\text {补 }}=00011101$ | $[\frac{1}{2}X]_{\text {补 }}=11100010$ |
| $[-X]_{\text {补 }}=11000110$           | $[-X]_{\text {补 }}=00111011$           |
| $[X]_{\text {原 }}=00111010$            | $[X]_{\text {原 }}=10111011$            |
| $[X]_{\text {反 }}=00111010$            | $[X]_{\text {反 }}=11000100$            |
| $[X]_{\text {移 }}=10111010$            | $[X]_{\text {移 }}=01000101$            |

------

<div align=center>
  <img src="images\真值-原-补-反-移.png." title="定点整数真值-原码-补码-反码-移码" height="50%" width="50%">
</div>


<div align=center>
  <img src="images\不同编码真值范围.png." title="6种不同编码对应的真值范围" height="50%" width="50%">
</div>



### 数据的浮点表示

浮点数的一般格式：


$$
F=M \times R^E
$$



- $M$：尾数（可正可负）
- $E$：阶码（可正可负）
- $R$：基数/基值

## 2.2 非数值数据编码

## 2.3 检错与纠错码