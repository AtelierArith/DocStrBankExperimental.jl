```
nzrange(A::AbstractSparseMatrixCSC, col::Integer)
```

Devuelve el rango de índices a los valores no nulos estructurales de una columna de matriz dispersa. En conjunto con [`nonzeros`](@ref) y [`rowvals`](@ref), esto permite iterar de manera conveniente sobre una matriz dispersa:

```
A = sparse(I,J,V)
rows = rowvals(A)
vals = nonzeros(A)
m, n = size(A)
for j = 1:n
   for i in nzrange(A, j)
      row = rows[i]
      val = vals[i]
      # realizar magia dispersa...
   end
end
```

!!! advertencia
    Agregar o eliminar elementos no nulos de la matriz puede invalidar el `nzrange`, no se debe mutar la matriz mientras se itera.

