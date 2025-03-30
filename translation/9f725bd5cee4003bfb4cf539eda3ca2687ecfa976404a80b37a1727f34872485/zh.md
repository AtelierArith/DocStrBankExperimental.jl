```
typeintersect(T::Type, S::Type)
```

计算一个包含 `T` 和 `S` 交集的类型。通常这将是最小的这样的类型或接近它的一个类型。

一个保证精确行为的特殊情况：当 `T <: S` 时，`typeintersect(S, T) == T == typeintersect(T, S)`。
