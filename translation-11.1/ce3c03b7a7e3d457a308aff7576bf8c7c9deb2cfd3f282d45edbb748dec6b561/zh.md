```
@boundscheck(blk)
```

将表达式 `blk` 注释为边界检查块，允许通过 [`@inbounds`](@ref) 省略它。

!!! note
    编写 `@boundscheck` 的函数必须被内联到其调用者中，以便 `@inbounds` 生效。


# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> @inline function g(A, i)
           @boundscheck checkbounds(A, i)
           return "accessing ($A)[$i]"
       end;

julia> f1() = return g(1:2, -1);

julia> f2() = @inbounds return g(1:2, -1);

julia> f1()
ERROR: BoundsError: attempt to access 2-element UnitRange{Int64} at index [-1]
Stacktrace:
 [1] throw_boundserror(::UnitRange{Int64}, ::Tuple{Int64}) at ./abstractarray.jl:455
 [2] checkbounds at ./abstractarray.jl:420 [inlined]
 [3] g at ./none:2 [inlined]
 [4] f1() at ./none:1
 [5] top-level scope

julia> f2()
"accessing (1:2)[-1]"
```

!!! warning
    `@boundscheck` 注释允许您作为库作者选择允许 *其他代码* 使用 [`@inbounds`](@ref) 删除您的边界检查。如上所述，调用者必须使用他们可以访问的信息验证他们的访问是有效的，然后才能使用 `@inbounds`。例如，对于索引到您的 [`AbstractArray`](@ref) 子类，这涉及到检查索引是否与其 [`axes`](@ref) 相符。因此，只有在您确定其行为是正确的情况下，才应将 `@boundscheck` 注释添加到 [`getindex`](@ref) 或 [`setindex!`](@ref) 实现中。

