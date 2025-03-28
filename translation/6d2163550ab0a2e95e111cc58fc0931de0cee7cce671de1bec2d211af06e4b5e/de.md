```
Vararg{T,N}
```

Der letzte Parameter eines Tupeltyps [`Tuple`](@ref) kann der spezielle Wert `Vararg` sein, der eine beliebige Anzahl von nachfolgenden Elementen bezeichnet. `Vararg{T,N}` entspricht genau `N` Elementen des Typs `T`. Schließlich entspricht `Vararg{T}` null oder mehr Elementen des Typs `T`. `Vararg` Tupeltypen werden verwendet, um die Argumente darzustellen, die von varargs-Methoden akzeptiert werden (siehe den Abschnitt über [Varargs-Funktionen](@ref) im Handbuch.)

Siehe auch [`NTuple`](@ref).

# Beispiele

```jldoctest
julia> mytupletype = Tuple{AbstractString, Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```
