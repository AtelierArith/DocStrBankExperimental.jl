```
UndefVarError(var::Symbol, [scope])
```

Un symbole dans le scope actuel n'est pas défini.

# Exemples

```jldoctest
julia> a
ERROR: UndefVarError: `a` not defined in `Main`

julia> a = 1;

julia> a
1
```
