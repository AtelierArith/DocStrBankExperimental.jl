```
issuccess(F::LU; allowsingular = false)
```

Prueba que la factorización LU de una matriz tuvo éxito. Por defecto, una factorización que produce un factor U válido pero deficiente en rango se considera un fallo. Esto se puede cambiar pasando `allowsingular = true`.

!!! compat "Julia 1.11"
    El argumento de palabra clave `allowsingular` se agregó en Julia 1.11.


# Ejemplos

```jldoctest
julia> F = lu([1 2; 1 2], check = false);

julia> issuccess(F)
false

julia> issuccess(F, allowsingular = true)
true
```
