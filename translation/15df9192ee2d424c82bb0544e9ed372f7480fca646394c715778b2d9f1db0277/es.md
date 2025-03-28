```
unsafe_replace!(p::Ptr{T}, expected, desired,
               [success_order::Symbol[, fail_order::Symbol=success_order]]) -> (; old, success::Bool)
```

Estas operaciones se realizan atómicamente para obtener y establecer condicionalmente una dirección de memoria a un valor dado. Si es compatible con el hardware, esto puede optimizarse a la instrucción de hardware apropiada; de lo contrario, su ejecución será similar a:

```
y = unsafe_load(p, fail_order)
ok = y === expected
if ok
    unsafe_store!(p, desired, success_order)
end
return (; old = y, success = ok)
```

El prefijo `unsafe` en esta función indica que no se realiza ninguna validación en el puntero `p` para asegurar que sea válido. Al igual que en C, el programador es responsable de asegurarse de que la memoria referenciada no se libere ni se recoja como basura mientras se invoca esta función. Un uso incorrecto puede causar un segfault en tu programa.

!!! compat "Julia 1.10"
    Esta función requiere al menos Julia 1.10.


Ver también: [`replaceproperty!`](@ref Base.replaceproperty!), [`atomic`](@ref)
