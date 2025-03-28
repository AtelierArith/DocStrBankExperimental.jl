```
widen(x)
```

Si `x` es un tipo, devuelve un tipo "más grande", definido de tal manera que las operaciones aritméticas `+` y `-` están garantizadas de no desbordarse ni perder precisión para cualquier combinación de valores que el tipo `x` puede contener.

Para tipos de enteros de tamaño fijo menores de 128 bits, `widen` devolverá un tipo con el doble de bits.

Si `x` es un valor, se convierte a `widen(typeof(x))`.

# Ejemplos

```jldoctest
julia> widen(Int32)
Int64

julia> widen(1.5f0)
1.5
```
