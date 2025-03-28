```
startswith(s::AbstractString, prefix::Regex)
```

Devuelve `true` si `s` comienza con el patrón de expresión regular, `prefix`.

!!! note
    `startswith` no compila el anclaje en la expresión regular, sino que pasa el anclaje como `match_option` a PCRE. Si el tiempo de compilación se amortiza, `occursin(r"^...", s)` es más rápido que `startswith(s, r"...")`.


Véase también [`occursin`](@ref) y [`endswith`](@ref).

!!! compat "Julia 1.2"
    Este método requiere al menos Julia 1.2.


# Ejemplos

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```
