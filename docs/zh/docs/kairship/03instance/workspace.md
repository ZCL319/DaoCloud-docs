---
hide:
  - toc
---

# 工作空间

工作空间是 DCE5.0 支持全局资源管理的划分设计；用于管理资源，包含层级和工作空间两部分。工作空间可以理解为部门下的项目，管理员通过层级和工作空间映射企业中的层级关系。

## 多云编排与工作空间的关系

在多云编排中，具有多云编排模块的超级管理员可以将对应的多云实例或多云命名空间以资源的形式绑定到对应工作空间内；这样的好处是结合了 DCE5.0 的权限管理能力，并无缝衔接了工作空间的角色与权限。

简单来说，当一个多云实例或多云命名空间之后，工作空间内的用户就能够直接获得多云编排的权限，减少了多云编排的权限传递成本。

在多云实例列表，可以看到工作空间的管理入口：

![20221128014958.png](../images/20221128014958.png)

## 工作空间管理界面

通过界面中，我们可以非常方便的看到每个多云实例或者多云命名空间所属的工作空间

![20221128014948](../images/20221128014948.png)

## 绑定/解绑工作空间

点击多云资源列表的尾部按钮，可以触发绑定/解绑操作

![20221128015020](../images/20221128015020.png)

> 绑定成功后，即可在全局管理模块查看对应的多云资源

## 注意事项

### 权限传递映射

1. 每个多云 实例/命名空间，只能够同时绑定单个工作空间
    1. 为保证资源与权限的匹配稳定性，我们不支持多个工作空间直接绑定同一个资源对象；这在整个 DCE5.0 权限设计中是统一的；
    2. 如果希望可以被其他工作空间也能够使用，我们后续会在工作空间的共享资源模块处理
2. 权限的映射处理，工作空间的身份如何在多云编排中体现
    1. 工作空间中拥有三个身份，WorkspaceAdmin/WorkspaceEdit/WorkspaceReadOnly
    2. WorkspaceAdmin 与 WorkspaceEdit 的权限在多云中几乎相等，后续在增加对应的多云实例管理能力时，会区分二者
    3. WorkspaceReadOnly 在多云编排中仍旧是只读权限的限制

### 多云命名空间与工作空间绑定

当多云工作空间与工作空间绑定，实际绑定之后会自动将绑定关系传递到全部工作集群之中，这里无需用户操作。

多云命名空间的权限与普通单集群命名空间权限无差别，仅具备单个命名空间的权限