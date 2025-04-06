```
spzeros!(::Type{Tv}, I::AbstractVector{Ti}, J::AbstractVector{Ti}, m::Integer, n::Integer,
         klasttouch::Vector{Ti}, csrrowptr::Vector{Ti}, csrcolval::Vector{Ti},
         [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}]) where {Tv,Ti<:Integer}
```

`spzeros(I, J)` 的父类和专家驱动，允许用户提供预分配的中间对象存储。此方法对 `spzeros` 的作用类似于 `SparseArrays.sparse!` 对 `sparse` 的作用。有关详细信息和所需缓冲区长度，请参阅 `SparseArrays.sparse!` 的文档。

!!! compat "Julia 1.10"
    此方法需要 Julia 1.10 或更高版本。

