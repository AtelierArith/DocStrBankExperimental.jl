```
qr!(A, pivot = NoPivot(); blocksize)
```

`qr!` 与 [`qr`](@ref) 相同，当 `A` 是 [`AbstractMatrix`](@ref) 的子类型时，但通过覆盖输入 `A` 来节省空间，而不是创建副本。如果因因式分解产生一个无法由 `A` 的元素类型表示的数字，例如对于整数类型，将抛出 [`InexactError`](@ref) 异常。

!!! compat "Julia 1.4"
    `blocksize` 关键字参数需要 Julia 1.4 或更高版本。


# 示例

```jldoctest
julia> a = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> qr!(a)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q 因子: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R 因子:
2×2 Matrix{Float64}:
 -3.16228  -4.42719
  0.0      -0.632456

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> qr!(a)
ERROR: InexactError: Int64(3.1622776601683795)
Stacktrace:
[...]
```
