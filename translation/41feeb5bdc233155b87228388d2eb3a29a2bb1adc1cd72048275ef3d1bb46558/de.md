```
Iterators.reverse(itr)
```

Gegeben ist ein Iterator `itr`, dann ist `reverse(itr)` ein Iterator über dieselbe Sammlung, jedoch in umgekehrter Reihenfolge. Dieser Iterator ist "lazy", da er keine Kopie der Sammlung erstellt, um sie umzukehren; siehe [`Base.reverse`](@ref) für eine eager Implementierung.

(Im Standardfall gibt dies ein `Iterators.Reverse`-Objekt zurück, das `itr` umschließt, welches iterierbar ist, wenn die entsprechenden [`iterate`](@ref) Methoden definiert sind, aber einige `itr`-Typen können spezialisiertere `Iterators.reverse`-Verhaltensweisen implementieren.)

Nicht alle Iterator-Typen `T` unterstützen die Iteration in umgekehrter Reihenfolge. Wenn `T` dies nicht tut, wird das Iterieren über `Iterators.reverse(itr::T)` einen [`MethodError`](@ref) auslösen, da die fehlenden `iterate`-Methoden für `Iterators.Reverse{T}` nicht vorhanden sind. (Um diese Methoden zu implementieren, kann der ursprüngliche Iterator `itr::T` von einem `r::Iterators.Reverse{T}`-Objekt durch `r.itr` abgerufen werden; allgemeiner kann man `Iterators.reverse(r)` verwenden.)

# Beispiele

```jldoctest
julia> foreach(println, Iterators.reverse(1:5))
5
4
3
2
1
```
