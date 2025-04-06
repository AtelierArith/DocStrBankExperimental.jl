```
maxintfloat(T=Float64)
```

El número de punto flotante con valor entero consecutivo más grande que está representado exactamente en el tipo de punto flotante dado `T` (que por defecto es `Float64`).

Es decir, `maxintfloat` devuelve el número de punto flotante con valor entero positivo más pequeño `n` tal que `n+1` *no* es representable exactamente en el tipo `T`.

Cuando se necesita un valor de tipo `Integer`, usa `Integer(maxintfloat(T))`.
