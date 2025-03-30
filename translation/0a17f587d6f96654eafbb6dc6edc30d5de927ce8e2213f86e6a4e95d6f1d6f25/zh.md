```
@fastmath expr
```

执行转换后的表达式，该表达式调用可能违反严格 IEEE 语义的函数。这允许以最快的方式进行操作，但结果是未定义的 – 在执行此操作时要小心，因为它可能会改变数值结果。

这设置了 [LLVM Fast-Math flags](https://llvm.org/docs/LangRef.html#fast-math-flags)，并对应于 clang 中的 `-ffast-math` 选项。有关更多详细信息，请参见 [性能注释的说明](@ref man-performance-annotations)。

# 示例

```jldoctest
julia> @fastmath 1+2
3

julia> @fastmath(sin(3))
0.1411200080598672
```
