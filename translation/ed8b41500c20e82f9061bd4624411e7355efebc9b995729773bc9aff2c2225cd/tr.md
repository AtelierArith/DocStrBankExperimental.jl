```
front(x::Tuple)::Tuple
```

`x`'in son bileşeni hariç tüm bileşenlerini içeren bir `Tuple` döndürür.

Ayrıca bkz: [`first`](@ref), [`tail`](@ref Base.tail).

# Örnekler

```jldoctest
julia> Base.front((1,2,3))
(1, 2)

julia> Base.front(())
HATA: ArgumentError: Boş bir tuple üzerinde front çağrısı yapılamaz.
```
