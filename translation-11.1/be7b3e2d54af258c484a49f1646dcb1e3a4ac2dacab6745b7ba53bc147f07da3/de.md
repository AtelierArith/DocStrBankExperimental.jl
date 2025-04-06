```
isassigned(ref::RefValue) -> Bool
```

Überprüfen, ob die gegebene [`Ref`](@ref) mit einem Wert verknüpft ist. Dies ist immer wahr für eine [`Ref`](@ref) eines Bittyp-Objekts. Gibt `false` zurück, wenn die Referenz undefiniert ist.

# Beispiele

```jldoctest
julia> ref = Ref{Function}()
Base.RefValue{Function}(#undef)

julia> isassigned(ref)
false

julia> ref[] = (foobar(x) = x)
foobar (generische Funktion mit 1 Methode)

julia> isassigned(ref)
true

julia> isassigned(Ref{Int}())
true
```
