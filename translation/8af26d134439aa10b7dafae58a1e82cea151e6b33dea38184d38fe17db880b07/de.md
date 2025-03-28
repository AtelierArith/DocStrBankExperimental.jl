```
UndefVarError(var::Symbol, [scope])
```

Ein Symbol im aktuellen Gültigkeitsbereich ist nicht definiert.

# Beispiele

```jldoctest
julia> a
ERROR: UndefVarError: `a` nicht definiert in `Main`

julia> a = 1;

julia> a
1
```
