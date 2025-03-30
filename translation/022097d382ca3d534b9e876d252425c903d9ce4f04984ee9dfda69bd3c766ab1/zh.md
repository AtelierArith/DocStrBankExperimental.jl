```
reim(A::AbstractArray)
```

返回一个包含两个数组的元组，分别包含 `A` 中每个条目的实部和虚部。

等价于 `(real.(A), imag.(A))`，但当 `eltype(A) <: Real` 时，`A` 会在不复制的情况下返回以表示实部，并且当 `A` 具有零维时，返回一个0维数组（而不是标量）。

# 示例

```jldoctest
julia> reim([1, 2im, 3 + 4im])
([1, 0, 3], [0, 2, 4])

julia> reim(fill(2 - im))
(fill(2), fill(-1))
```
