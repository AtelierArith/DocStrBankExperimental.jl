```
@nextract N esym isym
```

生成 `N` 个变量 `esym_1`，`esym_2`，...，`esym_N` 来从 `isym` 中提取值。`isym` 可以是 `Symbol` 或匿名函数表达式。

`@nextract 2 x y` 将生成

```
x_1 = y[1]
x_2 = y[2]
```

而 `@nextract 3 x d->y[2d-1]` 产生

```
x_1 = y[1]
x_2 = y[3]
x_3 = y[5]
```
