# Joints

如果有两个或者更多的边共享了一个节点的起点（不仅仅指一个方向）它们会在路径的某一处分叉；同样，如果一个或者多个边共享了一个节点的终点，那么它们会在某个地方汇合。

```
[ Potsdam ], [ Mannheim ]
   --> { end: back,0; }
 [ Weimar ]
   --> { start: front,0; } [ Finsterwalde ], [ Aachen ]
```

![](http://bloodgate.com/perl/graph/manual/img/joints.png)

```
+----------+           +--------+          +--------------+
| Mannheim | ------+-> | Weimar | -+-----> | Finsterwalde |
+----------+       |   +--------+  |       +--------------+
                   |               |
                   |               |
                   |               |
+----------+       |               |       +--------------+
| Potsdam  | ------+               +-----> |    Aachen    |
+----------+                               +--------------+
```

这个机制可以和边的标签一起使用：

```
[ Jena ] 
 -- train --> { start: front, 0; } 
  [ Augsburg ], [ Ulm ]
[ Jena ] -- car --> { start: front, 0; } [ Plauen ]
```

![](http://bloodgate.com/perl/graph/manual/img/joint_labels.png)

```
+------+           train    +----------+
| Jena | ------+----------> |   Ulm    |
+------+       |            +----------+
               |   train    +----------+
               +----------> | Augsburg |
               |            +----------+
               |    car     +----------+
               +----------> |  Plauen  |
                            +----------+
```



