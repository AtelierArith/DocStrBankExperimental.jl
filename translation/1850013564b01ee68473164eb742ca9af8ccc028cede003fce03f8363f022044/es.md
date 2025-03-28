```
Unicode.julia_chartransform(c::Union{Char,Integer})
```

Mapea el carácter Unicode (`Char`) o el punto de código (`Integer`) `c` al correspondiente carácter o punto de código "equivalente", respectivamente, de acuerdo con la equivalencia personalizada utilizada dentro del analizador de Julia (además de la normalización NFC).

Por ejemplo, `'µ'` (U+00B5 micro) se trata como equivalente a `'μ'` (U+03BC mu) por el analizador de Julia, por lo que `julia_chartransform` realiza esta transformación mientras deja otros caracteres sin cambios:

```jldoctest
julia> Unicode.julia_chartransform('µ')
'μ': Unicode U+03BC (categoría Ll: Letra, minúscula)

julia> Unicode.julia_chartransform('x')
'x': ASCII/Unicode U+0078 (categoría Ll: Letra, minúscula)
```

`julia_chartransform` es principalmente útil para pasar a la función [`Unicode.normalize`](@ref) con el fin de imitar la normalización utilizada por el analizador de Julia:

```jldoctest
julia> s = "µö"
"µö"

julia> s2 = Unicode.normalize(s, compose=true, stable=true, chartransform=Unicode.julia_chartransform)
"μö"

julia> collect(s2)
2-element Vector{Char}:
 'μ': Unicode U+03BC (categoría Ll: Letra, minúscula)
 'ö': Unicode U+00F6 (categoría Ll: Letra, minúscula)

julia> s2 == string(Meta.parse(s))
true
```

!!! compat "Julia 1.8"
    Esta función fue introducida en Julia 1.8.

