```
setrounding(f::Function, T, mode)
```

在 `f` 的持续时间内更改浮点类型 `T` 的舍入模式。它在逻辑上等同于：

```
old = rounding(T)
setrounding(T, mode)
f()
setrounding(T, old)
```

有关可用舍入模式，请参见 [`RoundingMode`](@ref)。
