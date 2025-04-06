```
GC.@preserve x1 x2 ... xn expr
```

Marca los objetos `x1, x2, ...` como *en uso* durante la evaluación de la expresión `expr`. Esto solo es necesario en código inseguro donde `expr` *utiliza implícitamente* memoria u otros recursos propiedad de uno de los `x`.

*Uso implícito* de `x` cubre cualquier uso indirecto de recursos lógicamente propiedad de `x` que el compilador no puede ver. Algunos ejemplos:

  * Acceder a la memoria de un objeto directamente a través de un `Ptr`
  * Pasar un puntero a `x` a `ccall`
  * Usar recursos de `x` que serían limpiados en el finalizador.

`@preserve` generalmente no debería tener ningún impacto en el rendimiento en casos de uso típicos donde extiende brevemente la vida del objeto. En la implementación, `@preserve` tiene efectos como proteger objetos asignados dinámicamente de la recolección de basura.

# Ejemplos

Al cargar desde un puntero con `unsafe_load`, el objeto subyacente se utiliza implícitamente, por ejemplo, `x` se utiliza implícitamente por `unsafe_load(p)` en lo siguiente:

```jldoctest
julia> let
           x = Ref{Int}(101)
           p = Base.unsafe_convert(Ptr{Int}, x)
           GC.@preserve x unsafe_load(p)
       end
101
```

Al pasar punteros a `ccall`, el objeto apuntado se utiliza implícitamente y debe ser preservado. (Sin embargo, ten en cuenta que normalmente deberías pasar `x` directamente a `ccall`, lo cual cuenta como un uso explícito.)

```jldoctest
julia> let
           x = "Hello"
           p = pointer(x)
           Int(GC.@preserve x @ccall strlen(p::Cstring)::Csize_t)
           # Alternativa preferida
           Int(@ccall strlen(x::Cstring)::Csize_t)
       end
5
```
