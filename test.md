- [Schedule](#schedule)
  - [ICWS](#icws)
    - [2022](#2022)
      - [1.A Declarative Approach to Topology-Aware Serverless Function-Execution Scheduling]
        (#1A Declarative Approach to Topology-Aware Serverless Function-Execution Scheduling)
        

# Schedule

## ICWS
> 是服务计算领域的权威学术会议，以服务计算为中心，涵盖了与云、边缘和物联网(IoT)相关的各种系统和网络研究，以及智能计算、学习、大数据和区块链应用技术，解决了知识网络、高性能、安全、隐私、可靠性等关键问题。

### 2022
>


#### 1.A Declarative Approach to Topology-Aware Serverless Function-Execution Scheduling 

**摘要：**

最新的无服务器平台使用硬编码调度策略，这些策略不知道函数可能存在的拓扑约束。在调度函数时考虑这些约束可以带来性能的显著提升，例如最小化加载时间或数据访问延迟。当考虑到新兴的多云和边缘云 continuum 系统时，这个问题变得更加紧迫，因为只有**特定的节点可以访问专用、本地资源**。为解决这个问题，我们提出了一种声明性语言来定义无服务器调度策略，以表达调度器和执行节点拓扑的约束。我们将我们的方法实现为 **OpenWhisk**平台的扩展，并展示相关场景，在这些场景中，我们的扩展与纯 OpenWhisk 相比具有竞争力或表现更优。

**核心内容**
在多云和边缘云连续系统中，分配函数时，并非所有worker都平等，只有特定的worker可以访问某些本地资源。实际上，像**像数据局部性**(由于访问数据的高延迟而产生的影响)，或者**会话局部性**(由于需要身份验证并打开新的会话以与其他服务交互而产生的影响)，可能会显著增加函数的运行时间。

为解决这个问题，我们提出了一个解决方案，让用户定义 Topology-Aware Scheduling Policies，能够减轻或消除低效函数分配。在这里，“Topology”是指：1）平台在不同区域中的部署，即地理位置相同区域的资源集合；2）这些区域中存在多个controller，即管理函数调度组件；3）不同worker，每个worker位于一个区域，但可能由所有controller访问。

提出了一个新的声明性语言，名为 TAPP(Topology-aware Allocation Priority Policies),用于编写描述拓扑感知功能执行调度策略的配置文件，为DevOps提供了对无服务器功能调度的更好控制。通过这种方式，遵循“基础设施即代码”方法，用户可以将所有相关的调度信息存储在一个单一的存储库中 (在单个或多个 TAPP 文件中),可以版本控制，更改和运行，而不会因为系统重新启动加载新配置而遭受停机时间。由于具有拓扑意识，TAPP脚本可以限制区域内功能的执行，并有助于提高无服务器应用程序的性能(例如，利用数据或代码位置属性)、安全性和弹性。