```
setprecision(f::Function, [T=BigFloat,] precision::Integer; base=2)
```

Ändert die arithmetische Präzision von `T` (in der angegebenen `base`) für die Dauer von `f`. Es ist logisch äquivalent zu:

```
old = precision(BigFloat)
setprecision(BigFloat, precision)
f()
setprecision(BigFloat, old)
```

Oft verwendet als `setprecision(T, precision) do ... end`

Hinweis: `nextfloat()`, `prevfloat()` verwenden nicht die von `setprecision` angegebene Präzision.

!!! compat "Julia 1.8"
    Das `base`-Schlüsselwort erfordert mindestens Julia 1.8.

