```
codeunit(s::AbstractString, i::Integer) -> Union{UInt8, UInt16, UInt32}
```

Retourne la valeur de l'unité de code dans la chaîne `s` à l'index `i`. Notez que

```
codeunit(s, i) :: codeunit(s)
```

C'est-à-dire que la valeur retournée par `codeunit(s, i)` est du type retourné par `codeunit(s)`.

# Exemples

```jldoctest
julia> a = codeunit("Hello", 2)
0x65

julia> typeof(a)
UInt8
```

Voir aussi [`ncodeunits`](@ref), [`checkbounds`](@ref).
