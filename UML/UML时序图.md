

# UML时序图（序列图）

参考链接：

[UML时序图(Sequence Diagram)学习笔记](https://blog.csdn.net/fly_zxy/article/details/80911942)

[UML建模图实战笔记](http://ifeve.com/uml-intro/)

## 什么是时序图

时序图(Sequence Diagram)，又名序列图、循序图，是一种UML交互图。它通过描述对象之间发送消息的时间顺序显示多个对象之间的动态协作。

## 时序图的元素

我们在画时序图时会涉及7种元素：**角色(Actor)、对象(Object)、生命线(LifeLine)、控制焦点(Activation)、消息(Message)、自关联消息、组合片段。**

其中前6种是比较常用和重要的元素，剩余的一种组合片段元素不是很常用，但是比较复杂。

我们先介绍前6种元素，在单独介绍组合片段元素。

### 认识时序图六种元素

![img](https://img-blog.csdn.net/20180704144557365?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

时序图解释：
1，用户输入手机密码
2，打开手机
3，打开微信扫一扫
4，返回微信扫一扫界面
5.1 扫描商家收款码
5.2 商家生成收款二维码
5.3 返回收款二维码
5.4 识别商家收款码
6，提示用户输入微信支付密码
7.1 输入微信支付密码
7.2 微信验证用户输入密码正确
7.3 向商家汇款

7.4 汇款成功
8，提示用户支付成功

### 角色(Actor)

系统角色，可以是人或者其他系统，子系统。以一个小人图标表示。

### 对象(Object)

命名方式   **对象名:类名**

对象位于时序图的顶部,以一个矩形表示。对象的命名方式一般有三种：
    1 对象名和类名。例如：华为手机:手机、loginServiceObject:LoginService。
    2 只显示类名，不显示对象，即为一个匿名类。例如：:手机、:LoginSservice。
    3 只显示对象名，不显示类名。例如：华为手机:、loginServiceObject:。

### 生命线(LifeLine)

时序图中**每个对象和底部中心**都有一条垂直的虚线，这就是对象的生命线(对象的时间线)。以一条垂直的虚线表。

### 控制焦点(Activation)

控制焦点代表时序图中在对象时间线上某段时期执行的操作。以一个很窄的矩形表示。

### 消息(Message)

表现代表对象之间发送的信息。消息分为三种类型。
    **同步消息(Synchronous Message)**
消息的发送者把控制传递给消息的接收者，然后停止活动，等待消息的接收者放弃或者返回控制。用来表示同步的意义。以一条实线+实心箭头表示。

​    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200827154211405.png#pic_center)

**异步消息(Asynchronous Message)**
消息发送者通过消息把信号传递给消息的接收者，然后继续自己的活动，不等待接受者返回消息或者控制。异步消息的接收者和发送者是并发工作的。以一条实线+大于号表示。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200827154256571.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21jc2Jhcnk=,size_16,color_FFFFFF,t_70#pic_center)

​    **返回消息(Return Message)**
返回消息表示从过程调用返回。以小于号+虚线表示。（下图的返回消息不对）

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/b0b4248e1b30ce5d49951dfd4dd5be88.png)

### 自关联消息

表示方法的自身调用或者一个对象内的一个方法调用另外一个方法。以一个半闭合的长方形+下方实心剪头表示。

### 组合片段

组合片段用来解决交互执行的条件和方式，它允许在序列图中直接表示逻辑组件，用于通过指定条件或子进程的应用区域，为任何生命线的任何部分定义特殊条件和子进程。组合片段共有13种，名称及含义如下：

| 片段类型 | 名称   | 说明                                                         |
| -------- | ------ | ------------------------------------------------------------ |
| Opt      | 选项   | 包含一个可能发生或不可能发生的序列。<br />可以在临界中指定序列发生的条件<br /><span style="color:red">相当于switch、if..语句</span> |
| Alt      | 抉择   | 包含一个片段列表，这些片段包含备选消息序列。<br />在任何场合下只发生一个序列。<br />可以在每个片段中设置一个临界来指示该片段可以运行的条件。<br />else的临界指示其他任何临界都不为True时运行的片段。<br />如果所有临界都为False并且没有else，则不执行任何片段<br /><span style="color:red">可以理解为if..else if...else条件语句</span> |
| Loop     | 循环   | 片段重复一定次数。<br />可以在临界中指示片段重复的条件。<br />Loop组合片段具有:“Min”和“Max”属性，它们指示片段可以重复的最小和最大次数。<br />默认是没有限制的。<br /><span style="color:red">类似于定时任务、相当于for语句</span> |
| Break    | 中断   | 如果执行此片段，则放弃序列的其余部分。<br />可以使用临界来指示发生中断的条件。 |
| Par      | 并行   | 并行处理<br />片段中的事件可以交错。<br /><span style="color:red">相当于多线程</span> |
| Critical | 关键   | 用在Par或Seq片段中。<br />指示次片段中的消息不得与其他消息交错。 |
| Seq      | 弱顺序 | 有两个或更多操作数片段。<br />涉及同一生命线的消息必须以片段的顺序发生。<br />如果消息涉及的生命线不同，来自不同片段的消息可能会并行交错 |
| Strict   | 强顺序 | 有两个或更多操作数片段。<br />这些片段必须按给定数顺序发生。 |
| Consider | 考虑   | 指定此片段描述的消息列表。<br />其他消息可发生在运行的系统中，但对此描述来说意义不大。<br />在“Messages”属性中键入该列表。 |
| Ignore   | 忽略   | 此片段未描述的消息列表。<br />这些消息可发生在运行的系统中。但对此描述来说意义不大。<br />在“Messages"属性中键入该列表。 |
| Assert   | 断言   | 操作数片段指定唯一有效的序列。<br />通常用在Consider或Ignore片段中。 |
| Neg      | 否定   | 此片段中显示的序列不得发生。<br />通常用在Consider或Ignore连段中。 |
|          |        |                                                              |

#### 常用组合片段举例

##### 抉择（Alt）

抉择在任何场合下只发生一个序列。 可以在每个片段中设置一个临界来指示该片段可以运行的条件。else 的临界指示其他任何临界都不为 True 时应运行的片段。如果所有临界都为 False 并且没有 else，则不执行任何片段。Alt片段组合可以理解为if..else if...else条件语句。

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/1f37ba42fdee396709e66bc39f32319c.png)

我们还拿微信支付的时序图举例，如果7.3向商家汇款的成功或失败流程需要在时序图中体现出来，可以这么使用Alt片段组合。

![img](https://img-blog.csdn.net/20180704155415694?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![img](https://pic001.cnblogs.com/images/2012/1/2012013015543491.gif)

条件判断，如果n>0则执行agree函数否者执行reject函数

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/1f37ba42fdee396709e66bc39f32319c.png)

##### 选项（Opt）

包含一个可能发生或不发生的序列。Opt相当于if..语句。

switch，当满足不同条件执行不同方法：

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/8d7b50f089ecccc3e4708e759405429e.png)

