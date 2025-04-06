```
startswith(io::IO, prefix::Union{AbstractString,Base.Chars})
```

检查一个 `IO` 对象是否以一个前缀开始，该前缀可以是字符串、字符，或字符的元组/向量/集合。另见 [`peek`](@ref)。
