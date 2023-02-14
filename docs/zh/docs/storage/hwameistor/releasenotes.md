# Hwameistor Release Notes

本页列出 Hwameistor 相关的 Release Notes，便于您了解各版本的演进路径和特性变化。

## 2022-12-30

### v0.7.1

#### 新功能

- **新增** Hwameistor DashBoard UI，可展现存储资源、存储节点等使用状态。

- **新增** 界面管理 Hwameistor 存储节点、本地磁盘、迁移记录。

- **新增** 存储池管理功能，支持界面展现存储池基本信息，及存储池对应节点信息。

- **新增** 本地卷管理功能 ，支持界面执行数据卷迁移、高可用转换。

#### 优化

- **优化** 数据迁移前不必要的日志，并规避其他 Namespace 下的 Job 执行影响。