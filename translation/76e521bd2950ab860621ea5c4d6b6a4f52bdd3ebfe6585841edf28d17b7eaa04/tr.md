```
Set{T} <: AbstractSet{T}
```

`Set`ler, hızlı üyelik testi sağlayan değiştirilebilir konteynerlerdir.

`Set`ler, `in`, `union` ve `intersect` gibi küme işlemlerinin verimli uygulamalarına sahiptir. Bir `Set` içindeki elemanlar, elemanların `isequal` tanımına göre benzersizdir. Bir `Set` içindeki elemanların sırası, bir uygulama ayrıntısıdır ve güvenilir değildir.

Ayrıca bakınız: [`AbstractSet`](@ref), [`BitSet`](@ref), [`Dict`](@ref), [`push!`](@ref), [`empty!`](@ref), [`union!`](@ref), [`in`](@ref), [`isequal`](@ref)

# Örnekler

```jldoctest; filter = r"^  '.'"ma
julia> s = Set("aaBca")
Set{Char} with 3 elements:
  'a'
  'c'
  'B'

julia> push!(s, 'b')
Set{Char} with 4 elements:
  'a'
  'b'
  'B'
  'c'

julia> s = Set([NaN, 0.0, 1.0, 2.0]);

julia> -0.0 in s # isequal(0.0, -0.0) is false
false

julia> NaN in s # isequal(NaN, NaN) is true
true
```
