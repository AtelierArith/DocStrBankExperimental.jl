```
UndefVarError(var::Symbol, [scope])
```

Mevcut kapsamda bir sembol tanımlı değil.

# Örnekler

```jldoctest
julia> a
HATA: UndefVarError: `a` tanımlı değil `Main` içinde

julia> a = 1;

julia> a
1
```
