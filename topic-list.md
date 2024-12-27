## 2025年本科毕设题目介绍

开源毕设的宗旨是，与志同道合者合作，做有兴趣的毕设题目，在开源社区分享毕设成果。

基于上一年的开源毕设的组织情况，每年秋季学期会在这里陆续更新一部分题目，供有兴趣的同学在自己的毕设选题时参考。

### xxxx

本题目的目标是，xxxx。

#### 背景

1. xxxx；

#### 目标

xxxx。

##### 参考文献

1. []()

### 1. CPU与FPGA间的软硬件接口设计与实现

#### 背景

SoC（System on chip）即片上系统是异构芯片设计的发展方向，其中，集成了FPGA与CPU的SoC可同时具备FPGA的大规模并发式处理能力以及CPU的通用计算能力。面临的主要问题在于在FPGA程序设计中很难高效的使用到CPU的计算能力造成资源浪费。CPU对于内存的访问更方便一些，更大量的数据可以采用缓存-处理的方式；而FPGA访问内存数据需要经过总线访问时序或DMA进行操作，极不方便。它一般使用多并行+流水的方式处理大量数据，对于一些需要大缓存的算法来说不太适应。

FPGA（即硬件）在并行计算能力上远比CPU（即软件）强。FPGA已被用软硬件结合的方式用来对海量数据计算进行加速，即将FPGA作为硬件加速卡安装在传统冯诺依曼机器（以CPU、存储器为中心）中。用户可以将海量运算功能部署在FPGA中，在CPU中运行的控制程序可以与FPGA进行交互获取计算结果。但FPGA开发难度大，易用性差，阻碍了其在普通计算机中的应用。

#### 目标

1. 在集成了FPGA与CPU的SoC平台上，面向FPGA硬件程序设计能够高效使用CPU计算存储资源的异步状态机规范与接口。
2. 设计一种模块，能够在编译时对高级程序代码进行分析，将不同的计算放到FPGA与CPU中，形成FPGA可加载的bitstream与CPU可执行程序，并根据定义的接口规范自动形成信息交互接口。特征是强调增量式与透明，即可以根据当前设备配置的FPGA体积动态、增量配置转义到FPGA上运行的功能，最大化FPGA资源利用；且只要求开发者具备软件开发能力。
3. 设计一种模块，能够针对正在执行或将要执行的软件进行指令级别的分析，将部分计算动态加载到FPGA中。其他特征与技术路线一一致。

#### 参考文献

