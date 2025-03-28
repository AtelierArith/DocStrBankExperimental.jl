```
unsafe_swap!(p::Ptr{T}, x, [order::Symbol])
```

Estas operaciones se realizan atómicamente para obtener y establecer simultáneamente una dirección de memoria. Si es compatible con el hardware, esto puede optimizarse a la instrucción de hardware apropiada; de lo contrario, su ejecución será similar a:

```
y = unsafe_load(p)
unsafe_store!(p, x)
return y
```

El prefijo `unsafe` en esta función indica que no se realiza ninguna validación en el puntero `p` para asegurar que sea válido. Al igual que en C, el programador es responsable de asegurarse de que la memoria referenciada no se libere ni se recoja mientras se invoca esta función. Un uso incorrecto puede causar un fallo de segmentación en su programa.

!!! compat "Julia 1.10"
    Esta función requiere al menos Julia 1.10.


Véase también: [`swapproperty!`](@ref Base.swapproperty!), [`atomic`](@ref)
