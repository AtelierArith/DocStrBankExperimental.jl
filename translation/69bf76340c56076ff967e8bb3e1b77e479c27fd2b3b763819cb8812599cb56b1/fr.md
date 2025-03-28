```
isunaryoperator(s::Symbol)
```

Renvoie `true` si le symbole peut être utilisé comme un opérateur unaire (préfixe), `false` sinon.

# Exemples

```jldoctest
julia> Meta.isunaryoperator(:-), Meta.isunaryoperator(:√), Meta.isunaryoperator(:f)
(true, true, false)
```
