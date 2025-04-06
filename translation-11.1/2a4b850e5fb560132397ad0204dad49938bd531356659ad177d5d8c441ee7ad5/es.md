```
StepRangeLen(         ref::R, step::S, len, [offset=1]) where {  R,S}
StepRangeLen{T,R,S}(  ref::R, step::S, len, [offset=1]) where {T,R,S}
StepRangeLen{T,R,S,L}(ref::R, step::S, len, [offset=1]) where {T,R,S,L}
```

Un rango `r` donde `r[i]` produce valores del tipo `T` (en la primera forma, `T` se deduce automáticamente), parametrizado por un valor de `ref`erencia, un `step` y la `len`gth. Por defecto, `ref` es el valor inicial `r[1]`, pero alternativamente puedes proporcionarlo como el valor de `r[offset]` para algún otro índice `1 <= offset <= len`. La sintaxis `a:b` o `a:b:c`, donde cualquiera de `a`, `b` o `c` son números de punto flotante, crea un `StepRangeLen`.

!!! compat "Julia 1.7"
    El 4to parámetro de tipo `L` requiere al menos Julia 1.7.

