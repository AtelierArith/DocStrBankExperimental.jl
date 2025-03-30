```
Threads.Atomic{T}
```

Bir `T` türünde bir nesneye referans tutar ve bunun yalnızca atomik olarak, yani bir iş parçacığına güvenli bir şekilde erişilmesini sağlar.

Yalnızca belirli "basit" türler atomik olarak kullanılabilir; bunlar, ilkel boolean, tam sayı ve kayan nokta türleridir. Bunlar `Bool`, `Int8`...`Int128`, `UInt8`...`UInt128` ve `Float16`...`Float64`'tür.

Yeni atomik nesneler, atomik olmayan değerlerden oluşturulabilir; eğer belirtilmezse, atomik nesne sıfır ile başlatılır.

Atomik nesnelere `[]` notasyonu kullanılarak erişilebilir:

# Örnekler

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> x[] = 1
1

julia> x[]
1
```

Atomik işlemler `atomic_` ön eki kullanır, örneğin [`atomic_add!`](@ref), [`atomic_xchg!`](@ref) vb.
