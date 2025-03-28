```
isbinaryoperator(s::Symbol)
```

Retourne `true` si le symbole peut être utilisé comme un opérateur binaire (infixe), `false` sinon.

# Exemples

```jldoctest
julia> Meta.isbinaryoperator(:-), Meta.isbinaryoperator(:√), Meta.isbinaryoperator(:f)
(true, false, false)
```
