```
tail(x::Tuple)::Tuple
```

`x`'in ilk bileşeni hariç tüm bileşenlerini içeren bir `Tuple` döndürür.

Ayrıca bakınız: [`front`](@ref Base.front), [`rest`](@ref Base.rest), [`first`](@ref), [`Iterators.peel`](@ref).

# Örnekler

```jldoctest
julia> Base.tail((1,2,3))
(2, 3)

julia> Base.tail(())
HATA: ArgumentError: Boş bir tuple üzerinde tail çağrısı yapılamaz.
```
