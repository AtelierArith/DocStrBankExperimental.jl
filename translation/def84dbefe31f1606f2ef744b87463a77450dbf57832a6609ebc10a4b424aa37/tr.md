```
cbrt(x::Gerçek)
```

`x`'in küp kökünü döndürür, yani $x^{1/3}$. Negatif değerler kabul edilir (eğer $x < 0$ ise negatif gerçek kökü döndürür).

Önek operatör `∛`, `cbrt` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> cbrt(big(27))
3.0

julia> cbrt(big(-27))
-3.0
```
