# 简介

`Graph::Easy` 是一个处理图形DSL的Perl模块，它有如下功能：

- 提供了一种易懂，可读性很强的图形描述语言
- 一种支持 ASCII Art 的基于网格的布局器
- 可以导出为[Graphviz][1], [VCG][2](Visualizing Compiler Graphs), [GDL][3](Graph Description LAnguages) 和 [GraphML][4]格式。
- 可以从`Graphviz`, `VCG` 和 `GDL`导入图像。

本文档旨在让你学会使用`Graph::Easy`语言来创建图像（或者流程图），然后将它转换为ASCII, HTML, SVG或者是可以导出为png或者pdf文件的`Graphviz`格式。

要了解本模块，请从[概述](overview/README.md)开始。
# 下载和镜像

可以在[CPAN][5]下载`Graph::Easy`。

如果你想创建一个镜像，请联系[作者][6]. 本文档可以在下面这些网站找到：

- [http://bloodgate.com/perl/graph/manual](http://bloodgate.com/perl/graph/manual)
- [http://search.cpan.org/~tels/Graph-Easy-Manual/doc/manual/index.html](http://search.cpan.org/~tels/Graph-Easy-Manual/doc/manual/index.html)

# Demo和使用本模块的网站
Demo可以在[这里][7]看到（现在这个网站已经无法打开）；这个模块也在一些perl的graph的模块使用；另外，可以通过[Mediawiki插件][8]在wiki里面使用这个模块；你深知可以把这种图形添加到[POD][9]中。

下面的一些网站和项目使用了本模块：

- [S23][10]
- [Bloodgate][11]
- [BOWiki][12]
- [Cosmogol][13]

# bug反馈
如果有问题，可以给作者发[邮件][14]; Bug反馈在[rt.cpan.org][15]

[1]: http://graphviz.org/
[2]: http://rw4.cs.uni-sb.de/~sander/html/gsvcg1.html
[3]: http://www.aisee.com/
[4]: http://graphml.graphdrawing.org/
[5]: http://search.cpan.org/~tels/Graph-Easy/
[6]: http://bloodgate.com/mail.html
[7]: http://bloodgate.com/graph-demo
[8]: http://search.cpan.org/~tels/mediawiki-graph/
[9]: http://bloodgate.com/wiki/POD
[10]: http://s23.org/wiki/Graph_Extension
[11]: http://bloodgate.com/wiki/Graph
[12]: http://onto.eva.mpg.de/bowiki/index.php/Special:GO/Nucleus
[13]: http://www.cosmogol.fr/examples.html
[14]: http://bloodgate.com/mail.html
[15]: http://rt.cpan.org/NoAuth/ReportBug.html?Queue=Graph-Easy
