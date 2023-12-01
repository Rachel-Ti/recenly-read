- [schedule](#schedule)
  - [SC](#sc)
    - [2022](#2022)
      - [1.IceBreaker: Warming Serverless Functions Better with Heterogeneity](#1icebreaker-warming-serverless-functions-better-with-heterogeneity)
      - [1.SFS: Smart OS Scheduling for Serverless Functions]
      (#1SFS: Smart OS Scheduling for Serverless Functions)
    - [2021](#2021)
      - [1.Understanding, Predicting and Scheduling Serverless Workloads under Partial Interference]
        (#1understanding, predicting and Scheduling Serverless Workloads under Partial Interference)
  - [IWQoS](#IWQoS)
    - [2022](#2022)
      - [1.On the Joint Optimization of Function Assignment and Communication Scheduling toward Performance Efficient Serverless Edge Computing]
      (#1On the Joint Optimization of Function Assignment and Communication Scheduling toward Performance Efficient Serverless Edge Computing)
  - [CCGridW](#CCGridW)
    - [2022](#2022)
      - [1.Optimizing Memory Allocation in a Serverless Architecture through Function Scheduling]
        (#1Optimizing Memory Allocation in a Serverless Architecture through Function Scheduling)
- [edge](#edge)
  - [ICWS](#icws)
    - [2022](#2022)
      - [1.A Declarative Approach to Topology-Aware Serverless Function-Execution Scheduling]
        (#1A Declarative Approach to Topology-Aware Serverless Function-Execution Scheduling)
  - [SMARTCOMP](#SMARTCOMP)
    - [2022](#2022)
      - [1.A Prototype for QKD-secure Serverless Computing with ETSI MEC]
        (#1A Prototype for QKD-secure Serverless Computing with ETSI MEC)
      - [2.Stateless or stateful FaaS? I’ll take both!]
        (#2Stateless or stateful FaaS? I’ll take both!)
  

# schedule  

## SC  
> SC (International Conference for High Performance Computing, Networking, Storage, and Analysis)是高性能计算，体系结构领域顶级会议，CCF推荐A类会议，CORE Conference Ranking A类会议，H5指数44，Impact Score 4.95，录取率约20%。SC被誉为是可以看到未来的技术的会议，该会议被看作是用来解决世界级难题的地方！
### 2022

#### 1.SFS: Smart OS Scheduling for Serverless Functions

[pdf](https://cz5waila03cyo0tux1owpyofgoryroob.aminer.cn/6A/77/51/6A77513774241F0AD7F4A217828F22C4.pdf)

**摘要：**
无服务器计算通过让开发人员编写细粒度的无服务器或云函数，为构建和扩展云应用开辟了新的途径。云函数的执行时间通常很短，范围从几毫秒到几百秒。然而，由于公共云的深度整合导致的资源争用，函数执行时间可能会显著延长，无法准确计算函数的真实资源使用情况。我们观察到，对于开源FaaS平台（OpenLambda）而言，函数持续时间可以具有很高的不可预测性，放大量超过50倍。我们的实验表明，云函数主机服务器的操作系统调度策略对性能具有至关重要的影响。默认的Linux调度器**CFS（Completely Fair Scheduler）**对负载不敏感，经常在短函数上下文切换，导致周转时间比服务时间长得多。我们提出了SFS（Smart Function Scheduler）它完全在用户空间中工作，并精心编排现有的Linux FIFO和CFS调度器，以接近最短剩余时间优先(SRTF)。SFS使用**双层调度**，SFS使用两级调度，无缝地将新的FILTER策略与Linux CFS结合在一起，以换取长函数持续时间的增加，从而显著提高短函数的性能。我们在Linux用户空间中实现了SFS，并将其移植到OpenLambda。评估结果显示，与CFS相比，SFS显著缩短了短函数的执行时间，对较长的函数影响较小。

**核心内容**
在 FaaS 工作负载中，大多数云函数都是短暂且执行时间范围广泛的。默认的 Linux 调度程序 CFS 经常上下文切换短函数，导致等待时间不公，从而导致比它们本应得到的等待时间更长。因此，SFS 更改为先来先服务（SRTF）- 先发制人版本的最短作业优先（SJF），它总是调度完成后最快的作业。但是，将 SRTF 直接应用是不可能的，因此我们提出了 SFS，一种用户空间函数调度程序，用于优化短函数密集型 FaaS 工作负载的周转时间。SFS 完全在用户空间内运行，利用现有的内核调度策略（先进先出队列，先进先出优先级）来近似 SRTF。为此，SFS 采用双层调度：在最高级别上，SFS 使用一种新的 FILTER（先进先出队列，先进先出优先级）算法，按照函数被入队和预先抢占的顺序安排函数，如果它们在**动态变化的时间片内不能完成，则过滤掉**；在最低级别上，那些从最高级别过滤下来的函数在**Linux CFS**中继续。这样，短函数可以在不需要任何上下文切换的情况下执行，或者如果有必要，最少进行一次上下文切换，以更快完成。目标是通过最小化函数执行时间，最大化 RTE 度量，从而实现“按需付费”的承诺，并减少不公平的附加费用。

[code](https://github.com/ds2-lab/sfs)

### 2021

#### 1.Understanding, predicting and scheduling serverless workloads under partial interference

[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9910093)

**摘要：**
分布式云应用之间的干扰可以分为三类：完全干扰、部分干扰和零干扰。尽管以前的研究仅关注完全干扰，但部分干扰（发生在应用的部分区域）则更为常见，但却研究得不够深入。将应用结构化为小规模、短寿命函数的无服务器计算进一步加剧了部分干扰。我们分析了无服务器计算中部分干扰的特征，发现其具有高波动性、时空变化和传播特性。基于这些观察，我们提出了一种增量学习预测器，名为Gsight，通过利用端到端的调用路径 harnessing spatial-temporal overlap codes 和函数概况，实现高精度。实验结果表明，Gsight可以实现平均误差1.71%。其收敛速度至少是服务器丰富系统速度的3倍。一个调度案例研究显示，所提出的方法可以提高函数密度≥18.79%，同时保证服务质量（QoS）。

[code](https://github.com/tjulym/gray/tree/main)

## IWQoS

>International Symposium on Quality of Service,CCF分级：计算机网络B,录用率：2021年24.61%，CCF分级：计算机网络B，截稿时间：2023/2/5(注册)，录用通知时间：2023/3/29

### 2022

#### 1.On the Joint Optimization of Function Assignment and Communication Scheduling toward Performance Efficient Serverless Edge Computing

[pdf](https://arxiv.org/pdf/2203.06385.pdf)

**摘要：**
无服务器边缘计算作为部署复杂应用的有效载体，其中包含相互依赖的功能，其分配决策对应用性能影响很大。尽管类似问题已经得到了广泛研究，但现有方法都没有考虑通信风格的多样性，这在无服务器计算中是特别引入的，对性能效率也有很大影响。我们比较了两种通信风格，分别称为直接传递和远程存储，用于在函数之间传输中间数据。我们发现，没有一种通信风格可以在所有场景中占据主导地位，最优选择取决于多个因素，如扇出度、数据大小和网络带宽。因此，如何为每个函数间通信链选择适当的通信风格，以及函数分配决策，对应用性能至关重要。为此，我们提出了一种基于优先级的分配和选择（PASS）算法，综合考虑函数分配和通信风格选择。我们对PASS算法的近似比进行了理论分析，并在实际应用上进行了大量实验，结果显示，与最先进的方法相比，PASS平均可以将完成时间减少24.1%。


## CCGridW
>  International Symposium on Cluster, Cloud and Internet Computing Workshops(CCGridW)。但IEEE/ACM International Symposium on Cluster, Cloud and Internet Computing (CCGrid)(CCGrid)是计算机体系结构/并行与分布计算/存储系统CCF C类会议。

### 2022

#### 1.Optimizing Memory Allocation in a Serverless Architecture through Function Scheduling

[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10181224)

**摘要：**
在无服务器架构中，函数并未充分利用分配的内存。这种内存过度分配提高了节点利用率，但浪费了资源，导致了冷启动和延迟问题。本文提出了一种针对无服务器架构的细粒度调度方法，旨在解决内存过度分配问题并提高数据局部性。该方法估算每个函数使用的内存量，以便在同一节点上调度相似的函数。因此，它减少了每个节点的使用，并将在单个节点内保持状态。我们通过现有的FaaS应用和实际数据对我们的方法进行了评估。



# edge

## ICWS
> IEEE International Conference on Web Services服务计算领域旗舰性的顶级国际学术会议。IEEE ICWS/SCC/CLOUD/Big Data/MS/SERVICES国际学术会议，又称为IEEE服务大会（IEEE SERVICES Congress），是由IEEE服务计算技术委员会发起的世界上服务计算领域规模最大、水平最高的系列国际学术会议，后来扩展到 云计算 和大数据等领域。

### 2022

#### 1.A Declarative Approach to Topology-Aware Serverless Function-Execution Scheduling 

[pdf](https://ieeexplore.ieee.org/abstract/document/9885760)

**摘要：**

最新的无服务器平台使用硬编码调度策略，这些策略不知道函数可能存在的拓扑约束。在调度函数时考虑这些约束可以带来性能的显著提升，例如最小化加载时间或数据访问延迟。当考虑到新兴的多云和边缘云 continuum 系统时，这个问题变得更加紧迫，因为只有**特定的节点可以访问专用、本地资源**。为解决这个问题，我们提出了一种声明性语言来定义无服务器调度策略，以表达调度器和执行节点拓扑的约束。我们将我们的方法实现为 **OpenWhisk**平台的扩展，并展示相关场景，在这些场景中，我们的扩展与纯 OpenWhisk 相比具有竞争力或表现更优。

**核心内容**
在多云和边缘云连续系统中，分配函数时，并非所有worker都平等，只有特定的worker可以访问某些本地资源。实际上，像**像数据局部性**(由于访问数据的高延迟而产生的影响)，或者**会话局部性**(由于需要身份验证并打开新的会话以与其他服务交互而产生的影响)，可能会显著增加函数的运行时间。

为解决这个问题，我们提出了一个解决方案，让用户定义 Topology-Aware Scheduling Policies，能够减轻或消除低效函数分配。在这里，“Topology”是指：1）平台在不同区域中的部署，即地理位置相同区域的资源集合；2）这些区域中存在多个controller，即管理函数调度组件；3）不同worker，每个worker位于一个区域，但可能由所有controller访问。

提出了一个新的声明性语言，名为 TAPP(Topology-aware Allocation Priority Policies),用于编写描述拓扑感知功能执行调度策略的配置文件，为DevOps提供了对无服务器功能调度的更好控制。通过这种方式，遵循“基础设施即代码”方法，用户可以将所有相关的调度信息存储在一个单一的存储库中 (在单个或多个 TAPP 文件中),可以版本控制，更改和运行，而不会因为系统重新启动加载新配置而遭受停机时间。由于具有拓扑意识，TAPP脚本可以限制区域内功能的执行，并有助于提高无服务器应用程序的性能(例如，利用数据或代码位置属性)、安全性和弹性。

[code](https://github.com/mattrent/openwhisk-deploy-kube)

## SMARTCOMP
> IEEE International Conference on Smart Computing是服务计算领域的权威学术会议，以服务计算为中心，涵盖了与云、边缘和物联网(IoT)相关的各种系统和网络研究，以及智能计算、学习、大数据和区块链应用技术，解决了知识网络、高性能、安全、隐私、可靠性等关键问题。

### 2022
>

#### 1.A Prototype for QKD-secure Serverless Computing with ETSI MEC

[pdf](https://ieeexplore.ieee.org/abstract/document/10207658)

**摘要：**
我们展示了边缘计算网络原型的实现情况，其中客户端和边缘域都承载了模拟量子密钥分发设备，用于医院用例。特别是，使用功能即服务（FaaS）模式的数字医疗应用将调用部署在边缘基础设施中的 Apache OpenWhisk 集群提供的远程功能，其中参数和返回值使用通过底层模拟 QKD 点对点网络生成的密钥进行加密。控制/管理平面中的所有交互均通过 ETSI MEC 和 QKD 行业研究小组定义的标准接口进行处理。

[code](https://github.com/Open-QKD-Network/qkd-net)

GitHub - ccicconetti/etsi-mec-qkd: Documents and software about the integration of ETSI MEC and ETSI QKD. Activities started within the project PON QUANCOM funded by the Italian Ministry of University and Research


#### 2.Stateless or stateful FaaS? I’ll take both!

[pdf](https://arxiv.org/pdf/2203.06385.pdf)

**摘要：**
无服务器计算作为一种非常受欢迎的云技术已经出现，服务（FaaS）编程模型使客户端可以调用无状态函数。无服务器计算的演变正在进行中，将其转向网络边缘，并扩大其范围，包括有状态函数。在本文中，我们认为无状态与有状态不是应用程序本身的二分法，而是一种随时间变化的应用程序的属性，这是通过对生产环境中收集的真实轨迹的分析得到证实的。基于这个观察，我们提出了一种资源分配问题的数学公式，这个公式涵盖了这两种操作模式，被称为lambda与mu，这些可以在运行时由边缘编排器高效地解决。我们通过模拟实验来评估这个提议的解决方案，这些实验在现实的网络和工作负载条件下进行，为从网络的角度实现一个系统指明了方向，在这个系统中，应用程序可以自由地适应其当前的操作模式，并以最低的运营成本优化其性能。

**核心内容**
1. 通过野外的定量分析，我们发现交替操作模式可以降低容器租赁费用 (有状态的)、函数调用和存储服务 (无状态的)，以及迁移开销 (第三部分)。
2. 我们提出了一个在边缘同时优化有状态容器和无状态容器函数调用布置的问题，并提出了一个有效解决方案和实际实现 (第四部分)。
3. 通过在现实网络和负载条件下进行模拟实验，我们评估了所提出系统的性能，以确定系统参数配置所涉及的关键权衡 (第五部分)。

在本文中，我们对边缘云应用程序的无状态(λ)和有状态(µ)操作模式之间的分裂采取了新的视角。特别是，基于对在Microsoft Azure生产环境中收集的公开可用跟踪的分析，我们发现，随着时间的推移，在这两种操作模式之间交替，应用程序可以从操作成本方面获益。这一观察结果使我们得到了一个混合整数线性问题的定义，该问题根据每个应用程序首选的瞬时模式，根据分配给µ-apps的容器和λ-apps的负载分配，共同优化了资源分配。我们制定了这个问题，以便可以通过两个连续的步骤有效地解决它，这意味着要定期执行，并且我们提出了尽最大努力处理连续优化运行之间的异步更改的措施。我们通过在合成但现实的边缘网络拓扑上进行综合仿真实验，并使用跟踪驱动的工作负载组合，评估了所提出解决方案的性能。

[code](https://github.com/ccicconetti/serverlessonedge)

