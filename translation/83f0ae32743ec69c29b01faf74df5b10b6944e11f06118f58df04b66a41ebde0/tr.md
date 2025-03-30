```
isbinaryoperator(s::Symbol)
```

Sembolün ikili (infix) operatör olarak kullanılabilir olup olmadığını kontrol eder, `true` dönerse, aksi takdirde `false` döner.

# Örnekler

```jldoctest
julia> Meta.isbinaryoperator(:-), Meta.isbinaryoperator(:√), Meta.isbinaryoperator(:f)
(true, false, false)
```
