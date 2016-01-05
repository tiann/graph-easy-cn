# FAQ

## 通常问题

### 有没有GUI编辑器？
没有，Sorry

### Graph::Easy使用什么拓展名？

直接使用**.txt**

### Graphviz

#### Graph::Easy和Graphviz的主要区别在哪？

`Graph::Easy`有如下特性：

- 更简单的符号；Graph::Easy的可读性非常强，因为非常容易维护；特别是对那些不熟悉Graphviz，HTML的用户
- 一个非常适合流程图的基于网格的布局器；对于复杂的图形也可以使用graphviz作为后端，享受两种布局器的便利
- 更易于安装，不需要编译器；只需要Perl就行。(这个已经不成立了）
- 可以输出HTML,ASCII art的图像
- 大小，长和宽都是相对的；因此输出格式可伸缩性很强。

#### 有什么Graphviz可以做到，但是Graph::Easy无法完成的？

以下是Graph::Easy处理起来比较困难的或者说还没有实现的问题：

- 对于复杂布局，布局器容易失控
- 布局器只有一个总体布局策略（不像graphviz, 它的dot, neato和circo都实现了不同的布局策略）
- 无法在边上定义起始点，边永远以一个普通的直线开头
- 分组(子图）目前无法嵌套
- 某些形状和选项目前做不到（椭圆形节点，多于两条线的边）
- 只有8种类型的边
- 没有足够的布局选项（margins, padding没有实现)

#### 有什么Graph::Easy可以做到，但是Graphviz无法完成的？

除了可读性，以下是一些关键不同点：

- 完整的Unicode支持
- 基于网格的布局器
- 支持ASCII, HTML, boxart格式的输出格式
- 可以对标签设置文本风格，比如下划线，斜体等等
- 甚至可以对文本设置混合的风格
- `text-wrap: auto` 会自动包裹标签
- 可以针对整个图设置布局方向，同时对每个节点和边调整不同的方向。
- graphviz没有实现波浪线的边，双线边也不明显
- 链接由`linkbase`和`link`两部分实现，因此你可以对所有的链接设置一个公共的url；甚至可以使用label名字自动生成url
- 可以自动限制节点长度
- 边箭头可以设置不同的颜色
- Graph::Easy提供了一个额外的颜色风格`w3c`

#### Graph::Easy和graphviz有其他的不同点吗？

其他的差别主要是输出格式以及这些格式的优缺点上, 比如：

- HTML格式支持文本缩放（对于视力障碍用户很好），但是png格式只支持固定大小的文本。
- 纯文本格式比如SVG和HTML更容易索引内容
- SVG格式是分辨率独立的
- ASCII格式缺失了部分东西，但是它甚至可以展示在终端上；

由于Graph::Easy自己的布局器只能生成HTML,SVG和ASCII格式的输出，所以其他的格式比如png，pdf要么通过使用graphviz作为后端，要么使用svg生成；如果将来SVG格式被打印机等系统支持的话，那么这么做几乎没必要。（10年过去了，依然是必要的 - -!)

#### 速度上有差别吗？

`Graph::EAsy`在耨鞋情况下较慢，其他情况下更快；但是这个区别只有在非常大的图上才明显；具体可以见[benchmark page][1]

### SVG (可伸缩矢量图像）问题

这个下面的问题在十几年前才有意义，当时firefox版本还是1.5, 固略过。

### Windows相关问题

#### 在Windows下面如何安装？

首先，你需要两样东西：

- Perl, 可以从[ActiveState][2]获取
- nmake, 查阅[获取和安装nmake][3]

安装好perl和nmake之后，可以正常安装`Graph::Easy`:

```
perl Makefile.PL
nmake
nmake test
nmake install
```
