---
layout: "post"
title: "使用PlantUML画UML"
date: "2016-05-02 12:11"
---

PlantUML 是一个用纯文本语言创建UML图的开源的工具。

其支持的图形包括：

* 时序图
* 用例图
* 类图
* 活动图
* 组件图
* 状态图
* 部署图
* 对象图

通常我们使用 ``VISIO`` 软件进行流程图等图的生成，现在使用``PlantUML``, 只需要创建一个包含PlantUML 命令的文本文件，然后就可以直接用其生成UML图片。

例如，下面为一个时序图文件的内容：
```
@startuml
Alice -> Bob: hello
@enduml
```

其生成的时序图为：

![](http://plantuml.com/plantuml/png/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000)

最简单和快速的测试PlantUML的方法 是使用在线编辑工具：
[online server](http://plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000)

其官方网站为：http://plantuml.com/

## 举例
下面列举了几个使用PlantUML生成UML图的例子，通过这些例子来直观的了解PlantUML 的使用。

* 时序图

```
@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
@enduml
```
![](http://plantuml.com/imgp/sequence.png)

* 用例图

```
@startuml
left to right direction
skinparam packageStyle rect
actor customer
actor clerk
rectangle checkout {
  customer -- (checkout)
  (checkout) .> (payment) : include
  (help) .> (checkout) : extends
  (checkout) -- clerk
}
@enduml


```
![](http://plantuml.com/imgp/usecase_015.png)

* 活动图

```
@startuml

start

if (Graphviz installed?) then (yes)
  :process all\ndiagrams;
else (no)
  :process only
  __sequence__ and __activity__ diagrams;
endif

stop

@enduml

```

![](http://plantuml.com/imgp/activity2_003.png)
* 类图

```
@startuml
Object <|-- ArrayList

Object : equals()
ArrayList : Object[] elementData
ArrayList : size()

@enduml
```

![](http://plantuml.com/imgp/classes_004.png)

* 状态图

```
@startuml
[*] --> 待复核:需要复核
待复核 --> 已接收
已接收 --> 已拒绝
待复核 --> 已拒绝
已接收 --> 汇款成功
已接收 --> 汇款失败
汇款失败 --> 已退款
汇款成功 --> [*]
已退款 --> [*]

@enduml

```

![](http://feidragon.github.io/tower-resources/demo-Class-Diagram.png)


## 安装

1. 首先必须在电脑中安装Java

2. 可选安装Graphviz(生成序列图和活动图之外的其他UML图需要用到它)

3. 下载 [plantuml.jar](http://sourceforge.net/projects/plantuml/files/plantuml.jar/download) 并保存到本地磁盘即可

4. 用命令行即可用包含PlantUML命令的文件生成图片

  例如：
  ```
    java -jar plantuml.jar sequenceDiagram.txt
  ```
  执行完就会生成一个名为sequenceDiagram.png的图片

## 编辑工具

现在已经有许多开发工具或编辑器支持PlantUML文件的编写、UML图片生成，可以在这里查看：[工具](http://plantuml.com/running.html)

个人推荐 Atom 编辑器作为编辑工具 ，其包含了PlantUML的插件：


* plantuml-viewer

  插件介绍：[https://atom.io/packages/plantuml-viewer](https://atom.io/packages/plantuml-viewer)

  ![](https://i.github-camo.com/bb28497b36c99c618a38f3eb114420c699a87833/68747470733a2f2f646c2e64726f70626f7875736572636f6e74656e742e636f6d2f752f31303830393339302f706c616e74756d6c2d7669657765722e676966)

## 参考资料

网络中已经有了一些介绍PlantUML使用的文章，可以参考：

[http://archive.3zso.com/archives/plantuml-quickstart.html](http://archive.3zso.com/archives/plantuml-quickstart.html)

[http://translate.plantuml.com/zh](http://translate.plantuml.com/zh)

[http://www.jianshu.com/p/e92a52770832](http://www.jianshu.com/p/e92a52770832)
