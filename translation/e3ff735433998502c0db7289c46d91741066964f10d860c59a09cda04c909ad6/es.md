```
hvncat(dim::Int, row_first, values...)
hvncat(dims::Tuple{Vararg{Int}}, row_first, values...)
hvncat(shape::Tuple{Vararg{Tuple}}, row_first, values...)
```

Concatenación horizontal, vertical y n-dimensional de muchos `values` en una sola llamada.

Esta función se llama para la sintaxis de matrices de bloques. El primer argumento especifica la forma de la concatenación, similar a `hvcat`, como una tupla de tuplas, o las dimensiones que especifican el número clave de elementos a lo largo de cada eje, y se utiliza para determinar las dimensiones de salida. La forma `dims` es más eficiente y se utiliza por defecto cuando la operación de concatenación tiene el mismo número de elementos a lo largo de cada eje (por ejemplo, [a b; c d;;; e f ; g h]). La forma `shape` se utiliza cuando el número de elementos a lo largo de cada eje es desigual (por ejemplo, [a b ; c]). La sintaxis desigual necesita una sobrecarga de validación adicional. La forma `dim` es una optimización para la concatenación a lo largo de solo una dimensión. `row_first` indica cómo se ordenan los `values`. El significado de los primeros y segundos elementos de `shape` también se intercambia según `row_first`.

# Ejemplos

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c;;; d e f]
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6

julia> hvncat((2,1,3), false, a,b,c,d,e,f)
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 3
 4

[:, :, 3] =
 5
 6

julia> [a b;;; c d;;; e f]
1×2×3 Array{Int64, 3}:
[:, :, 1] =
 1  2

[:, :, 2] =
 3  4

[:, :, 3] =
 5  6

julia> hvncat(((3, 3), (3, 3), (6,)), true, a, b, c, d, e, f)
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6
```

# Ejemplos para la construcción de los argumentos

```
[a b c ; d e f ;;;
 g h i ; j k l ;;;
 m n o ; p q r ;;;
 s t u ; v w x]
⇒ dims = (2, 3, 4)

[a b ; c ;;; d ;;;;]
 ___   _     _
 2     1     1 = elementos en cada fila (2, 1, 1)
 _______     _
 3           1 = elementos en cada columna (3, 1)
 _____________
 4             = elementos en cada corte 3d (4,)
 _____________
 4             = elementos en cada corte 4d (4,)
⇒ shape = ((2, 1, 1), (3, 1), (4,), (4,)) con `row_first` = true
```
