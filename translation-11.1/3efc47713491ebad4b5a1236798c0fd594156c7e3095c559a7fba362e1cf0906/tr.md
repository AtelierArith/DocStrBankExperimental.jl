```
setprecision(f::Function, [T=BigFloat,] precision::Integer; base=2)
```

Verilen `base` için `f` süresince `T` aritmetik hassasiyetini değiştirir. Mantıken eşdeğerdir:

```
old = precision(BigFloat)
setprecision(BigFloat, precision)
f()
setprecision(BigFloat, old)
```

Genellikle `setprecision(T, precision) do ... end` şeklinde kullanılır.

Not: `nextfloat()`, `prevfloat()` `setprecision` ile belirtilen hassasiyeti kullanmaz.

!!! compat "Julia 1.8"
    `base` anahtar kelimesi en az Julia 1.8 gerektirir.

