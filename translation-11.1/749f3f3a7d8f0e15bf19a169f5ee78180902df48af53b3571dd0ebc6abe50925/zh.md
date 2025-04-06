```
ReverseOrdering(fwd::Ordering=Forward)
```

一个反转排序的包装器。

对于给定的 `Ordering` `o`，以下对于所有 `a`，`b` 成立：

```
lt(ReverseOrdering(o), a, b) == lt(o, b, a)
```
