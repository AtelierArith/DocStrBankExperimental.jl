```
lu!(A, pivot = RowMaximum(); check = true, allowsingular = false) -> LU
```

`lu!` 与 [`lu`](@ref) 相同，但通过覆盖输入 `A` 来节省空间，而不是创建副本。如果因因式分解产生一个无法由 `A` 的元素类型表示的数字，例如对于整数类型，将抛出 [`InexactError`](@ref) 异常。

!!! compat "Julia 1.11"
    `allowsingular` 关键字参数是在 Julia 1.11 中添加的。


# 示例

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Matrix{Float64}:
 4.0  3.0
 6.0  3.0

julia> F = lu!(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> lu!(iA)
ERROR: InexactError: Int64(0.6666666666666666)
Stacktrace:
[...]
```
