```
codeunit(s::AbstractString, i::Integer) -> Union{UInt8, UInt16, UInt32}
```

Gibt den Codeeinheitswert im String `s` am Index `i` zurück. Beachten Sie, dass

```
codeunit(s, i) :: codeunit(s)
```

Das heißt, der Wert, der von `codeunit(s, i)` zurückgegeben wird, ist vom Typ, der von `codeunit(s)` zurückgegeben wird.

# Beispiele

```jldoctest
julia> a = codeunit("Hello", 2)
0x65

julia> typeof(a)
UInt8
```

Siehe auch [`ncodeunits`](@ref), [`checkbounds`](@ref).
