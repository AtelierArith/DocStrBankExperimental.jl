```
@atomiconce a.b.x = value
@atomiconce :sequentially_consistent a.b.x = value
@atomiconce :sequentially_consistent :monotonic a.b.x = value

Değeri atomik olarak, daha önce ayarlanmamışsa koşullu olarak atayın ve `success::Bool` değerini döndürün. Burada `success`, atamanın tamamlanıp tamamlanmadığını gösterir.

Bu işlem, `setpropertyonce!(a.b, :x, value)` çağrısına karşılık gelir.

Daha fazla bilgi için kılavuzdaki [Alan başına atomikler](@ref man-atomics) bölümüne bakın.

# Örnekler

```

jldoctest julia> mutable struct AtomicOnce            @atomic x            AtomicOnce() = new()        end

julia> a = AtomicOnce() AtomicOnce(#undef)

julia> @atomiconce a.x = 1 # a'nın x alanını 1 olarak ayarla, eğer ayarlanmamışsa, sıralı tutarlılıkla true

julia> @atomic a.x # a'nın x alanını al, sıralı tutarlılıkla 1

julia> @atomiconce a.x = 1 # a'nın x alanını 1 olarak ayarla, eğer ayarlanmamışsa, sıralı tutarlılıkla false

```

!!! compat "Julia 1.11"
    Bu işlevsellik en az Julia 1.11 gerektirir.
```
