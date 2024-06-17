## 2024年本科毕设题目介绍

参考：[20231008-开源毕设题目和参与同学征集](https://www.yuque.com/xyong-9fuoz/hg8kgr/lg625y278c2f60sd#byKFi)

### xxxx

本题目的目标是，xxxx。

#### 总体目标

1. xxxx；

#### 1.1 xxxx（xxx）

xxxx。

##### 工作内容

  1. xxx。

##### 相关工作

1. []()

### 1. 面向FPGA的软硬件结合异步状态机接口设计与实现

#### 背景

SoC（System on chip）即片上系统是异构芯片设计的发展方向，其中，集成了FPGA与CPU的SoC可同时具备FPGA的大规模并发式处理能力以及CPU的通用计算能力。面临的主要问题在于在FPGA程序设计中很难高效的使用到CPU的计算能力造成资源浪费。CPU对于内存的访问更方便一些，更大量的数据可以采用缓存-处理的方式；而FPGA访问内存数据需要经过总线访问时序或DMA进行操作，极不方便。它一般使用多并行+流水的方式处理大量数据，对于一些需要大缓存的算法来说不太适应。

#### 目标

在集成了FPGA与CPU的SoC平台上，面向FPGA硬件程序设计能够高效使用CPU计算存储资源的异步状态机规范与接口。

### 2. 基于软硬件结合的透明增量式动态转义加速器设计与实现

#### 背景

FPGA（即硬件）在并行计算能力上远比CPU（即软件）强。FPGA已被用软硬件结合的方式用来对海量数据计算进行加速，即将FPGA作为硬件加速卡安装在传统冯诺依曼机器（以CPU、存储器为中心）中。用户可以将海量运算功能部署在FPGA中，在CPU中运行的控制程序可以与FPGA进行交互获取计算结果。但FPGA开发难度大，易用性差，阻碍了其在普通计算机中的应用。SoC

#### 目标

（两条技术路线二选一）

技术路线一：设计一种模块，能够在编译时对高级程序代码进行分析，将不同的计算放到FPGA与CPU中，形成FPGA可加载的bitstream与CPU可执行程序，并根据定义的接口规范自动形成信息交互接口。特征是强调增量式与透明，即可以根据当前设备配置的FPGA体积动态、增量配置转义到FPGA上运行的功能，最大化FPGA资源利用；且只要求开发者具备软件开发能力。

技术路线二：设计一种模块，能够针对正在执行或将要执行的软件进行指令级别的分析，将部分计算动态加载到FPGA中。其他特征与技术路线一一致。

#### 参考文献

1、Programming and Synthesis for Software-defined FPGA Acceleration: Status and Future Prospects： [https://www.sfu.ca/~zhenman/files/J6-TRETS2021-SDA-Survey.pdf](https://www.sfu.ca/~zhenman/files/J6-TRETS2021-SDA-Survey.pdf)

2、Userspace Bypass: Accelerating Syscall-intensive Applications： [https://www.usenix.org/system/files/osdi23-zhou-zhe.pdf](https://www.usenix.org/system/files/osdi23-zhou-zhe.pdf)

### 3. 跨操作系统的异步驱动模块设计与实现

#### 目标

利用 Rust 语言模块化、异步支持的特点，将异步机制与底层设备结合起来，实现更高效的异步驱动，并且能够在多个操作系统中应用。

#### 任务要求

1. 理解 Rust 语言异步编程及其原理；
2. 理解 Rust 语言模块化思想；
3. 理解一种设备的设计细节，思考其是否具有异步特性；
4. 在 linux 环境下或裸机环境下完成性能对比实验；

#### 参考文献

1. 2394-async_await - The Rust RFC Book. [https://rust-lang.github.io/rfcs/2394-async_await.html](https://rust-lang.github.io/rfcs/2394-async_await.html).
2. 3185-static-async-fn-in-trait - The Rust RFC Book. [https://rust-lang.github.io/rfcs/3185-static-async-fn-in-trait.html](https://rust-lang.github.io/rfcs/3185-static-async-fn-in-trait.html).
### 4. 在QEMU模拟器中的共享调度器设计与实现

共享调度器：将协程引入内核，以协程为任务单元，为其添加优先级作为调度依据。共享调度器基于协程对系统调用进行了异步化改造。

#### 目标

将软件定义的协程与硬件提供的机制进行配合，在中断/异常发生时，减少特权级以及上下文切换的开销，实现完全异步的中断/异常处理。设计出合理的接口并在 QEMU 模拟器中实现原型。

#### 任务要求

1. 理解 Rust 语言异步编程及其原理；
2. 理解 embassy 与共享调度器设计细节；
3. 理解硬件对中断/异常/系统调用的支持；
4. 设计出中断/异常的异步处理方案；
5. 熟悉 QEMU 模拟器，并对其进行改造，搭建系统原型，完成性能对比测试；

#### 参考文献

1. 2394-async_await - The Rust RFC Book. [https://rust-lang.github.io/rfcs/2394-async_await.html](https://rust-lang.github.io/rfcs/2394-async_await.html).
2. 3185-static-async-fn-in-trait - The Rust RFC Book. [https://rust-lang.github.io/rfcs/3185-static-async-fn-in-trait.html](https://rust-lang.github.io/rfcs/3185-static-async-fn-in-trait.html).
3. Embassy. Embassy. *Embassy* [https://embassy.dev/](https://embassy.dev/).
4. Specifications – RISC-V International. [https://riscv.org/technical/specifications/](https://riscv.org/technical/specifications/).
5. Documentation - QEMU. [https://wiki.qemu.org/Documentation#For_developers](https://wiki.qemu.org/Documentation#For_developers).
### 5. 在FPGA上的共享调度器设计与实现

共享调度器：将协程引入内核，以协程为任务单元，为其添加优先级作为调度依据。共享调度器基于协程对系统调用进行了异步化改造。

#### 目标

将软件定义的协程与硬件提供的机制进行配合，在中断/异常发生时，减少特权级以及上下文切换的开销，实现完全异步的中断/异常处理。设计出合理的接口并在 FPGA 上实现相应的硬件逻辑。

#### 任务要求

1. 理解 Rust 语言异步编程及其原理；
2. 理解 embassy 与共享调度器设计细节；
3. 理解硬件对中断/异常/系统调用的支持；
4. 设计出中断/异常的异步处理方案；
5. 熟悉 FPGA 开发流程；
6. 熟悉 rocketchip 并能对其进行改造，搭建系统原型，完成性能对比测试；

#### 参考文献

1. 2394-async_await - The Rust RFC Book. [https://rust-lang.github.io/rfcs/2394-async_await.html](https://rust-lang.github.io/rfcs/2394-async_await.html).
2. 3185-static-async-fn-in-trait - The Rust RFC Book. [https://rust-lang.github.io/rfcs/3185-static-async-fn-in-trait.html](https://rust-lang.github.io/rfcs/3185-static-async-fn-in-trait.html).
3. Embassy. Embassy. *Embassy* [https://embassy.dev/](https://embassy.dev/).
4. Specifications – RISC-V International. [https://riscv.org/technical/specifications/](https://riscv.org/technical/specifications/).
5. Asanovic, K. *et al.* The Rocket Chip Generator.
### 6. 微内核操作系统ReL4中基于用户态中断的异步系统调用设计

ReL4是用Rust重写的支持seL4在RISCV上的系统调用的微内核，用户态中断允许应用不经过内核直接向其他应用发送信号。当前的ReL4微内核以同步IPC进行系统调用。

#### 目标

利用RISCV平台已有的用户态中断机制，对ReL4微内核中的同步系统调用进行异步化改造，减少内核陷入和上下文切换次数，从而降低IPC开销，提升系统性能。

#### 任务要求

1. 理解微内核的相关概念，了解微内核的发展趋势和性能瓶颈。
2. 理解seL4的IPC机制，理解其中的优势和弊端。
3. 学习理解用户态中断的相关知识。
4. 学习使用Rust异步编程的相关技能。

#### 参考文献

[1] Klein G, Elphinstone K, Heiser G, et al. seL4: Formal verification of an OS kernel[C]//Proceedings of the ACM SIGOPS 22nd symposium on Operating systems principles. 2009: 207-220.

[2] Heiser G, Elphinstone K. L4 microkernels: The lessons from 20 years of research and deployment[J]. ACM Transactions on Computer Systems (TOCS), 2016, 34(1): 1-29.

[3] Klimiankou Y. Micro-CLK: returning to the asynchronicity with communication-less microkernel[C]//Proceedings of the 12th ACM SIGOPS Asia-Pacific Workshop on Systems. 2021: 106-114.

[4] Heiser G. The seL4 Microkernel–An Introduction[J]. The seL4 Foundation, 2020, 1.

### 7. 基于ReL4的用户态驱动模块设计

ReL4是用Rust重写的支持seL4在RISCV上的系统调用的微内核，用户态中断允许应用不陷入内核直接接收信号。当前ReL4的系统中断通过notification机制代理给用户态。

#### 目标

利用用户态中断改造ReL4的notification机制，使得接收线程无需主动陷入内核来阻塞等待中断到来，提升驱动线程的并发度。利用Rust语言的协程支持，设计并开发基于用户态中断的抢占式用户态驱动模块。

#### 任务要求

1. 理解微内核的相关概念，了解微内核的发展趋势和性能瓶颈。
2. 理解seL4的notification机制，理解其中的优势和弊端。
3. 学习理解用户态中断的相关知识。
4. 学习使用Rust异步编程的相关技能。
5. 设计用户态驱动模块，并能够部署在ReL4和seL4上，进行性能测试。

#### 参考文献

[1] Klein G, Elphinstone K, Heiser G, et al. seL4: Formal verification of an OS kernel[C]//Proceedings of the ACM SIGOPS 22nd symposium on Operating systems principles. 2009: 207-220.

[2] Heiser G, Elphinstone K. L4 microkernels: The lessons from 20 years of research and deployment[J]. ACM Transactions on Computer Systems (TOCS), 2016, 34(1): 1-29.

[3] Elphinstone K, Zarrabi A, Mcleod K, et al. A performance evaluation of rump kernels as a multi-server os building block on sel4[C]//Proceedings of the 8th Asia-Pacific Workshop on Systems. 2017: 1-8.

[4] Heiser G. The seL4 Microkernel–An Introduction[J]. The seL4 Foundation, 2020, 1.

### 8. 基于硬件支持的单地址空间模块隔离方法

由于内核代码的复杂性和快速的开发速度，加上使用不安全的低级编程语言，导致内核中经常出现错误和漏洞。尽管已经有许多静态和动态机制来保护内核代码的执行，但攻击者仍然能够找到绕过这些保护措施的新方法。现代内核需要一种实际的手段来限制单个漏洞的影响，即内核子系统的隔离。

#### 目标

基于硬件(如Intel MPK)技术支持，实现内核子系统之间的隔离。通过硬件和软件工程的配合，降低隔离的开销同时减少开发者的开发负担。

#### 任务要求

1. 理解为什么需要对操作系统进行隔离
2. 熟悉常见的硬件隔离手段
3. 具备对内核子系统的分析和拆解能力
4. 具备较强的编程实现能力
5. 设计基于硬件支持的隔离手段并应用到内核子系统上

#### 参考文献

1. [A Study of Security Isolation Techniques](https://dl.acm.org/doi/abs/10.1145/2988545)
2. [FlexOS: towards flexible OS isolation](https://FlexOS: towards flexible OS isolation)
3. [Intra-unikernel isolation with Intel memory protection keys](https://dl.acm.org/doi/abs/10.1145/3381052.3381326)

### 9. 基于Rust语言支持的单地址空间模块隔离方法

由于内核代码的复杂性和快速的开发速度，加上使用不安全的低级编程语言，导致内核中经常出现错误和漏洞。尽管已经有许多静态和动态机制来保护内核代码的执行，但攻击者仍然能够找到绕过这些保护措施的新方法。现代内核需要一种实际的手段来限制单个漏洞的影响，即内核子系统的隔离。

#### 目标

大多数隔离技术限定在特定的硬件平台之上，不仅性能受限，扩展性也很差，无法广泛部署。通过语言机制实现与硬件支持相同的子系统隔离效果，在保证性能的同时达到更好的扩展性和适用性。

#### 任务要求

1. 理解为什么需要对操作系统进行隔离
2. 熟悉常见的硬件隔离手段
3. 具备对内核子系统的分析和拆解能力
4. 具备较强的编程实现能力
5. 设计并实现基于语言机制的隔离措施并应用到内核子系统上

#### 参考文献

1. [Singularity: rethinking the software stack](https://dl.acm.org/doi/abs/10.1145/1243418.1243424)
2. [RedLeaf: Isolation and Communication in a Safe Operating System](https://www.usenix.org/conference/osdi20/presentation/narayanan-vikram)

### 10. 单地址空间隔离模块间异步通信方法研究

