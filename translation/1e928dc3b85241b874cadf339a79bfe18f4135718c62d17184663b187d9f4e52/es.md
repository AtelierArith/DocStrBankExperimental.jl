```
code_typed(f, types; kw...)
```

Devuelve un array de la forma reducida inferida por tipo (IR) para los métodos que coinciden con la función genérica dada y la firma de tipo.

# Argumentos de Palabra Clave

  * `optimize::Bool = true`: opcional, controla si se aplican optimizaciones adicionales, como la inserción en línea.
  * `debuginfo::Symbol = :default`: opcional, controla la cantidad de metadatos de código presentes en la salida, las opciones posibles son `:source` o `:none`.

# Argumentos Internos de Palabra Clave

Esta sección debe considerarse interna y es solo para quienes entienden los internals del compilador de Julia.

  * `world::UInt = Base.get_world_counter()`: opcional, controla la edad del mundo a utilizar al buscar métodos, usa la edad del mundo actual si no se especifica.
  * `interp::Core.Compiler.AbstractInterpreter = Core.Compiler.NativeInterpreter(world)`: opcional, controla el intérprete abstracto a utilizar, usa el intérprete nativo si no se especifica.

# Ejemplos

Se pueden poner los tipos de argumento en una tupla para obtener el correspondiente `code_typed`.

```julia
julia> code_typed(+, (Float64, Float64))
1-element Vector{Any}:
 CodeInfo(
1 ─ %1 = Base.add_float(x, y)::Float64
└──      return %1
) => Float64
```
