```
StepRangeLen(         ref::R, step::S, len, [offset=1]) where {  R,S}
StepRangeLen{T,R,S}(  ref::R, step::S, len, [offset=1]) where {T,R,S}
StepRangeLen{T,R,S,L}(ref::R, step::S, len, [offset=1]) where {T,R,S,L}
```

一个范围 `r`，其中 `r[i]` 产生类型为 `T` 的值（在第一种形式中，`T` 是自动推导的），由一个 `ref` 参考值、一个 `step` 和长度 `len` 参数化。默认情况下，`ref` 是起始值 `r[1]`，但您也可以将其作为某个其他索引 `1 <= offset <= len` 的值 `r[offset]` 提供。语法 `a:b` 或 `a:b:c`，其中 `a`、`b` 或 `c` 任何一个是浮点数，创建一个 `StepRangeLen`。

!!! compat "Julia 1.7"
    第四个类型参数 `L` 至少需要 Julia 1.7。

