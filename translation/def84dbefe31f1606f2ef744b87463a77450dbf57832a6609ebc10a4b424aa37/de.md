```
cbrt(x::Real)
```

Gibt die Kubikwurzel von `x` zurück, d.h. $x^{1/3}$. Negative Werte werden akzeptiert (es wird die negative reelle Wurzel zurückgegeben, wenn $x < 0$).

Der Präfixoperator `∛` ist äquivalent zu `cbrt`.

# Beispiele

```jldoctest
julia> cbrt(big(27))
3.0

julia> cbrt(big(-27))
-3.0
```
