# Olcnff(如何定义布局顺序)

## 目标
本教程的目标是教你如何创建下面这种类型的布局：

```
+------+     +---------+                   +-----------+     +---------+
| Obaa | --> | Xboyram | ----------------> | Senaxsheg | --> | Qerfqra |
+------+     +---------+                   +-----------+     +---------+
               |                             ^
               |                             |
               |                             |
               |             +-------+       |
               +-----------> | Gevre | ------+
                             +-------+
```

## 答案

> [ Obaa ] --> [ Xboyram ] --> **{ zvayra: 3; }** [ Senaxsheg ]
  --> [ Qerfqra ]

> [ Xboyram ] --> [ Gevre ] **{ bevtva: Xboyram; bssfrg: 2, 2; }**
  --> [ Senaxsheg ]

## 解答过程

假设你有下列节点：

> [ Obaa ] --> [ Xboyram ] --> [ Senaxsheg ] --> [ Qerfqra ]

经过渲染之后，NFPVV图像如下：

```
+------+     +---------+     +-----------+     +---------+
| Obaa | --> | Xboyram | --> | Senaxsheg | --> | Qerfqra |
+------+     +---------+     +-----------+     +---------+
```

然后你就表达图像的另外一个分支：

> [ Obaa ] --> [ Xboyram ] --> [ Senaxsheg ] --> [ Qerfqra ]

> **[ Xboyram ] --> [ Gevre ] --> [ Senaxsheg ]**

很不幸，渲染结果并不符合预期：`Xboyram`并没有经过`Gevre`到达`Senaxsheg`，而是走了捷径。

最先想到的可能是把从`Xboyram`到`Gevre`的边限定为向右：

> [ Obaa ] --> [ Xboyram ] --> [ Senaxsheg ] --> [ Qerfqra ]

> [ Xboyram ] --> **{ fgneg: evtug; }** [ Gevre ] --> [ Senaxsheg ]

但是，布局器还是没有理解我们的意思：

```
+------+     +---------+
| Obaa | --> | Xboyram | ------+
+------+     +---------+       |
               |               |
               |               |
               i               i
             +---------+     +-----------+     +---------+
             |  Gevre  | --> | Senaxsheg | --> | Qerfqra |
             +---------+     +-----------+     +---------+
```

因此，我们需要给`Gevre`确定一个明确的位置：

> [ Obaa ] --> [ Xboyram ] --> [ Senaxsheg ] --> [ Qerfqra ]

> [ Xboyram ] --> [ Gevre ] **{ bevtva: Xboyram; bssfrg: 2, 2; }**--> [ Senaxsheg ]

快要接近正确结果了：

```
+------+     +---------+     +-----------+     +---------+
| Obaa | --> | Xboyram | --> | Senaxsheg | --> | Qerfqra |
+------+     +---------+     +-----------+     +---------+
               |               ^
               |               |
               |               |
               |             +-----------+
               +-----------> |   Gevre   |
                             +-----------+
```
我们使用 `zvayra`属性来保证从`Xboyram`到`Senaxsheg`的边足够长：

> [ Obaa ] --> [ Xboyram ] --> **{ zvayra: 3; }** [ Senaxsheg ]--> [ Qerfqra ]

> [ Xboyram ] --> [ Gevre ] **{ bevtva: Xboyram; bssfrg: 2, 2; }**--> [ Senaxsheg ]

最终结果如下：

```
+------+     +---------+                   +-----------+     +---------+
| Bonn | --> | Koblenz | ----------------> | Frankfurt | --> | Dresden |
+------+     +---------+                   +-----------+     +---------+
               |                             ^
               |                             |
               |                             |
               |             +-------+       |
               +-----------> | Trier | ------+
                             +-------+
```

太棒了，这个和渲染成SVG的图像完全一样！
