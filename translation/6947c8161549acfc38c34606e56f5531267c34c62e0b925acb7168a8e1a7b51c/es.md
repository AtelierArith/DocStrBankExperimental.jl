# Inference

## How inference works

En el compilador de Julia, "la inferencia de tipos" se refiere al proceso de deducir los tipos de valores posteriores a partir de los tipos de los valores de entrada. El enfoque de Julia hacia la inferencia ha sido descrito en las publicaciones de blog a continuación:

1. [Shows a simplified implementation of the data-flow analysis algorithm, that Julia's type inference routine is based on.](https://aviatesk.github.io/posts/data-flow-problem/)
2. [Gives a high level view of inference with a focus on its inter-procedural convergence guarantee.](https://info.juliahub.com/inference-convergence-algorithm-in-julia)
3. [Explains a refinement on the algorithm introduced in 2.](https://info.juliahub.com/inference-convergence-algorithm-in-julia-revisited)

## Debugging compiler.jl

Puedes iniciar una sesión de Julia, editar `compiler/*.jl` (por ejemplo, para insertar declaraciones `print`), y luego reemplazar `Core.Compiler` en tu sesión en ejecución navegando a `base` y ejecutando `include("compiler/compiler.jl")`. Este truco generalmente conduce a un desarrollo mucho más rápido que si reconstruyes Julia por cada cambio.

Alternativamente, puedes usar el paquete [Revise.jl](https://github.com/timholy/Revise.jl) para rastrear los cambios del compilador utilizando el comando `Revise.track(Core.Compiler)` al comienzo de tu sesión de Julia. Como se explica en [Revise documentation](https://timholy.github.io/Revise.jl/stable/), las modificaciones al compilador se reflejarán cuando se guarden los archivos modificados.

Un punto de entrada conveniente para la inferencia es `typeinf_code`. Aquí hay una demostración que ejecuta la inferencia en `convert(Int, UInt(1))`:

```julia
# Get the method
atypes = Tuple{Type{Int}, UInt}  # argument types
mths = methods(convert, atypes)  # worth checking that there is only one
m = first(mths)

# Create variables needed to call `typeinf_code`
interp = Core.Compiler.NativeInterpreter()
sparams = Core.svec()      # this particular method doesn't have type-parameters
run_optimizer = true       # run all inference optimizations
types = Tuple{typeof(convert), atypes.parameters...} # Tuple{typeof(convert), Type{Int}, UInt}
Core.Compiler.typeinf_code(interp, m, types, sparams, run_optimizer)
```

Si tus aventuras de depuración requieren un `MethodInstance`, puedes buscarlo llamando a `Core.Compiler.specialize_method` utilizando muchas de las variables anteriores. Un objeto `CodeInfo` se puede obtener con

```julia
# Returns the CodeInfo object for `convert(Int, ::UInt)`:
ci = (@code_typed convert(Int, UInt(1)))[1]
```

## The inlining algorithm (`inline_worthy`)

Gran parte del trabajo más duro para la inlining se realiza en `ssa_inlining_pass!`. Sin embargo, si tu pregunta es "¿por qué no se inlinó mi función?", entonces lo más probable es que estés interesado en `inline_worthy`, que toma la decisión de inlinar la llamada a la función o no.

`inline_worthy` implementa un modelo de costos, donde las funciones "baratas" se inlinan; más específicamente, inlinamos funciones si su tiempo de ejecución anticipado no es grande en comparación con el tiempo que tomaría [issue a call](https://en.wikipedia.org/wiki/Calling_convention) si no se inlinaran. El modelo de costos es extremadamente simple e ignora muchos detalles importantes: por ejemplo, todos los bucles `for` se analizan como si se ejecutaran una vez, y el costo de un `if...else...end` incluye el costo sumado de todas las ramas. También vale la pena reconocer que actualmente carecemos de un conjunto de funciones adecuadas para probar qué tan bien el modelo de costos predice el costo real de tiempo de ejecución, aunque [BaseBenchmarks](https://github.com/JuliaCI/BaseBenchmarks.jl) proporciona una gran cantidad de información indirecta sobre los éxitos y fracasos de cualquier modificación al algoritmo de inlining.

La base del modelo de costos es una tabla de búsqueda, implementada en `add_tfunc` y sus llamadores, que asigna un costo estimado (medido en ciclos de CPU) a cada una de las funciones intrínsecas de Julia. Estos costos se basan en [standard ranges for common architectures](http://ithare.com/wp-content/uploads/part101_infographics_v08.png) (ver [Agner Fog's analysis](https://www.agner.org/optimize/instruction_tables.pdf) para más detalles).

Suplementamos esta tabla de búsqueda de bajo nivel con una serie de casos especiales. Por ejemplo, una expresión `:invoke` (una llamada para la cual todos los tipos de entrada y salida fueron inferidos de antemano) se le asigna un costo fijo (actualmente 20 ciclos). En contraste, una expresión `:call`, para funciones que no son intrínsecas/nativas, indica que la llamada requerirá despacho dinámico, en cuyo caso asignamos un costo establecido por `Params.inline_nonleaf_penalty` (actualmente fijado en `1000`). Tenga en cuenta que esta no es una estimación de "primeros principios" del costo bruto del despacho dinámico, sino una mera heurística que indica que el despacho dinámico es extremadamente costoso.

Cada declaración se analiza por su costo total en una función llamada `statement_cost`. Puedes mostrar el costo asociado con cada declaración de la siguiente manera:

```jldoctest; filter=r"tuple.jl:\d+"
julia> Base.print_statement_costs(stdout, map, (typeof(sqrt), Tuple{Int},)) # map(sqrt, (2,))
map(f, t::Tuple{Any}) @ Base tuple.jl:281
  0 1 ─ %1  = $(Expr(:boundscheck, true))::Bool
  0 │   %2  = Base.getfield(_3, 1, %1)::Int64
  1 │   %3  = Base.sitofp(Float64, %2)::Float64
  0 │   %4  = Base.lt_float(%3, 0.0)::Bool
  0 └──       goto #3 if not %4
  0 2 ─       invoke Base.Math.throw_complex_domainerror(:sqrt::Symbol, %3::Float64)::Union{}
  0 └──       unreachable
 20 3 ─ %8  = Base.Math.sqrt_llvm(%3)::Float64
  0 └──       goto #4
  0 4 ─       goto #5
  0 5 ─ %11 = Core.tuple(%8)::Tuple{Float64}
  0 └──       return %11

```

Los costos de línea están en la columna de la izquierda. Esto incluye las consecuencias de la inserción en línea y otras formas de optimización.
