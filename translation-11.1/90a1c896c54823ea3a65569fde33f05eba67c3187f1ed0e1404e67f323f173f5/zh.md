```
BitSet([itr])
```

构造一个由给定可迭代对象生成的 `Int` 的排序集合，或者一个空集合。实现为位字符串，因此设计用于密集整数集合。如果集合将是稀疏的（例如，包含几个非常大的整数），请改用 [`Set`](@ref)。
