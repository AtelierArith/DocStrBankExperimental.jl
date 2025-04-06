```
unsafe_modify!(p::Ptr{T}, op, x, [order::Symbol]) -> Pair
```

Estas operaciones se realizan atómicamente para obtener y establecer una dirección de memoria después de aplicar la función `op`. Si es compatible con el hardware (por ejemplo, incremento atómico), esto puede optimizarse a la instrucción de hardware apropiada; de lo contrario, su ejecución será similar a:

```
y = unsafe_load(p)
z = op(y, x)
unsafe_store!(p, z)
return y => z
```

El prefijo `unsafe` en esta función indica que no se realiza ninguna validación en el puntero `p` para asegurar que sea válido. Al igual que en C, el programador es responsable de asegurarse de que la memoria referenciada no se libere ni se recoja como basura mientras se invoca esta función. Un uso incorrecto puede causar un fallo de segmentación en su programa.

!!! compat "Julia 1.10"
    Esta función requiere al menos Julia 1.10.


Véase también: [`modifyproperty!`](@ref Base.modifyproperty!), [`atomic`](@ref)
