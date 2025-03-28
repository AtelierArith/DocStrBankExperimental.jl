```
transpose!(dest,src)
```

Transponer el arreglo `src` y almacenar el resultado en el arreglo preasignado `dest`, que debe tener un tamaño correspondiente a `(size(src,2),size(src,1))`. No se admite la transposición en el lugar y ocurrirán resultados inesperados si `src` y `dest` tienen regiones de memoria superpuestas.

# Ejemplos

```jldoctest
julia> A = [3+2im 9+2im; 8+7im  4+6im]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im

julia> B = zeros(Complex{Int64}, 2, 2)
2×2 Matrix{Complex{Int64}}:
 0+0im  0+0im
 0+0im  0+0im

julia> transpose!(B, A);

julia> B
2×2 Matrix{Complex{Int64}}:
 3+2im  8+7im
 9+2im  4+6im

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im
```