1. [面向硬件的异构OS设计](https://github.com/wujingbang/heterOS)
2. 龚思衡的毕设
3. 蒋嘉铭的毕设
4. Programming and Synthesis for Software-defined FPGA Acceleration: Status and Future Prospects： [https://www.sfu.ca/~zhenman/files/J6-TRETS2021-SDA-Survey.pdf](https://www.sfu.ca/~zhenman/files/J6-TRETS2021-SDA-Survey.pdf)
5. Userspace Bypass: Accelerating Syscall-intensive Applications： [https://www.usenix.org/system/files/osdi23-zhou-zhe.pdf](https://www.usenix.org/system/files/osdi23-zhou-zhe.pdf)

### 2. Rust组件化操作系统设计、实现和改进

#### 背景

为实现开源操作系统社区项目间的操作系统内核模块的代码级复用和协作开发，计划基于Rust语言建立一个可复用Rust内核组件库，并定制多种架构的操作系统内核。参与本项目的同学可从以下几个角度参与这个操作系统内核模块库的建设。

#### 目标

- 利用内核组件库中的已有模块，定制具有独立特征的操作系统内核；
- 改进和完善内核组件库中的已有组件：可能的改进方向是执行性能、适用场景、安全性、支持新特征等；
- 基于你的操作系统开发需求，为内核模块库增加新组件；
- 操作系统内核组件库的自动测试工具开发和完善；
- 操作系统内核组件的静态分析工具和和集成平台开发和完善；

#### 参考文献

- [组件化操作系统](https://opencamp.cn/os2edu/camp/2024fall/stage/3?tab=video)：关于组件化操作系统的教学视频；

  - [组件化内核的构建方法与示例](https://www.yuque.com/xyong-9fuoz/hg8kgr/yrqlvc26nf8qfrcl)：石磊的关于组件化操作系统的技术报告；

#### 内核组件库

- [内核模块组织kern-crates](https://github.com/kern-crates)

- [已有模块列表](https://kern-crates.github.io/.github/)

- [内核模块自动测试工具](https://github.com/kern-crates/testing/wiki/组件化多仓CI开发日志)

- [内核模块静态分析工具](https://github.com/os-checker/os-checker/)

  - [Rust crate静态分析平台使用帮助文档](https://os-checker.github.io/book/)
  - [kern-crates内核组件的静态分析结果](https://kern-crates.github.io)

#### 已有的组件化OS列表

- 王润基：[zCore](https://github.com/kern-crates/zCore)

  - [zCore模块化的crates仓库列表](https://github.com/kern-crates/zCore?tab=readme-ov-file#list-of-zcores-modular-crates)

- 贾越凯：[ArceOS](https://github.com/arceos-org/arceos)

  - [List of crates in ArceOS](https://arceos.org/arceos/)

- 郑友捷：[Starry-OS](https://github.com/Starry-OS/Starry/)

- 杨金博：[ByteOS](https://github.com/Byte-OS/byteos)

- 陈林峰：[Alien](https://github.com/Godones/Alien/)

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

### 6. 微内核操作系统设计、实现和改进

#### 背景

用户态中断允许应用不经过内核直接向其他应用发送信号。目前x86和RISC-V平台上都有用户态中断的支持，其中x86系列中有CPU芯片支持用户态中断，RISC-V上的用户态支持是在QEMU模拟器和FPGA上实现的，RISC-V上还有中断控制器与调度器结合的硬件实现TAIC；微内核操作系统seL4的Rust重写实现；reL4中也对RISC-V和ARM平台有了初步的支持，reL4在RISC-V上还提供异步通知机制、异步IPC和异步系统调用。这些已有工作为基于软硬协同的微内核操作系统IPC性能优化提供了必要的基础。本项目将继续沿着利用用户态中断等硬件支持来提升微内核操作系统的IPC性能。

#### 目标

本项目将继续沿着利用用户态中断等硬件支持来提升微内核操作系统的IPC性能的方向，在RISC-V、x86和ARM平台上，围绕QEMU和FPGA上的硬件改进、reL4的软件异步机制适配和改进、reL4上的传统操作系统功能实现等研究点开展研究工作。

#### 已有参考

* 项晨东-[基于用户态中断技术实践报告](https://www.xuetangx.com/learn/THU0809100czxt/THU0809100czxt/14294493/video/25500375)：这个工作在QEMU模拟器中实现了x86用户态中断机制，支持在Linux中使用用户态中断机制给指定进程发送用户中断。

   * [问题以及探究过程](https://github.com/OS-F-4/usr-intr/blob/main/ppt/qemu工作文档分块/问题以及探究过程.md)

* 田凯夫：[RISC-V 用户态中断扩展设计与实现](https://www.xuetangx.com/learn/THU0809100czxt/THU0809100czxt/14294493/video/35643597)（技术报告）：这个工作在QEMU模拟器和FPGA上实现了RISC-V的用户态中断机制，并利用用户态中断优化了seL4微内核的IPC性能。

   * [代码和文档](https://www.yuque.com/xyong-9fuoz/hg8kgr/nlr21043ghhmmuf9#gXRW2)

* 廖东海、朱懿、李龙昊：reL4微内核操作系统的设计与实现：这个工作目前已在RISC-V上已通过基准测试，有基于用户态中断的异步通知、异步IPC和异步系统调用支持；在ARM平台上通过基准测试；

   * [ReL4：基于用户态中断的高性能异步微内核设计与实现](https://www.yuque.com/xyong-9fuoz/hg8kgr/xd49izet7xd38gdy#aVrhG)（报告）

   * [reL4 book](https://rel4team.github.io/zh/)（文档）

   * [reL4 org](https://github.com/rel4team2)（代码仓库）

#### 6.1 reL4在x86上的移植和IPC性能优化

##### 任务要求

1. 重现已有相关工作；

2. 将reL4移植到x86平台上，并通过微内核的基准测试；

3. 在QEMU模块器环境下，利用x86的用户态中断支持reL4的通知机制、异步IPC和异步系统调用；

4. 在x86真实机器上，利用x86的用户态中断支持reL4的通知机制、异步IPC和异步系统调用；

5. 性能测试对比分析；

#### 6.2 reL4在RISC-V上重构和IPC性能优化

##### 任务要求

1. 重现已有相关工作；
2. 基于TAIC重构reL4的异步通知机制、异步IPC和异步系统调用；
3. 基于TAIC重构reL4的调度机制；
4. 性能测试对比分析；

#### 6.3 微内核操作系统ReL4中基于用户态中断的异步系统调用设计

##### 任务要求

利用RISCV平台已有的用户态中断机制，对ReL4微内核中的同步系统调用进行异步化改造，减少内核陷入和上下文切换次数，从而降低IPC开销，提升系统性能。

1. 理解微内核的相关概念，了解微内核的发展趋势和性能瓶颈。

2. 理解seL4的IPC机制，理解其中的优势和弊端。

3. 学习理解用户态中断的相关知识。

4. 学习使用Rust异步编程的相关技能。

##### 参考文献

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

