```
nextind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Caso `n == 1`

    Si `i` está dentro de los límites en `s`, devuelve el índice del inicio del carácter cuya codificación comienza después del índice `i`. En otras palabras, si `i` es el inicio de un carácter, devuelve el inicio del siguiente carácter; si `i` no es el inicio de un carácter, avanza hasta el inicio de un carácter y devuelve ese índice. Si `i` es igual a `0`, devuelve `1`. Si `i` está dentro de los límites pero es mayor o igual a `lastindex(str)`, devuelve `ncodeunits(str)+1`. De lo contrario, lanza `BoundsError`.
  * Caso `n > 1`

    Se comporta como si se aplicara `n` veces `nextind` para `n==1`. La única diferencia es que si `n` es tan grande que aplicar `nextind` alcanzaría `ncodeunits(str)+1`, entonces cada iteración restante aumenta el valor devuelto en `1`. Esto significa que en este caso `nextind` puede devolver un valor mayor que `ncodeunits(str)+1`.
  * Caso `n == 0`

    Devuelve `i` solo si `i` es un índice válido en `s` o es igual a `0`. De lo contrario, se lanza `StringIndexError` o `BoundsError`.

# Ejemplos

```jldoctest
julia> nextind("α", 0)
1

julia> nextind("α", 1)
3

julia> nextind("α", 3)
ERROR: BoundsError: attempt to access 2-codeunit String at index [3]
[...]

julia> nextind("α", 0, 2)
3

julia> nextind("α", 1, 2)
4
```
