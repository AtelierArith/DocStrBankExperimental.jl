```
include_string([mapexpr::Function,] m::Module, code::AbstractString, filename::AbstractString="string")
```

Comme [`include`](@ref), sauf qu'il lit le code à partir de la chaîne donnée plutôt qu'à partir d'un fichier.

L'argument optionnel `mapexpr` peut être utilisé pour transformer le code inclus avant qu'il ne soit évalué : pour chaque expression analysée `expr` dans `code`, la fonction `include_string` évalue en réalité `mapexpr(expr)`. S'il est omis, `mapexpr` par défaut à [`identity`](@ref).

!!! compat "Julia 1.5"
    Julia 1.5 est requis pour passer l'argument `mapexpr`.

