```
spzeros!(::Type{Tv}, I::AbstractVector{Ti}, J::AbstractVector{Ti}, m::Integer, n::Integer,
         klasttouch::Vector{Ti}, csrrowptr::Vector{Ti}, csrcolval::Vector{Ti},
         [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}]) where {Tv,Ti<:Integer}
```

`spzeros(I, J)` için bir ana ve uzman sürücü, kullanıcının ara nesneler için önceden tahsis edilmiş depolama sağlamasına olanak tanır. Bu yöntem `spzeros` için, `SparseArrays.sparse!` yönteminin `sparse` için yaptığına benzer. Gerekli tampon uzunlukları ve `SparseArrays.sparse!` ile ilgili ayrıntılar için belgeleri kontrol edin.

!!! compat "Julia 1.10"
    Bu yöntem Julia sürüm 1.10 veya daha yenisini gerektirir.

