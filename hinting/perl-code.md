# Perl代码

下面的例子展示了如何使用`perl`代码创建一个类似自动分割特性的布局；首先是`Graph::Easy`语言的表达：

```
[A|B|C] [1]->[ABC.2]
```

perl代码如下：

```perl
use Graph::Easy;

my $g = Graph::Easy->new();
my $a = $g->add_node('A');
my $b = $g->add_node('B'); $b->relative_to($a, 1, 0);
my $c = $g->add_node('C'); $c->relative_to($b, 1, 0);
my $o = $g->add_node('1'); $g->add_edge($o,$c);
print $g->as_ascii();
```

两种表达的输出如下：

```
         +---+
         | 1 |
         +---+
           |
           |
           v
+---+---+----+
| A | B |  C |
+---+---+----+
```
