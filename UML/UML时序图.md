[TOC]

# UML时序图（序列图）

参考链接：

[UML时序图(Sequence Diagram)学习笔记](https://blog.csdn.net/fly_zxy/article/details/80911942)

## 什么是时序图

时序图(Sequence Diagram)，又名序列图、循序图，是一种UML交互图。它通过描述对象之间发送消息的时间顺序显示多个对象之间的动态协作。

## 时序图的元素

我们在画时序图时会涉及7种元素：**角色(Actor)、对象(Object)、生命线(LifeLine)、控制焦点(Activation)、消息(Message)、自关联消息、组合片段。**

其中前6种是比较常用和重要的元素，剩余的一种组合片段元素不是很常用，但是比较复杂。

我们先介绍前6种元素，在单独介绍组合片段元素。

### 角色(Actor)

系统角色，可以是人或者其他系统，子系统。以一个小人图标表示。

### 对象(Object)

命名方式   **对象名:类名**

对象位于时序图的顶部,以一个矩形表示。对象的命名方式一般有三种：
    1 对象名和类名。例如：华为手机:手机、loginServiceObject:LoginService。
    2 只显示类名，不显示对象，即为一个匿名类。例如：:手机、:LoginSservice。
    3 只显示对象名，不显示类名。例如：华为手机:、loginServiceObject:。

### 生命线(LifeLine)

