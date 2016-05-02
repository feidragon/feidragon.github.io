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
下面列举了几个使用PlantUML生成UML图的例子，通过这些列子来直观的理解PlantUML 如何进行画图

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

![](demo-Class-Diagram.png)
* 组件图


## 安装
Local installation
Once you've got the idea, you may install locally PlantUML. (There is a page dedicated on installation here)

You must have Java installed on your machine, and optionally Graphviz software which are used for all diagrams but sequence diagrams and activity beta diagrams.

Then you can then download the jar file plantuml.jar, and save it on your local disk.

An easy way of testing your installation is to launch the GUI by double-clicking on the JAR file.

You can also include PlantUML into your own scripts or documentation tools:

    Make a file containing PlantUML commands, either with an editor or when running other software which calls PlantUML.

    Here is a file called sequenceDiagram.txt:

    @startuml
    Alice -> Bob: test
    @enduml

    Run (or have the software call) PlantUML with this file as input. The output is an image, which either appears in the other software, or is written to an image file on disk.

    For example,

    java -jar plantuml.jar sequenceDiagram.txt

    and the result is a nice diagram in sequenceDiagram.png.

## 编辑工具

个人推荐 Atom作为编辑工具


已经有了一些介绍PlantUML使用的文章，可以参考：

http://archive.3zso.com/archives/plantuml-quickstart.html

更多使用方法参考官方中文文档：http://translate.plantuml.com/zh
