```
__init__
```

La función `__init__()` en un módulo se ejecuta inmediatamente *después* de que el módulo se carga en tiempo de ejecución por primera vez. Se llama una vez, después de que todas las demás declaraciones en el módulo han sido ejecutadas. Debido a que se llama después de importar completamente el módulo, las funciones `__init__` de los submódulos se ejecutarán primero. Dos usos típicos de `__init__` son llamar a funciones de inicialización en tiempo de ejecución de bibliotecas externas en C e inicializar constantes globales que involucran punteros devueltos por bibliotecas externas. Consulta la [sección del manual sobre módulos](@ref modules) para más detalles.

# Ejemplos

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```
