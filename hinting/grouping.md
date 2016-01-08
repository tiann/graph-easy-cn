# 分组

可以使用括号将节点分组，也就是创建一个子图；分组会提示布局器尽量把组里面的节点放在相近的地方。

```
( German Cities
  [ Berlin ] -> [ Potsdam ]
) {
  border-style: dashed;
  }
```

```
...................................
: German Cities:                  :
:                                 :
: +-------------+     +---------+ :
: |   Berlin    | --> | Potsdam | :
: +-------------+     +---------+ :
:                                 :
:.................................:
```

分组的特性与`nodeclass`结合起来更加强大：

```
node.cities { color: blue; }

( German Cities
  [ Berlin ] -> [ Potsdam ]
) { 
  border-style: dashed;
  nodeclass: cities;
  }
```

在上面这个例子里面，分组里面的节点会自动拥有`node.cities`这个属性。

给以给指定一个分组到一个节点的边，反过来也可行。

```
[ From Node to Group ] -->

( German cities:
  [ Berlin ] -> [ Potsdam ]
) 

  -- group to group -->

( German rivers:
  [ Rhein ] -> [ Elbe ]
)

--> [ From Group to Node ]
```

