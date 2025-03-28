```
evalfile(path::AbstractString, args::Vector{String}=String[])
```

Carga el archivo en un módulo anónimo usando [`include`](@ref), evalúa todas las expresiones y devuelve el valor de la última expresión. El argumento opcional `args` se puede usar para establecer los argumentos de entrada del script (es decir, la variable global `ARGS`). Ten en cuenta que las definiciones (por ejemplo, métodos, globales) se evalúan en el módulo anónimo y no afectan al módulo actual.

# Ejemplos

```jldoctest
julia> write("testfile.jl", """
           @show ARGS
           1 + 1
       """);

julia> x = evalfile("testfile.jl", ["ARG1", "ARG2"]);
ARGS = ["ARG1", "ARG2"]

julia> x
2

julia> rm("testfile.jl")
```
