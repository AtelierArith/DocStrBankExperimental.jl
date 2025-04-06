```
permutedims!(dest, src, perm)
```

Permuta las dimensiones del arreglo `src` y almacena el resultado en el arreglo `dest`. `perm` es un vector que especifica una permutación de longitud `ndims(src)`. El arreglo preasignado `dest` debe tener `size(dest) == size(src)[perm]` y se sobrescribe completamente. No se admite la permutación en el lugar y ocurrirán resultados inesperados si `src` y `dest` tienen regiones de memoria superpuestas.

Véase también [`permutedims`](@ref).
