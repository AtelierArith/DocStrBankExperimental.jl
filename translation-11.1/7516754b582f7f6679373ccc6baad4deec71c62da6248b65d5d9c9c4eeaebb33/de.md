```
LoadError(file::AbstractString, line::Int, error)
```

Ein Fehler ist aufgetreten beim [`include`](@ref Base.include), [`require`](@ref Base.require) oder [`using`](@ref) einer Datei. Die Einzelheiten des Fehlers sollten im Feld `.error` verfügbar sein.

!!! compat "Julia 1.7"
    LoadErrors werden seit Julia 1.7 nicht mehr von `@macroexpand`, `@macroexpand1` und `macroexpand` ausgegeben.

