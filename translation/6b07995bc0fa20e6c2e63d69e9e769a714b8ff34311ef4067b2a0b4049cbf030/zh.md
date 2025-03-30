```
@evalpoly(z, c...)
```

计算多项式 $\sum_k z^{k-1} c[k]$，其中系数为 `c[1]`、`c[2]`，...；也就是说，系数按 `z` 的幂的升序给出。此宏扩展为高效的内联代码，使用霍纳法则，或者对于复数 `z`，使用更高效的类似 Goertzel 的算法。

另见 [`evalpoly`](@ref)。

# 示例

```jldoctest
julia> @evalpoly(3, 1, 0, 1)
10

julia> @evalpoly(2, 1, 0, 1)
5

julia> @evalpoly(2, 1, 1, 1)
7
```
