```
@ncall N f sym...
```

生成一个函数调用表达式。`sym` 表示任意数量的函数参数，最后一个参数可以是匿名函数表达式，并扩展为 `N` 个参数。

例如，`@ncall 3 func a` 生成

```
func(a_1, a_2, a_3)
```

而 `@ncall 2 func a b i->c[i]` 产生

```
func(a, b, c[1], c[2])
```
