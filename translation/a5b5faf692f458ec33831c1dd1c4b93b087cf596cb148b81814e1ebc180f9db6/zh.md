```
Profile.Allocs.@profile [sample_rate=0.1] expr
```

对 `expr` 期间发生的分配进行分析，同时返回结果和 AllocResults 结构体。

采样率为 1.0 将记录所有内容；0.0 将不记录任何内容。

```julia
julia> Profile.Allocs.@profile sample_rate=0.01 peakflops()
1.03733270279065e11

julia> results = Profile.Allocs.fetch()

julia> last(sort(results.allocs, by=x->x.size))
Profile.Allocs.Alloc(Vector{Any}, Base.StackTraces.StackFrame[_new_array_ at array.c:127, ...], 5576)
```

有关更多信息，请参阅 Julia 文档中的分析教程。

!!! compat "Julia 1.11"
    较旧版本的 Julia 在所有情况下无法捕获类型。在较旧版本的 Julia 中，如果您看到类型为 `Profile.Allocs.UnknownType` 的分配，这意味着分析器不知道分配了什么类型的对象。这主要发生在分配来自编译器生成的代码时。有关更多信息，请参见 [issue #43688](https://github.com/JuliaLang/julia/issues/43688)。

    自 Julia 1.11 以来，所有分配都应报告类型。


!!! compat "Julia 1.8"
    分配分析器是在 Julia 1.8 中添加的。

