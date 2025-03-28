```
isoperator(s::Symbol)
```

Retourne `true` si le symbole peut être utilisé comme un opérateur, `false` sinon.

# Exemples

```jldoctest
julia> Meta.isoperator(:+), Meta.isoperator(:f)
(true, false)
```
