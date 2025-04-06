```
Base.rest(collection[, itr_state])
```

Belirli bir yineleme durumu `itr_state` ile `collection`'ın sonunu almak için genel bir işlev. Eğer `collection` kendisi bir `Tuple` ise bir `Tuple`, `collection` bir `AbstractArray` ise `AbstractVector`'ın bir alt türü, `collection` bir `AbstractString` ise `AbstractString`'in bir alt türü ve aksi takdirde `Iterators.rest(collection[, itr_state])`'ye geri dönen bir rastgele yineleyici döner.

Kullanıcı tanımlı koleksiyon türleri için, son pozisyondaki [atama sırasında yutma](@ref destructuring-assignment) davranışını özelleştirmek için aşırı yüklenebilir, örneğin `a, b... = collection`.

!!! compat "Julia 1.6"
    `Base.rest` en az Julia 1.6 gerektirir.


Ayrıca bakınız: [`first`](@ref first), [`Iterators.rest`](@ref), [`Base.split_rest`](@ref).

# Örnekler

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.rest(a, state)
(1, [3, 2, 4])
```
