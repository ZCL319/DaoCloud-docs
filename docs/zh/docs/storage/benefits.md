---
hide:
  - toc
---

# 功能优势

## Hwameistor 云原生本地存储

**IO 本地化**

100% 本地吞吐，无网络开销，节点故障时 Pod 在副本节点启动，使用副本数据卷进行本地 IO 读写。

**高性能、高可用性**

- 100% IO 本地化，实现高性能本地吞吐
- 2 副本数据卷冗余备份，保障数据高可用

**线性扩展**

- 独立节点单元，最小 1 节点，扩展数量不限
- 控制平面、数据平面分离，节点扩展，不影响业务应用数据 I/O

**CPU、内存开销小**

IO 本地化，相同的 IO 读写，CPU 平稳，无较大波动，内存资源开销小

**生产可运维**

- 支持节点、磁盘、数据卷组（VG）维度迁移
- 支持换盘等运维行为
