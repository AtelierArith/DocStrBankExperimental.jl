```
isoperator(s::Symbol)
```

Sembolün bir operatör olarak kullanılabilir olup olmadığını kontrol eder, `true` dönerse kullanılabilir, aksi takdirde `false` döner.

# Örnekler

```jldoctest
julia> Meta.isoperator(:+), Meta.isoperator(:f)
(true, false)
```
