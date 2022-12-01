---
hide:
  - toc
---

# 安装简介

DCE 5.0 有两个版本：社区版和商业版。

| 版本   | 包含的模块                                                   | 描述                                               |
| ------ | ------------------------------------------------------------ | -------------------------------------------------- |
| 社区版 | 全局管理<br />容器管理<br />可观测性                         | [免费体验](../dce/license0.md)，3 个模块会保持持续更新，可随时[下载子模块的离线包](../download/dce5.md) |
| 商业版 | 全局管理<br />容器管理<br />可观测性<br />应用工作台<br />多云编排<br />微服务引擎<br />服务网格<br />精选中间件<br />云原生网络<br />云原生存储<br />镜像仓库 | [正版授权](https://qingflow.com/f/e3291647)，各个模块可按需自由组合，可随时[下载子模块的离线包](../download/dce5.md)   |

DCE 5.0 社区版的安装流程图如下：

```mermaid
flowchart TB

subgraph second[使用说明]
    direction TB
    U[ ] -.-
    free[申请免费体验] --- kpanda[容器管理]
    kpanda --- ghippo[全局管理]
    ghippo --- insight[可观测性]
    insight -.- ask[提问!!!]
end

subgraph first[安装社区版]
    direction TB
    S[ ] -.-
    plan[资源规划] --> k8s[准备 K8s 集群] 
    k8s --> tools[安装依赖项]
    tools -.-> kind[通过 kind 集群<br>在线安装]
    tools -.-> s1[通过标准 k8s 集群<br>在线安装]
    tools -.-> s2[通过标准 k8s 集群<br>离线安装]
end

start([fa:fa-user DCE 5.0 社区版<br>安装和使用流程简介]) --> first
start --> second

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
classDef spacewhite fill:#ffffff,stroke:#fff,stroke-width:0px,color:#000
classDef plain fill:#ddd,stroke:#fff,stroke-width:4px,color:#000;
classDef k8s fill:#326ce5,stroke:#fff,stroke-width:4px,color:#fff;
classDef cluster fill:#fff,stroke:#bbb,stroke-width:2px,color:#326ce5;

class plan,k8s,tools,kind,s1,s2,kpanda,ghippo,insight,free,ask cluster;
class start plain
class S,U spacewhite

click plan "https://docs.daocloud.io/install/community/resources/"
click k8s "https://docs.daocloud.io/install/community/kind/online/#kind"
click tools "https://docs.daocloud.io/install/install-tools/"
click kind "https://docs.daocloud.io/install/community/kind/online/"
click s1 "https://docs.daocloud.io/install/community/k8s/online/"
click s2 "https://docs.daocloud.io/install/community/k8s/offline/"

click kpanda "https://docs.daocloud.io/kpanda/03ProductBrief/WhatisKPanda/"
click ghippo "https://docs.daocloud.io/ghippo/01ProductBrief/WhatisGhippo/"
click insight "https://docs.daocloud.io/insight/03ProductBrief/WhatisInsight/"
click free "https://docs.daocloud.io/dce/license0/"
click ask "https://docs.daocloud.io/download/dce5/#_3"
```

DCE 5.0 商业版的安装流程图如下：

```mermaid
flowchart TB

    start([fa:fa-user DCE 5.0 商业版<br>安装流程]) -.- deploy[部署规划]
    deploy --> tools[在火种节点上安装依赖项]
    tools --> download[下载离线包]
    download --> config{编辑并配置<br>clusterConfig.yaml<br>重要!}

    config -.compactClusterMode: false.-> typical[经典安装模式]
    typical --> k8s2[自动创建 K8s 集群]
    typical --> mng2[自动创建管理集群<br>安装 Kubean Operator]
    typical --> gsc2[自动创建全局服务集群<br>安装 DCE 常规组件]

    config -.compactClusterMode: true.-> simple[简约安装模式]
    simple --> k8s1[自动创建 K8s 集群]
    simple --> gsc1[自动在一个集群<br>安装所有 DCE 组件]

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
classDef spacewhite fill:#ffffff,stroke:#fff,stroke-width:0px,color:#000
classDef plain fill:#ddd,stroke:#fff,stroke-width:4px,color:#000;
classDef k8s fill:#326ce5,stroke:#fff,stroke-width:4px,color:#fff;
classDef cluster fill:#fff,stroke:#bbb,stroke-width:2px,color:#326ce5;

class deploy,tools,download,config cluster
class typical,k8s,mng2,gsc2,k8s2 k8s
class simple,start plain
class gsc1,k8s1 grey

click deploy "https://docs.daocloud.io/install/commercial/deploy-plan/"
click tools "https://docs.daocloud.io/install/install-tools/"
click download "https://docs.daocloud.io/install/commercial/download-file/"
click config "https://docs.daocloud.io/install/commercial/clusterconfig/"
click typical,simple "https://docs.daocloud.io/install/commercial/start-install/"
```