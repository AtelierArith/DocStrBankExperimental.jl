```
thisind(s::AbstractString, i::Integer) -> Int
```

Si `i` está dentro de los límites en `s`, devuelve el índice del inicio del carácter cuyo código de unidad de codificación `i` es parte. En otras palabras, si `i` es el inicio de un carácter, devuelve `i`; si `i` no es el inicio de un carácter, retrocede hasta el inicio de un carácter y devuelve ese índice. Si `i` es igual a 0 o `ncodeunits(s)+1`, devuelve `i`. En todos los demás casos, lanza `BoundsError`.

# Ejemplos

```jldoctest
julia> thisind("α", 0)
0

julia> thisind("α", 1)
1

julia> thisind("α", 2)
1

julia> thisind("α", 3)
3

julia> thisind("α", 4)
ERROR: BoundsError: attempt to access 2-codeunit String at index [4]
[...]

julia> thisind("α", -1)
ERROR: BoundsError: attempt to access 2-codeunit String at index [-1]
[...]
```
