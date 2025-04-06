```
LoadError(file::AbstractString, line::Int, error)
```

Une erreur s'est produite lors de [`include`](@ref Base.include), [`require`](@ref Base.require) ou [`using`](@ref) d'un fichier. Les détails de l'erreur devraient être disponibles dans le champ `.error`.

!!! compat "Julia 1.7"
    Les LoadErrors ne sont plus émis par `@macroexpand`, `@macroexpand1` et `macroexpand` depuis Julia 1.7.

