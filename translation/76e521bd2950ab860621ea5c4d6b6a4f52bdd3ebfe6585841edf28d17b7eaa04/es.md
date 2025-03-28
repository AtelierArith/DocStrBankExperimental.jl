```
Set{T} <: AbstractSet{T}
```

Los `Set` son contenedores mutables que proporcionan una prueba de pertenencia rápida.

Los `Set` tienen implementaciones eficientes de operaciones de conjunto como `in`, `union` e `intersect`. Los elementos en un `Set` son únicos, según lo determinado por la definición de `isequal` de los elementos. El orden de los elementos en un `Set` es un detalle de implementación y no se puede confiar en él.

Véase también: [`AbstractSet`](@ref), [`BitSet`](@ref), [`Dict`](@ref), [`push!`](@ref), [`empty!`](@ref), [`union!`](@ref), [`in`](@ref), [`isequal`](@ref)

# Ejemplos

```jldoctest; filter = r"^  '.'"ma
julia> s = Set("aaBca")
Set{Char} con 3 elementos:
  'a'
  'c'
  'B'

julia> push!(s, 'b')
Set{Char} con 4 elementos:
  'a'
  'b'
  'B'
  'c'

julia> s = Set([NaN, 0.0, 1.0, 2.0]);

julia> -0.0 in s # isequal(0.0, -0.0) es falso
false

julia> NaN in s # isequal(NaN, NaN) es verdadero
true
```
