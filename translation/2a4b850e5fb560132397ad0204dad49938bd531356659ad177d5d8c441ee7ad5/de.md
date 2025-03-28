```
StepRangeLen(         ref::R, step::S, len, [offset=1]) where {  R,S}
StepRangeLen{T,R,S}(  ref::R, step::S, len, [offset=1]) where {T,R,S}
StepRangeLen{T,R,S,L}(ref::R, step::S, len, [offset=1]) where {T,R,S,L}
```

Ein Bereich `r`, bei dem `r[i]` Werte vom Typ `T` erzeugt (im ersten Fall wird `T` automatisch abgeleitet), parametrisiert durch einen `ref`erenzwert, einen `step` und die `len`gth. Standardmäßig ist `ref` der Startwert `r[1]`, alternativ können Sie ihn als Wert von `r[offset]` für einen anderen Index `1 <= offset <= len` angeben. Die Syntax `a:b` oder `a:b:c`, wobei einer von `a`, `b` oder `c` Fließkommazahlen sind, erstellt einen `StepRangeLen`.

!!! compat "Julia 1.7"
    Der 4. Typparameter `L` erfordert mindestens Julia 1.7.

