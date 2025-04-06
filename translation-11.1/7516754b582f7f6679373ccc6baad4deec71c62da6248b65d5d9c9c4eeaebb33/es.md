```
LoadError(file::AbstractString, line::Int, error)
```

Ocurrió un error mientras se [`include`](@ref Base.include), [`require`](@ref Base.require) o [`using`](@ref) un archivo. Los detalles del error deberían estar disponibles en el campo `.error`.

!!! compat "Julia 1.7"
    Los LoadErrors ya no se emiten por `@macroexpand`, `@macroexpand1` y `macroexpand a partir de Julia 1.7.

