```
finalizer(f, x)
```

Registra una función `f(x)` que se llamará cuando no haya referencias accesibles al programa para `x`, y devuelve `x`. El tipo de `x` debe ser un `mutable struct`, de lo contrario, la función lanzará una excepción.

`f` no debe causar un cambio de tarea, lo que excluye la mayoría de las operaciones de E/S como `println`. Usar el macro `@async` (para diferir el cambio de contexto fuera del finalizador) o `ccall` para invocar directamente funciones de E/S en C puede ser útil para fines de depuración.

Ten en cuenta que no hay una edad de mundo garantizada para la ejecución de `f`. Puede ser llamada en la edad de mundo en la que se registró el finalizador o en cualquier edad de mundo posterior.

# Ejemplos

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizando $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizando %s.", repr(x))
end
```

Un finalizador puede ser registrado en la construcción del objeto. En el siguiente ejemplo, ten en cuenta que confiamos implícitamente en que el finalizador devuelve el `mutable struct` recién creado `x`.

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizando $t.")
        finalizer(f, x)
    end
end
```
