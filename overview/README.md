# 概要

## 输入和输出

下图是Graph::Easy的概要图，输入是绿色，直接输出是橘黄色，白色是组成节点。黄色的节点是使用第三方模块支持的格式输出。

![](http://bloodgate.com/perl/graph/manual/img/dataflow.png)

有很多种方式创建`Graph::Easy`内部支持的数据结构：

- 使用交互式编辑器（没有实现）
- 使用`Graph::Easy`能理解的文本格式（graphviz, VCG, GDL, Graph::Easy)然后使用命令行工具`graph-easy`来解析并产生输出（这个工具会和模块一起安装）
- 直接写perl代码

下面是一点使用perl代码的例子：

```perl
use strict;
use Graph::Easy;

my $graph = Graph::Easy->new();

$graph->add_edge('Bonn', 'Berlin');
$graph->add_edge('Berlin', 'Bonn', 'train' );
```

相应的文本描述如下：

```
[ Berlin ] -- train --> [ Bonn ]
[ Bonn ] --> [ Berlin ]
```

如你所见，使用文本描述更加简洁。当然，使用文本然后解析还是使用perl完全取决于你。同样地，如果你有了`Graph::Easy`对象，你可以把它输出为任意你想要的格式。
另外，使用文本描述是完备的：你可以先解析文本，产生输出；然后可以把输出又转换为文本描述。

## 存储和布局

Graph::Easy的确使用了[Graph][1]模块来存储和管理内部的图形数据；但是从版本v0.25开始，它没有这么做了；它简单地把边和节点存储了Perl的Hash表，然后直接访问；为什么这么做请参见[这里][2]

要说明的是，Graph和Graph::Easy这两个模块都仅仅存储了图形的表示数据，没有特定的布局信息；比如下面的图（使用`Graph::Easy`语法表示的 )

```
[ A ] -> [ C ] -> [ D ]
[ C ] -> [ E ]
```

可以有多种布局方式（有可能无穷多种），下面是两个例子：

![](http://bloodgate.com/perl/graph/manual/img/example1.png)

```
+---+     +---+     +---+
| A | --> | C | --> | D |
+---+     +---+     +---+
            |
            |
            v
          +---+
          | E |
          +---+
```

## 布局

上面提到过，Graph::Easy仅仅存储了图像的描述信息，要产生特定的布局，需要借助其他的工具；以下是在Perl里面可以通过Graph产生布局的一些方法：

- [Graph::Easy][3]
- [dot][4](使用graphviz)
- [Graph-Layderer][5]
- [Graph-Layout-Aesthetic][6]

将来或许会有更多，但是作者开始写这个模块的时候，只有这些选择。和其他的方式不同`Graph::Easy`使用了一种checker-board tiled布局。

要指出的是，传统的把节点放置在任意位置的方式不能产生ASCII格式的输出，也不能产生HTML的输出；好吧，或许是有可能，但是如果边不是直的而是到处都是的话，那么非常难办。

以上也是这个项目存在的原因。:-P
