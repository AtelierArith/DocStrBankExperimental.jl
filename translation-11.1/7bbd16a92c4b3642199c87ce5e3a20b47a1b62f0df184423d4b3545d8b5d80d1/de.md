```
sprint(f::Function, args...; context=nothing, sizehint=0)
```

Rufen Sie die angegebene Funktion mit einem I/O-Stream und den bereitgestellten zusätzlichen Argumenten auf. Alles, was in diesen I/O-Stream geschrieben wird, wird als String zurückgegeben. `context` kann ein [`IOContext`](@ref) sein, dessen Eigenschaften verwendet werden, ein `Pair`, das eine Eigenschaft und ihren Wert angibt, oder ein Tupel von `Pair`, das mehrere Eigenschaften und deren Werte angibt. `sizehint` schlägt die Kapazität des Puffers (in Bytes) vor.

Das optionale Schlüsselwort-Argument `context` kann auf ein `:key=>value`-Paar, ein Tupel von `:key=>value`-Paaren oder ein `IO`- oder [`IOContext`](@ref)-Objekt gesetzt werden, dessen Attribute für den an `f` übergebenen I/O-Stream verwendet werden. Der optionale `sizehint` ist eine empfohlene Größe (in Bytes), die für den Puffer, der zum Schreiben des Strings verwendet wird, zugewiesen werden soll.

!!! compat "Julia 1.7"
    Das Übergeben eines Tupels an das Schlüsselwort `context` erfordert Julia 1.7 oder höher.


# Beispiele

```jldoctest
julia> sprint(show, 66.66666; context=:compact => true)
"66.6667"

julia> sprint(showerror, BoundsError([1], 100))
"BoundsError: attempt to access 1-element Vector{Int64} at index [100]"
```
