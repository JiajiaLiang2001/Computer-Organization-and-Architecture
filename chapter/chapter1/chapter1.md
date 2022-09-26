- [第 1 章 序论](#第-1-章-序论)
  - [1.1 计算机发展简史](#11-计算机发展简史)
  - [1.2 摩尔定律](#12-摩尔定律)
  - [1.3 超算TOP500](#13-超算top500)
  - [1.4 计算机分层结构](#14-计算机分层结构)
    - [计算机系统层次结构](#计算机系统层次结构)
    - [计算机体系结构](#计算机体系结构)
    - [计算机组成](#计算机组成)
    - [计算机实现](#计算机实现)
  - [1.5 计算机基本组成](#15-计算机基本组成)
    - [硬件系统](#硬件系统)
    - [软件系统](#软件系统)
  - [1.6 计算机分类及其性能描述](#16-计算机分类及其性能描述)
  - [1.7 计算机性能描述](#17-计算机性能描述)
    - [计算机系统性能计算（定性）](#计算机系统性能计算定性)
    - [计算机系统性能计算（定量）](#计算机系统性能计算定量)
    - [用测试程序来测评计算机系统性能](#用测试程序来测评计算机系统性能)
  - [1.8 Amdahl定律](#18-amdahl定律)

# 第 1 章 序论

## 1.1 计算机发展简史

http://egov.uok.edu.in/elearningug/tutorials/7934_1_2016_161115135359.pdf

## 1.2 摩尔定律

**摩尔定律**：集成电路芯片的集成度每18个月翻一番。

## 1.3 超算TOP500

https://top500.org

## 1.4 计算机分层结构

### 计算机系统层次结构

<div align=center>
  <img src="images\计算机系统的层次结构.png" title="计算机系统的层次结构" height="25%" width="25%">
</div>


第 $1$ 级 计算机指令的设置和每条指令工作的细节。

第 $2$ 级 针对具体硬件物理计算机。

第 $3$ 级 对整个系统的硬件、软件系统进行有效管理。

第 $4$ 级 针对特定处理器，不同处理器的指令系统不一样（系统处理器的指令系统可兼容）。

第 $5$ 级 跨平台。

第 $6$ 级 更适合应用的，更接近自然语言的。

<div align=center>
  <img src="images\计算机分层结构形式1.png" title="计算机分层结构形式1" height="50%" width="50%">
</div>


<div align=center>
  <img src="images\计算机分层结构形式2.png" title="计算机分层结构形式2" height="50%" width="50%">
</div>

> 我们这里主要研究与描述硬件物理计算机，工作层次位于 1~3 级。

### 计算机体系结构

**计算机体系结构（Computer Architecture）**：计算机系统的属性—概念性结构及功能特性。

计算机系统结构所指的计算机的属性主要包括：

- 数据的表示形式；
- 寻址方式；
- 内部寄存器组；
- 指令集；
- 中断系统；
- 处理器工作状态及其切换；
- 存储系统；
- 输入/输出结构；
- 信息保护及特权；
- 高性能设计
- ...

### 计算机组成

**计算机组成（Computer Organization）**：计算机系统的逻辑实现。

> 包括最低层内部算法、数据流、控制流的逻辑实现。

计算机组成所指的计算机的设计主要包括：

- 数据通路的宽度；
- 专用部件的设置（如乘除法专用部件、浮点运算专用部件等）
- 各功能部件的并行程度；
- 各种操作的相容性与互斥性；
- 控制机构的组成方式；
- 缓冲与排队技术的应用；
- 预估、预判方法；
- 高可靠性技术
- ...

### 计算机实现

**计算机实现（Computer Implementation）**：计算机系统的物理实现。

计算机实现所指的计算机的部件主要包括：

- 电路芯片
- 电子元器件
- 部件
- 插头
- 插座
- ...

| 对应层次       | 具体概念                                 |
| -------------- | ---------------------------------------- |
| 计算机系统结构 | 计算机的总体属性                         |
| 计算机组成     | 计算机的总体属性的逻辑设计               |
| 计算机实现     | 计算机的总体属性的逻辑设计的物理器件实现 |

## 1.5 计算机基本组成

### 硬件系统

**计算机硬件**：计算机中看得见摸得着的实体。

​		计算机结构是 1946 由冯·偌依曼提出，提出计算机是依据*存储程序*、*执行程序并实现控制*的方式工作的。

<div align=center>
  <img src="images\早期计算机（硬件）的组成.png" title="早期计算机（硬件）的组成" height="50%" width="50%">
</div>


- $\color{orange}{运算器}$：实现算术运算和逻辑运算。
- $\color{orange}{控制器}$：根据指令的功能产生相应的控制信号，控制其他部分的工作。
- $\color{orange}{存储器}$：存储数据和程序。
- $\color{orange}{输入设备}$：将外部信息输入到计算机。
- $\color{orange}{输出设备}$：接收计算机处理的结果并处理。

------

$\color{red}{基本思想}$：冯·诺依曼计算机工作的基本思想，就是将计算机要处理的问题用指令编成程序，并将程序和数据一起存放在存储器中，在控制器的控制下，从存储器中逐条取出指令并执行，通过执行程序最终解决计算机所要处理的问题。

$\color{red}{特点}$：

1. 总是一条指令接一条指令地执行，执行指令会产生控制流，在控制流的驱动下完成指令的功能。在此过程中，数据流则是被动地调用。
2. 指令、数据及其他信息均是用二进制编码来表示的。

$\color{green}{早期的\;PC\;机}$

<div align=center>
  <img src="images\微型计算机结构框图.png" title="微型计算机结构框图" height="50%" width="50%">
</div>

$\color{green}{目前的\;PC\;机的主板结构}$

<div align=center>
  <img src="images\PC机主板结构.png" title="PC机主板结构" height="50%" width="50%">
</div>



### 软件系统

**计算机软件**：通常是指计算机所配置的各类程序和文件，存放在内存或外存中的二进制编码信息，不能直接触摸而修改相对比较容易。

- **系统软件**：一系列保障计算机很好运行的程序集合。它们的功能是对系统的各种资源(硬件和软件)进行管理和调度，使计算机能有条不紊地工作，为用户提供有效的服务，充分发挥其效能。
  - 操作系统
  - 语言处理程序
  - 通用程序
  - 各种服务支持软件
- **应用软件**：应用软件是指用户在各自的应用中，为解决自己的任务而编写的程序。这是一类直接以用户的需求为目标的程序。由于用户的多样性（各行各业、各种部门）和用户需求的多样性，使得这类软件也具有多样性。
  - 科学计算
  - 信息管理
  - 过程控制
  - 武器装备
  - ...

## 1.6 计算机分类及其性能描述

$\color{green}{早期的计算机分类}$

​		在20世纪80年代前，人们根据计算机的字长、规模、价格等指标，将计算机分为微型机、小型机、中型机、大型机和巨型机。

$\color{green}{目前依据用途分类}$

- $\color{orange}{通用计算机}$
  - $\color{orange}{个人计算机（PC）}$
  - $\color{orange}{服务器}$
    - WEB 服务器
    - FTP 服务器
    - MAIL 服务器
    - 文件共享服务器
    - 数据库应用服务器
    - 网站的网关服务器
    - DNS 服务器
    - 流媒体服务器
- $\color{orange}{嵌入式计算机（专用计算机）}$

**$\color{green}{佛林（Flynn）分类法}$**：按照计算机在执行程序的过程中信息流的特征进行分类的。

在程序执行过程中存在三种信息流：

**指令流（IS）**—— $\begin{equation}
M M->C U
\end{equation}$  。

**数据流（DS）**—— 包括输人数据、中间数据和结果，$\begin{equation}
M M<->P U
\end{equation}$。

**控制流（CS**）—— $\begin{equation}
C U->P U
\end{equation}$。

**单指令流单数据流 SISD（Single Instruction Single Datastream）**：单一控制单元，单一处理单元和单一主存储器。举例：传统的串行计算机。

*SISD*：

<div align=center>
  <img src="images\SISD.png" title="单指令流单数据流" height="50%" width="50%">
</div>


**单指令流多数据流 SIMD（Single Instruction Multiple Datastream）**：单个控制单元，多个处理单元和多个存储器模块。举例：阵列处理器，向量处理机。

*SIMD*：

<div align=center>
  <img src="images\SIMD.png" title="单指令流多数据流" height="50%" width="50%">
</div>


**多指令流单数据流 MISD（Multiple Instruction Single Datastream）**：多个控制单元同时执行多条指令对同一数据进行处理。无实际。

*MISD*：

<div align=center>
  <img src="images\MISD.png" title="多指令流单数据流" height="50%" width="50%">
</div>


**多指令流多数据流 MIMD（Multiple Instruction Multiple Datastream）**：多个控制单元同时执行多条指令处理多条数据。举例：多处理机，机群（集群）系统。

*MIMD*：

<div align=center>
  <img src="images\MIMD.png" title="多指令流多数据流" height="50%" width="50%">
</div>

## 1.7 计算机性能描述

### 计算机系统性能计算（定性）

- **CPU 字长**：CPU 一次能处理数据的位数。

> 字长 $\uparrow$ $\longrightarrow$ CPU 能处理的数据精度 $\uparrow$

- **主频**：时钟脉冲的频率。

> 主频 $\uparrow$ $\longrightarrow$ CPU 工作节拍 $\uparrow$

- **主存容量**：$\mathbf{C}_{\mathrm{MAX}}=\mathbf{2}^{\mathbf{n}}$，$n$ ：CPU 地址总线根数。
- **带宽均衡性**
- **软硬件配置**
- **性能价格比**
- **RASIS 特性**
- **兼容性**
- **友好性**：人体工程学。
- **环保性**：对人和对环境的污染。

### 计算机系统性能计算（定量）

- **MIPS**：每秒钟执行指令的百万条数 。[Top500](https://top500.org/)
- **MFLOPS**：每秒钟执行浮点数的百万次操作的数量。
- **吞吐量（Throughput）**：给定时间内（并行）完成的总任务数。
- **响应时间/执行时间（Execution Time**）：一个任务从开始到完成的时间。
- **CPU 时间**：一个任务从开始到完成的 CPU 所用时间。
- **处理器数量**

> 一般计算机，执行时间 $\downarrow$$\longrightarrow$ 吞吐量 $\uparrow$ ；CPU 时间 $\downarrow$ $\longrightarrow$ 执行时间 $\downarrow $
>
> 多处理系统计算机，吞吐量 $\uparrow$

$\color{red}{因此使用更快的 CPU，可以改善执行时间和吞吐量}$ 。

**计算机系统性能**：

$\color{green}{用执行时间衡量（反比）}$
$$
\text { 性能 } P=\frac{1}{\text { 执行时间 } T}
$$
$\color{green}{用吞吐率衡量 （正比）}$
$$
\text { 性能 } P==\text { 吞吐率 }=\frac{\text { 完成的总任务数  } X}{\text { 给定时间 } t}
$$
**相对性能（Relative Performance）/性能比（Performance Ratio）**：计算机 $X$ 比计算机 $Y$ 快 $n$ 倍，或在 $Y$ 上的执行时间比 $X$ 的长 $n$ 倍。
$$
n=\frac{P_{\mathrm{X}}}{P_{\mathrm{Y}}}=\frac{T_{\mathrm{Y}}}{T_{\mathrm{X}}}
$$

### 用测试程序来测评计算机系统性能

$\color{green}{基准测试程序}$

以往：

- $\color{orange}{实际应用程序}$ 
- $\color{orange}{修正的实际应用程序}$ 
- $\color{orange}{核心程序}$ 
- $\color{orange}{小测试程序}$ 
- **$\color{orange}{合成测试程序（测试程序组件/合成测试程序/基准测试程序）}$**

> 利用基准测试程序的优点是可以避免单个测试程序的片面性，更加全面地测试计算机的性能。
>
> 因此，目前利用合成测试程序进行计算机性能评估已被广泛采用。

目前常见的基准测试程序：

- $\color{orange}{TPC-C}$ ：对系统在线处理事务的能力进行评价。
- $\color{orange}{TPC-H}$ ：对系统在线数据库资料的查询能力进行评价。
- $\color{orange}{SPEC\;web\;2005}$ ：评价系统同时响应 http 连接的最大数量。
- $\color{orange}{SPEC\;jApp\;Server2004}$ ：评价系统基于 Java 平台每秒钟所完成的java操作的最大数量。
- $\color{orange}{SPEC\;CPU2000}$：用于对特定程序包执行时的评估。
- $\color{orange}{Linpack}$ ：在每秒钟内，利用高斯消元法求解一元 N 次线性方程组的次数来评价系统的性能。
- $\color{orange}{HPCC}$ ：利用双精度矩阵乘法、傅立叶变换、并行矩阵转置等七个子项全面评价系统的性能。
- $\color{orange}{SAP\;SD}$：测试系统的响应时间及每小时完成的定单数，用以衡量系统同时执行应用程序及数据库的能力。

$\color{green}{PC\;性能测试}$

1. CPU 性能测试

   1. PC Mark2002：整机综合性能测试软件，其中包含对CPU、内存、硬盘等子系统的性能测试。
   2. Super pi（104万位）：将圆周率计算到104万位。

2. 基准测试软件测试

   1. 办公应用

      - Business Winstone2001：模拟Office2000、Lotus Notes R5、Netscape Navigator4.7、Norton AntiVirus2000和WinZip 7.0实际工作环境的测试软件，测试系统对办公应用软件的处理速度。 

   2. 网络/多媒体创作

      - CC Winstone2002：模拟Adobe PhotoShop 5.5/Premiere 5.1、Dreamweaver 3.0、Director 8.0和Sound Forge4.5实际工作的测试软件，用于测试系统对图形处理、多媒体音频、视频编辑软件的处理速度。

   3. 3D游戏处理性能

      - 3D Mark2001 SE：常用的3D游戏性能测试软件。

      - Quake3 Ver1.17：OpenGL游戏性能基准测试软件。

      - Serious Sam-second Encounter：一个CPU 3D游戏性能测试工具。

   4. 3D图形性能

      - Cinema 4D XL V6.103：专业的Open GL引擎3D绘图软件，用于测试CPU在专业OpenGL 3D绘图软件中的性能。

3. 实际应用软件测试

   - MPEG4编码：FlasK MPEG0.594+DivX5.0.2

   - MP3编码：Lame3.89 alpha

   - 文件压缩：Winzip 8.1

## 1.8 Amdahl定律

**Amdahl 定律**：计算机系统中某一部件由于采用某种更快的执行方式后，整个系统性能的提高与这种执行方式的使用频率或占总执行时间的比例有关。

**加速比**：
$$
\text { 加速比 }=\frac{\text { 改进后的系统性能 }}{\text { 改进前的系统性能 }}=\frac{\text { 改进前的系统总执行时间 }}{\text { 改进后的系统总执行时间 }}
$$
取决于两个因素：

- **可改进比例 $f_{\mathrm{e}}$**：可改进部分在原系统总执行时间中所占的比例。
- **部件加速比 $r_{\mathrm{e}}$**：可改进部分改进后性能提高的程度。

$\color{green}{对串行处理器讨论}$

假设存在单个部件改进，改进前系统总执行时间为  $T_0$，改进后系统总执行时间 $T_n$，则
$$
T_{\mathrm{n}}=T_0\left(1-f_{\mathrm{e}}+\frac{f_{\mathrm{e}}}{r_{\mathrm{e}}}\right)
$$
单个部件可改进的加速比：
$$
S_{\mathrm{p}}=\frac{1}{\left(1-f_{\mathrm{e}}\right)+\frac{f_{\mathrm{e}}}{r_{\mathrm{e}}}}
$$

> 当系统可改进的部分 $f_{\mathrm{e}}$ 确定后，既使该部分改进后不再需要时间，即 $r_e \rightarrow \infty$，则 $S_{\mathrm{p}}=1 /\left(1-f_{\mathrm{e}}\right)$。
>
> $\color{red}{系统性能的改善受可改进部分 f_{\mathrm{e}} 的限制}$

同理可得多个部件可改进的加速比：
$$
S_{\mathrm{p}}=\frac{1}{\left(1-\sum f_{\mathrm{e}}\right)+\left(\frac{\sum f_{\mathrm{c}}}{r_{\mathrm{e}}}\right)}
$$
$\color{green}{对并行处理器讨论}$

利用多处理器并行、多线程并行技术带来的收益：
$$
S_{\mathrm{p}}=\frac{1}{\left(1-f_{\mathrm{e}}\right)+\frac{f_{\mathrm{e}}}{n}}
$$

- $f_{\mathrm{e}}$：并行部分所占比例。
- $\left(1-f_e\right)$：串行部分所占比例。
- $n$：并行处理结点个数。

$\left(1-f_e\right)=0$，$\operatorname{Max} S_p=n$

$\left(1-f_e\right)=1$，$\operatorname{Min} S_p=1$

$n \rightarrow \infty$，$\lim S_p \rightarrow 1 /\left(1-f_e\right)$，$\color{red}{加速比上限}$

