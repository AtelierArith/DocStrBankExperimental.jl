```
replace(A, old_new::Pair...; [count::Integer])
```

Gibt eine Kopie der Sammlung `A` zurück, in der für jedes Paar `old=>new` in `old_new` alle Vorkommen von `old` durch `new` ersetzt werden. Die Gleichheit wird mit [`isequal`](@ref) bestimmt. Wenn `count` angegeben ist, werden höchstens `count` Vorkommen insgesamt ersetzt.

Der Elementtyp des Ergebnisses wird unter Verwendung von Promotion (siehe [`promote_type`](@ref)) basierend auf dem Elementtyp von `A` und den Typen der `new`-Werte in den Paaren gewählt. Wenn `count` weggelassen wird und der Elementtyp von `A` ein `Union` ist, wird der Elementtyp des Ergebnisses keine Singleton-Typen enthalten, die durch Werte eines anderen Typs ersetzt werden: Zum Beispiel wird `Union{T,Missing}` zu `T`, wenn `missing` ersetzt wird.

Siehe auch [`replace!`](@ref), [`splice!`](@ref), [`delete!`](@ref), [`insert!`](@ref).

!!! compat "Julia 1.7"
    Version 1.7 ist erforderlich, um Elemente eines `Tuple` zu ersetzen.


# Beispiele

```jldoctest
julia> replace([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace([1, missing], missing=>0)
2-element Vector{Int64}:
 1
 0
```
