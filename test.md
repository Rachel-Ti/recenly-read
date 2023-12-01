- [CCFA](#ccfa)
  - [Conference](#conference)
    - [ASPLOS](#asplos)
      - [2022](#2022)
        - [1.IceBreaker: Warming Serverless Functions Better with Heterogeneity](#1icebreaker-warming-serverless-functions-better-with-heterogeneity)
      
      

# CCFA

## Conference

### ASPLOS

> 摘要截止日期 2022.10.20

#### 2022

> 2022.2.28-3.14
>
> 有专门的关于 serverless 的会议主题

##### 1.IceBreaker: Warming Serverless Functions Better with Heterogeneity 

**摘要：**

无服务器计算是一种新兴的计算模式，它依赖于在预期执行前的 "预热 "函数，以便为用户提供更快、更经济的服务。不幸的是，**预热函数可能是不准确的，并且在预热期间会产生令人望而却步的昂贵成本（即函数保活成本）**。在本文中，**我们介绍了 IceBreaker，这是一种新颖的技术，通过用异构节点（昂贵和便宜）组成系统来减少服务时间和 "保活 "成本。IceBreaker 的做法是，根据函数的时间变化概率，动态地确定在具有成本效益类型的节点来预热函数。通过采用异构性，IceBreaker 允许在相同的成本预算下拥有更多数量的节点，因此可以保活更多数量的函数，并减少高负载时的等待时间**。我们的实际系统评估证实，IceBreaker 使用具有代表性的无服务器应用程序和行业级工作负载跟踪，将整体保持不变的成本降低了 45％，执行时间降低了 27％。IceBreaker 是第一个采用并利用昂贵和便宜节点混合的想法来改善无服务器函数的服务时间和保持成本的技术--为研究人员和从业者开辟了一条在异构服务器上进行无服务器计算的新研究途径。
