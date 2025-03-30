```
@atomicreplace a.b.x beklenen => istenen
@atomicreplace :sıralı_tutarlı a.b.x beklenen => istenen
@atomicreplace :sıralı_tutarlı :monotonik a.b.x beklenen => istenen
```

Koşullu değişimi atomik olarak gerçekleştirerek `(eski, başarı::Bool)` değerlerini döndürün. Burada `başarı`, değişimin tamamlanıp tamamlanmadığını gösterir.

Bu işlem, `replaceproperty!(a.b, :x, beklenen, istenen)` çağrısına karşılık gelir.

Daha fazla bilgi için kılavuzdaki [Alan başına atomikler](@ref man-atomics) bölümüne bakın.

# Örnekler

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicreplace a.x 1 => 2 # a'nın x alanını 1 ise 2 ile değiştir, sıralı tutarlılık ile
(eski = 1, başarı = true)

julia> @atomic a.x # a'nın x alanını al, sıralı tutarlılık ile
2

julia> @atomicreplace a.x 1 => 2 # a'nın x alanını 1 ise 2 ile değiştir, sıralı tutarlılık ile
(eski = 2, başarı = false)

julia> xchg = 2 => 0; # a'nın x alanını 2 ise 0 ile değiştir, sıralı tutarlılık ile

julia> @atomicreplace a.x xchg
(eski = 2, başarı = true)

julia> @atomic a.x # a'nın x alanını al, sıralı tutarlılık ile
0
```

!!! uyum "Julia 1.7"
    Bu işlevsellik en az Julia 1.7'yi gerektirir.

