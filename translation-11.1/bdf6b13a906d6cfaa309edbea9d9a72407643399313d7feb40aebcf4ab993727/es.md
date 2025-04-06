```
finalmente
```

Ejecuta algún código cuando un bloque de código dado sale, independientemente de cómo salga. Por ejemplo, aquí se muestra cómo podemos garantizar que un archivo abierto se cierre:

```julia
f = open("file")
try
    operate_on_file(f)
finally
    close(f)
end
```

Cuando el control sale del bloque [`try`](@ref) (por ejemplo, debido a un [`return`](@ref), o simplemente finalizando normalmente), [`close(f)`](@ref) se ejecutará. Si el bloque `try` sale debido a una excepción, la excepción continuará propagándose. Un bloque `catch` puede combinarse con `try` y `finally` también. En este caso, el bloque `finally` se ejecutará después de que `catch` haya manejado el error.
