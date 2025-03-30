```
Some{T}
```

在 `Union{Some{T}, Nothing}` 中使用的包装类型，用于区分缺少值（[`nothing`](@ref)）和存在一个 `nothing` 值（即 `Some(nothing)`）。

使用 [`something`](@ref) 来访问 `Some` 对象包装的值。
