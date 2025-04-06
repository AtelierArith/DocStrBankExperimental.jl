```
UndefVarError(var::Symbol, [scope])
```

Un símbolo en el ámbito actual no está definido.

# Ejemplos

```jldoctest
julia> a
ERROR: UndefVarError: `a` no definido en `Main`

julia> a = 1;

julia> a
1
```