![img](https://img-blog.csdn.net/20180704165231581?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 循环（Loop）

片段重复一定次数，可以在临界中指示片段重复的条件。Loop相当于for语句。

![img](https://img-blog.csdn.net/20180704165240271?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

当没有指定循环边界默认范围为[0,无穷大]：

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/67d7606ef2c2a208a377bb0f9a2284fe.png)

如果只指定了一个值，那么默认执行该值次数：

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/150f617477f23a155d6d5700c763665b.png)

指定了循环边界,则最少执行最小值值，最多执行最大值次数：

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/932dcd05b17d6d3304643de981b9b6c6.png)

实现dowhile方式，至少执行一次,如果size<0则退出:

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/7ee5af3386326ebb8ef55b8e01c7cc6f.png)

##### 并行（Par）

并行处理，片段中的事件可以并行交错。**Par相当于多线程。**

![img](https://img-blog.csdn.net/20180704165248751?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

同时进行，比如多个线程同时执行任务

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/890ab714a24b446502cf0afffb4e0e56.png)

##### Break 中断

n=10时候执行save并退出循环

![image.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/fd6a6d93d2024af0e249aeba12728acb.png)

### 其他元素

#### 注释

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200827154329349.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21jc2Jhcnk=,size_16,color_FFFFFF,t_70#pic_center)

#### 约束

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200827154404576.png#pic_center)

## 时序图的绘制技巧

1，从初始消息开始画，依次画出随后消息，并给每个消息分配序号，方便理解。

2，角色和对象用名词，消息用动词。

3，角色放在时序图的开始位置，对象重要程度或使用频率从左到右排列。这就要根据时间的流程考虑了，是一个比较主观的事情。

![img](https://img-blog.csdn.net/20180704161449488?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

4，控制焦点两端要以消息元素封顶，控制焦点不要超过消息元素。

**正确示范**

**![img](https://img-blog.csdn.net/20180704161521522?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**

**错误示范**

**![img](https://img-blog.csdn.net/201807041615478?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZseV96eHk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**

**最后的技巧就是多联系绘制时序图，熟能生巧，自然而然就会画了。**