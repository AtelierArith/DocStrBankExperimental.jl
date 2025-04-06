```
endswith(s::AbstractString, suffix::Regex)
```

Devuelve `true` si `s` termina con el patrón de expresión regular, `suffix`.

!!! note
    `endswith` no compila el anclaje en la expresión regular, sino que pasa el anclaje como `match_option` a PCRE. Si el tiempo de compilación se amortiza, `occursin(r"...$", s)` es más rápido que `endswith(s, r"...")`.


Véase también [`occursin`](@ref) y [`startswith`](@ref).

!!! compat "Julia 1.2"
    Este método requiere al menos Julia 1.2.


# Ejemplos

```jldoctest
julia> endswith("JuliaLang", r"Lang|Roberts")
true
```
