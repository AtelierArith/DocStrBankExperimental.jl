```
prevind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Caso `n == 1`

    Si `i` está dentro de los límites en `s`, devuelve el índice del inicio del carácter cuya codificación comienza antes del índice `i`. En otras palabras, si `i` es el inicio de un carácter, devuelve el inicio del carácter anterior; si `i` no es el inicio de un carácter, retrocede hasta el inicio de un carácter y devuelve ese índice. Si `i` es igual a `1`, devuelve `0`. Si `i` es igual a `ncodeunits(str)+1`, devuelve `lastindex(str)`. De lo contrario, lanza `BoundsError`.
  * Caso `n > 1`

    Se comporta como si se aplicara `n` veces `prevind` para `n==1`. La única diferencia es que si `n` es tan grande que aplicar `prevind` alcanzaría `0`, entonces cada iteración restante disminuye el valor devuelto en `1`. Esto significa que en este caso `prevind` puede devolver un valor negativo.
  * Caso `n == 0`

    Devuelve `i` solo si `i` es un índice válido en `str` o es igual a `ncodeunits(str)+1`. De lo contrario, se lanza `StringIndexError` o `BoundsError`.

# Ejemplos

```jldoctest
julia> prevind("α", 3)
1

julia> prevind("α", 1)
0

julia> prevind("α", 0)
ERROR: BoundsError: attempt to access 2-codeunit String at index [0]
[...]

julia> prevind("α", 2, 2)
0

julia> prevind("α", 2, 3)
-1
```
