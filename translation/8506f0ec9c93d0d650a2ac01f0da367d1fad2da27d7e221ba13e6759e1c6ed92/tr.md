```
@atomicswap a.b.x = new
@atomicswap :sequentially_consistent a.b.x = new
```

`new` değerini `a.b.x`'e kaydeder ve `a.b.x`'in eski değerini döndürür.

Bu işlem, `swapproperty!(a.b, :x, new)` çağrısına karşılık gelir.

Daha fazla ayrıntı için kılavuzdaki [Alan bazında atomikler](@ref man-atomics) bölümüne bakın.

# Örnekler

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicswap a.x = 2+2 # a'nın x alanını 4 ile değiştir, sıralı tutarlılıkla
1

julia> @atomic a.x # a'nın x alanını al, sıralı tutarlılıkla
4
```

!!! uyumluluk "Julia 1.7"
    Bu işlevsellik en az Julia 1.7'yi gerektirir.

