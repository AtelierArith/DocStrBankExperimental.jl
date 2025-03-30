```
isunaryoperator(s::Symbol)
```

Sembolün bir unar (ön) operatör olarak kullanılabilir olup olmadığını kontrol eder, `true` dönerse, aksi takdirde `false` döner.

# Örnekler

```jldoctest
julia> Meta.isunaryoperator(:-), Meta.isunaryoperator(:√), Meta.isunaryoperator(:f)
(true, true, false)
```
